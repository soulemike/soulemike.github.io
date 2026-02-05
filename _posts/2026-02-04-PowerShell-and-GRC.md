# PowerShell and GRC: Moving from “Disable It” to “Manage It”

For years, many security conversations have started with the idea that hackers use PowerShell so it should be disabled. In reality, PowerShell is an essential operations tool. The real task is to manage risk so that organizations can use PowerShell safely while preserving the automation and efficiency that teams depend on.
 
## The Myth: “Hackers Use PowerShell, Disable It”
It is true that attackers abuse PowerShell. Disabling it entirely harms operational capability and often encourages workarounds that are even riskier. Mature organizations balance risks with benefits.

<img alt="image" src="https://github.com/user-attachments/assets/50a3bb49-384f-4d9d-b83d-536758a6ad52" />

<img alt="image" src="https://github.com/user-attachments/assets/4d432aec-703c-4489-9303-b3a8ff01f9c9" />

<img alt="image" src="https://github.com/user-attachments/assets/a278bb9c-eb94-45e8-8622-fa526027e5d9" />


## How Adversaries Hide: Understanding Obfuscation
Attackers commonly hide intent using hex encoding or other forms of obfuscation. By decoding these strings step by step, you uncover ordinary behavior concealed behind encoded data.

<img alt="image" src="https://github.com/user-attachments/assets/a4855e5e-6c73-4df7-bb04-60ba782c5089" />

<img alt="image" src="https://github.com/user-attachments/assets/22590c2d-c1b7-479a-b7d7-4f5f5543b7ea" />

<img alt="image" src="https://github.com/user-attachments/assets/45467313-76d3-408e-8b24-9d346da04b33" />

<img alt="image" src="https://github.com/user-attachments/assets/db4bd49c-349f-440b-8014-1a3436f3820e" />

## What Risk Really Means and How GRC Helps
Risk is a combination of probability and impact. GRC exists to ensure that organizations understand why a control is needed, what must be done, and what is actually happening.

<img alt="image" src="https://github.com/user-attachments/assets/dbeddd47-bfc6-473e-beea-c9ace9896f7e" />

<img alt="image" src="https://github.com/user-attachments/assets/bdb0df76-3739-40ed-b410-da3c00dd5fd7" />

<img alt="image" src="https://github.com/user-attachments/assets/a462d3f6-953c-4360-98da-bb269a1dc8d1" />

## Navigating Industry Frameworks Without Creating New Ones
Organizations operate within frameworks like ISO, COSO, FAIR, NIST, ITIL and COBIT. The goal is not to invent new standards but to apply existing ones consistently.

<img alt="image" src="https://github.com/user-attachments/assets/c9dc8c5f-ebbe-4cbb-87c9-c4b7215e5e0b" />

<img alt="image" src="https://github.com/user-attachments/assets/48ec82ec-de99-4c26-8df6-f70707ee217e" />

<img alt="image" src="https://github.com/user-attachments/assets/97cf0ecc-db05-4a2f-9232-88947cfd7c4f" />

## Is PowerShell Really the Issue
MITRE ATT&CK describes several techniques involving PowerShell misuse, such as T1059.001 and T1546.013.

<img alt="image" src="https://github.com/user-attachments/assets/c5f475f2-49d6-4a2f-90b6-90344707833a" />

## Practical Risk Mitigations for PowerShell
1. Observability through logging and EDR
2. Access governance with admin tiering and JEA
3. Script signing and software restriction policies
4. Inbound and outbound access control
5. Secret management and AppSec testing

<img alt="image" src="https://github.com/user-attachments/assets/11c21f9d-4e59-41cf-924c-d6caf23d1cbf" />

## Where to Begin: High Value Controls
Start with logging, EDR and remoting hygiene. Move next to script signing, admin tiering and software restrictions.

<img alt="image" src="https://github.com/user-attachments/assets/aa1be504-b60e-486c-a7e0-bc263bc2987d" />

## A Simple Three Phase Approach
Phase 1: Observe and contain

Phase 2: Establish trust

Phase 3: Institutionalize controls

[ASD's guidance](https://www.cyber.gov.au/business-government/protecting-devices-systems/system-administration/securing-powershell-in-the-enterprise) on this is a great starting point for applying these concepts.

## Conclusion
PowerShell is not inherently unsafe. The absence of proper governance is what creates risk. Managing PowerShell through GRC principles allows organizations to keep automation advantages while reducing attack surface.
