# A Hybrid Identity Maturity Model That Actually Delivers Security Outcomes

[Summary blog for this presentation at HIP Conf 2026.](https://www.hipconf.com/resources/a-hybrid-identity-maturity-model-that-actually-delivers-security-outcomes/)

Identity maturity is useful only when it changes risk.

A program can deploy MFA, migrate a SIEM, improve endpoint coverage, and still leave the weaknesses that make an identity attack dangerous. The practical test is whether the work reduces standing privilege, removes weak authentication, closes orphaned access, improves detection, or shortens recovery.

That is the premise behind the hybrid identity maturity model I presented at HIPconf 2026. The model organizes the work into four practices, 10 processes, 27 capabilities, and three maturity levels. More importantly, it ties progression to observable security outcomes rather than a score for its own sake.

> Slide references below use the visible conference deck numbering.

![Slide 2: A Hybrid Identity Maturity Model that Actually Delivers Security Outcomes](https://raw.githubusercontent.com/soulemike/soulemike.github.io/refs/heads/main/assets/hybrid-identity-maturity/slide-02-title.png)

*Slide 2: The presentation starts with a simple requirement for the model: maturity has to deliver a security outcome.*

## Maturity scores can describe motion without proving security

Most maturity models are good at inventorying activity. That can still be useful. It tells us what exists, where capabilities are deployed, and what work has been completed.

The problem appears when those measures become the definition of success.

Slide 11 uses three familiar examples: endpoint agent coverage, MFA enablement, and new SIEM log sources. Each can represent meaningful progress. None independently answers whether exposure to harm is lower. A control can be deployed broadly and still be weak, inconsistently enforced, poorly governed, or disconnected from the assets that matter most.

![Slide 11: The Wrong Question](https://raw.githubusercontent.com/soulemike/soulemike.github.io/refs/heads/main/assets/hybrid-identity-maturity/slide-11-wrong-question.png)

*Slide 11: Tool deployment and coverage are inputs. The security question is whether the resulting exposure changed.*

The more useful operating question is the one introduced on Slide 12: **Are we more secure?** That forces the program to connect implementation work to weaknesses removed and risk controlled.

## Security outcomes are the business question

Identity risk is already a business issue. Slide 18 frames common corporate risk statements around unauthorized access, stolen credentials, third parties, unavoidable incidents, and financial, regulatory, and reputational impact. It then maps those concerns to actions an identity program can actually take.

Shrink standing privilege. Strengthen authentication and lifecycle governance. Govern human and machine identities. Improve visibility, response, and recovery. Measure maturity by risks actively controlled.

![Slide 18: It’s a Named Risk in the 10-K](https://raw.githubusercontent.com/soulemike/soulemike.github.io/refs/heads/main/assets/hybrid-identity-maturity/slide-18-named-risk.png)

*Slide 18: The model connects enterprise risk statements to identity controls that can materially reduce exposure.*

Slide 23 extends that idea into a set of operational outcomes: reduced standing privileges, better visibility, stronger governance and accountability, faster response and recovery, and more automation with less toil. Those outcomes are useful because they change how leaders can prioritize investment. A new platform, policy, or automation should make one or more of them measurably better.

## Hybrid identity is where accumulated exceptions become risk

Hybrid environments rarely fail because one team designed them badly. They become complicated over time.

A service account survives because nobody is sure what depends on it. An application keeps a hardcoded dependency on a domain controller because modernization was deferred. One workforce gets phishing-resistant authentication while another remains on SMS. A policy stays disabled because an application owner expects it to break something.

The result is accumulated dependency. Slide 27 describes this with a useful analogy: **every workaround is a loan, and the interest comes due at hardening time.**

![Slide 27: The Hybrid Reality](https://raw.githubusercontent.com/soulemike/soulemike.github.io/refs/heads/main/assets/hybrid-identity-maturity/slide-27-hybrid-reality.png)

*Slide 27: Long-lived workarounds create dependencies across identity types, protocols, authentication strengths, and organizational ownership.*

This matters because the weakest part of the environment establishes the practical floor. A highly mature cloud control does not remove the exposure created by an unmanaged service account or a legacy authentication path that still reaches something important.

Slide 28 gives the model a concrete definition of risk: a threat meets a weakness and creates exposure. Attackers are the threat. Standing access, weak authentication, and accounts without clear ownership are weaknesses. Exposure is what an attacker can reach, and for how long, when the two meet.

![Slide 28: What We Mean by Risk](https://raw.githubusercontent.com/soulemike/soulemike.github.io/refs/heads/main/assets/hybrid-identity-maturity/slide-28-risk.png)

*Slide 28: The model focuses measurement on weaknesses because that is the part of the risk equation the identity program can directly change.*

That distinction gives the maturity model something useful to measure. The program may not be able to remove the threat, but it can remove weaknesses and reduce the resulting exposure.

## A maturity model needs a test

The test is simple: **what weakness was removed?**

Slide 31 organizes the progression into Crawl, Walk, and Run. Crawl is about seeing and controlling the environment. Walk modernizes and standardizes it. Run automates proven controls and reduces risk at scale.

![Slide 31: The Test of Maturity](https://raw.githubusercontent.com/soulemike/soulemike.github.io/refs/heads/main/assets/hybrid-identity-maturity/slide-31-test-of-maturity.png)

*Slide 31: Crawl, Walk, and Run represent increasing ability to remove weaknesses, not increasingly impressive labels.*

This sequencing matters. Automation applied to an environment that is still poorly understood can scale the wrong decision. Standardization applied before visibility can normalize incomplete data. Maturity has to create the conditions for the next stage.

## Four practices, each with an observable outcome

The model groups the identity landscape into four practices: Lifecycle Management, Access Management, Entitlement Management, and Threat Management.

![Slide 36: Four Practices](https://raw.githubusercontent.com/soulemike/soulemike.github.io/refs/heads/main/assets/hybrid-identity-maturity/slide-36-four-practices.png)

*Slide 36: The four practices cover the identity lifecycle, authentication, entitlement, and identity-aware detection and recovery.*

### Lifecycle Management

Lifecycle Management governs identities from creation to retirement. Its processes cover joiner, mover, and leaver workflows; credential issuance and rotation; and the lifecycle of human, service, and machine identities.

The progression on Slides 43 through 46 moves from manual tickets, shared credentials, and unmanaged machine identities toward event-driven provisioning, short-lived credentials, and lifecycle controls for every identity type. The outcome on Slide 46 is concrete: **no orphaned access, and access always matches reality.**

A useful operational test is equally concrete: can you name the owner of every service account?

### Access Management

Access Management controls how identities prove who they are. Slides 50 through 52 move protocols and authentication factors from legacy access and limited MFA toward conditional access, phishing-resistant authentication, passwordless methods, and continuous evaluation.

The outcome on Slide 52 is that every login is verified and credentials stop being the soft target. The first diagnostic question is straightforward: what still authenticates with a password alone?

### Entitlement Management

Entitlement Management governs who should have what, and when. Slides 56 through 59 cover access reviews, classification, and privileged access.

The progression moves from spreadsheet-driven reviews, undocumented sensitivity, and standing administrator rights toward continuous risk-prioritized certification, classification-driven access decisions, and just-in-time privilege. The outcome on Slide 59 is **least privilege that holds**, with no access lingering without a reason.

This is where the distinction between assigning least privilege and maintaining least privilege becomes operationally important. Access changes as people, systems, and business context change. The control has to keep up.

### Threat Management

Threat Management addresses identity-aware detection and incident preparedness. Slides 63 through 65 move from collected logs and generic policy toward correlated identity signals, automated response, session revocation, rehearsed playbooks, and tested recovery that includes tier-0 restoration.

The outcome on Slide 65 is fast detection and faster recovery. The practical maturity test is whether the organization has rehearsed identity recovery recently enough to know that the plan works.

Together, the four practices make maturity observable through changes in the operating environment. Ownership becomes clearer. Weak authentication disappears. Privilege becomes temporary. Recovery becomes rehearsed.

## Sequence is part of the risk strategy

The model's roadmap uses three stages: visibility, intelligence, and action.

Visibility answers who has access, to what, and how they got it. Intelligence standardizes the data so risk can be compared and ranked against business impact. Action removes the highest-risk standing access and automates decisions that have already been proven manually.

![Slide 69: Sequence for Risk Reduction](https://raw.githubusercontent.com/soulemike/soulemike.github.io/refs/heads/main/assets/hybrid-identity-maturity/slide-69-sequence.png)

*Slide 69: Visibility earns intelligence. Intelligence earns action. Skipping a stage risks automating a blind spot.*

The order changes the economics of the program. Better visibility reduces time spent discovering what exists. Standardized intelligence improves prioritization. Proven decisions are safer to automate. Each step creates leverage for the next rather than adding another disconnected control.

## Identity risk often lives in the seams between teams

Identity is a shared surface. GRC defines policy and review requirements. Operations provisions accounts and manages devices. Security detects abuse and responds. Application and data owners understand what the underlying systems are worth.

The failures often appear at the handoffs.

Slide 70 calls out several examples: policy authority that is never enforced in operations, device signals that one team produces and another trusts without validation, access granted without understanding the value of the data behind it, and classification that exists on paper but never reaches an access decision.

![Slide 70: Mind the Silo Seams](https://raw.githubusercontent.com/soulemike/soulemike.github.io/refs/heads/main/assets/hybrid-identity-maturity/slide-70-silo-seams.png)

*Slide 70: Identity becomes the shared surface across GRC, operations, security, and application or data ownership. Unowned seams become control gaps.*

This is an organizational design problem as much as a technical one. Mature identity programs need explicit ownership for the decisions that cross those boundaries, including who defines policy, who provides the signal, who validates it, and who is accountable when the signal is wrong.

## Build the roadmap around the next risk-reducing move

Slide 71 consolidates the model into an outcome-driven roadmap across Crawl, Walk, and Run. The point is not to push every capability to Run at the same time. The roadmap helps identify the next capability that removes a meaningful weakness.

![Slide 71: Your Outcome-Driven Roadmap](https://raw.githubusercontent.com/soulemike/soulemike.github.io/refs/heads/main/assets/hybrid-identity-maturity/slide-71-roadmap.png)

*Slide 71: The maturity model becomes a roadmap when each capability is tied to an observable security outcome.*

Slide 72 turns that roadmap into four immediate actions:

| Practice | Start here | If that is already done |
| --- | --- | --- |
| Lifecycle | Give every service account a named owner. | Put an expiry date on each one. |
| Access | List what still authenticates with a password alone. | Move administrators to phishing-resistant MFA. |
| Entitlement | List the accounts that could take over what you value. | Make that access time-bound. |
| Threat | Run one identity recovery drill end to end. | Time it, then shorten it. |

![Slide 72: What to Do Next](https://raw.githubusercontent.com/soulemike/soulemike.github.io/refs/heads/main/assets/hybrid-identity-maturity/slide-72-next.png)

*Slide 72: Pick one move per practice and create momentum from Crawl to Walk to Run.*

## Maturity is a means. Security is the goal.

A useful maturity review should make a decision clearer. It should show which weaknesses were removed, which exposures became smaller, where control still depends on an exception, and which proven decisions are ready to automate.

The score can still exist. It becomes supporting evidence rather than the objective.

The harder question is also the more useful one: **which line in your current identity maturity report would still matter if the product names and deployment percentages disappeared?**
