# Using AI to collect, summarize, and manage social activities

Was doing some reporting and needed to pull down a bunch of LinkedIn post activity and get it summarized.

🤖 Well GPTs are a thing now, and this takes minutes instead of hours.

Using Doug Finke's PSAI module and Przemyslaw Klys PSParseHTML module, this was short work.

💭 Gist link to follow in the comments shortly.

1. Go to https://www.linkedin.com/in/<username>/recent-activity/all/
2. Scroll as far back as you desire
3. Run this in console, copy object, and clean up to URL format
```javascript
// Select the parent UL element
const container = document.querySelector('#profile-content > div > div.scaffold-layout.scaffold-layout--breakpoint-xl.scaffold-layout--sidebar-main-aside.scaffold-layout--reflow > div > div > main > div > section > div.pv0.ph5 > div > div > div.scaffold-finite-scroll__content > ul');

if (container) {
  // Select all elements within that UL that have data-urn containing "urn:li:activity:"
  const elements = container.querySelectorAll('[data-urn*="urn:li:activity:"]');

  // Filter out any elements that *have a child* with the class update-components-header__text-view
  const filtered = Array.from(elements).filter(el => 
    !el.querySelector('.update-components-header__text-view')
  );

  // Extract data-urn values
  const urns = filtered.map(el => el.getAttribute('data-urn'));

  console.log(urns);
} else {
  console.warn('Container not found.');
}
```
4. Copy that object out and clean it up as an array
```powershell
$activities = @"
    https://www.linkedin.com/feed/update/urn:li:activity:000000000000000000000
"@
```
5. Make sure you have PSAI and PSParseHtml installed, and you have a local vault secret for your Azure OpenAI instance then run the below
```powershell
$activities = $activities.Split("`n")

$posts = @()
$regex = "[-:](?'id'[0-9]{19})(?:[-\/?\s]|$)"

#Install-Module psparsehtml, psai
Invoke-Expression $(Get-Secret -Name PSAI -AsPlainText)
Set-OAIProvider -Provider AzureOpenAI
Set-AzOAISecrets @secret

$prompt = "Provide a summary of no more than 10 words for the followng:"

foreach($activity in $activities){
    $post = @{
        activity     = $activity
        activityId   = @{}
        htmlDoc      = Invoke-RestMethod $activity
        postContent  = ""
        shortContent = ""
        summary      = ""
    }

    $postContentObject = ConvertFrom-Html -Content $post.htmlDoc
    $post.postContent = $postContentObject.selectNodes('//article').selectNodes('//p')|Where-Object{
        $_.Attributes.Name -eq "class" -and `
        $_.Attributes.Value -like "*attributed-text-segment-list__content*"}
    |Select-Object -First 1 -ExpandProperty InnerText
    $activity
    $post.shortContent = $post.postContent.Substring(0,[Math]::Min(200,$post.postContent.Length)-1)

    if($post.shortContent -ne ""){
      $post.summary = Invoke-OAIChat "$prompt $($post.shortContent)"
    }

    $match = [Regex]::Match($activity,$regex)
    $id = @{
        decimal         = ($match.Groups["id"]).Value
        binary          = ""
        timestampBinary = ""
        timestamp       = ""
    }
    $id.binary = [Convert]::ToString($id.decimal,2)
    $id.timestampBinary = $id.binary.Substring(0,41)
    $id.timestamp = [DateTimeOffset]::FromUnixTimeMilliseconds([Convert]::ToInt64($id.timestampBinary,2)).DateTime

    $post.activityId = $id
    $posts += $post
}
```
6. Now I keep all this activity in a SharePoint Online List for easy integration and analysis later, be sure to update the SPO Instance URL, Site Name, and List GUID below
```powershell
$site = Invoke-MgGraphRequest -Uri "v1.0/sites/<SpoInstanceUrl>:/sites/<SiteName>"
$list = Invoke-MgGraphRequest -Uri "v1.0/sites/$($site.id)/lists/<ListGuid>"

foreach($post in $posts|?{$_.Summary -ne ""}){
    $check = Invoke-MgGraphRequest -Uri "v1.0/sites/$($site.id)/lists/$($list.id)/items?`$expand=fields&`$filter=fields/LinkedInActivity eq '$($post.activityId.decimal)'"
    if(($check.Value|Measure-Object).Count -gt 0){
        Write-Warning "$($post.activityId.decimal) found in list, skipping"
        continue
    }
    $item = @{
        fields = @{
            Title = $post.summary
            ActivityType = "Social Post (LinkedIn/YouTube, etc...)"
            Partner = "To Do"
            BulkReference = $post.activity
            Relevant_x0020_When = $post.activityId.timestamp.ToString("yyyy-MM-ddTHH:mm:ssZ")
            LinkedInActivity = $post.activityId.decimal
        }
    }
    Invoke-MgGraphRequest -Uri "v1.0/sites/$($site.id)/lists/$($list.id)/items" -Method POST -Body $item|ConvertTo-Json
}
```
7. Filter your list using the To Do Partner value or alternate columns and update as necessary

Example of the results:

<img width="528" height="651" alt="image" src="https://github.com/user-attachments/assets/f3133333-4952-4f1d-b0ca-445efd61bd87" />

## Bonus

Doug, the author of PSAI, shared an awesome example with me of how using AI lets you reconsider how you approach work. This is a fairly deterministic and planned approach with rigid structure.

Alternatively you can just let AI figure it out:

```powershell
New-Agent -Tools Invoke-RestMethod | Get-AgentResponse '

provide a summary of the following LinkedIn activities, you can browse to these links using your tools:
https://www.linkedin.com/feed/update/urn:li:activity:7383533745330618368
https://www.linkedin.com/feed/update/urn:li:activity:7383532739548979200
https://www.linkedin.com/posts/douglasfinke_ai-that-works-the-sf-unconference-is-under-activity-7383507297903206400-zvu0
## Expected output
$post = @{
    activity    
    activityId  
    htmlDoc     
    postContent 
    shortContent
    summary     
}
'
```
