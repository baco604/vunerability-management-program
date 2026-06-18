# Official [Cyber Range](http://joshmadakor.tech/cyber-range) Project

# Vulnerability Management Program Implementation

In this project, we simulate the implementation of a comprehensive vulnerability management program, from inception to completion.

_**Inception State:**_ the organization has no existing policy or vulnerability management practices in place.

_**Completion State:**_ a formal policy is enacted, stakeholder buy-in is secured, and a full cycle of organization-wide vulnerability remediation is successfully completed.

---

<img width="1000" alt="image" src="https://github.com/user-attachments/assets/cfc5dbcf-3fcb-4a71-9c13-2a49f8bab3e6">

# Technology Utilized
- Tenable (enterprise vulnerability management platform)
- Azure Virtual Machines (Nessus scan engine + scan targets)
- PowerShell & BASH (remediation scripts)

---


# Table of Contents

- [Vulnerability Management Policy Draft Creation](#vulnerability-management-policy-draft-creation)
- [Mock Meeting: Policy Buy-In (Stakeholders)](#step-2-mock-meeting-policy-buy-in-stakeholders)
- [Policy Finalization and Senior Leadership Sign-Off](#step-3-policy-finalization-and-senior-leadership-sign-off)
- [Mock Meeting: Initial Scan Permission (Server Team)](#step-4-mock-meeting-initial-scan-permission-server-team)
- [Initial Scan of Server Team Assets](#step-5-initial-scan-of-server-team-assets)
- [Vulnerability Assessment and Prioritization](#step-6-vulnerability-assessment-and-prioritization)
- [Distributing Remediations to Remediation Teams](#step-7-distributing-remediations-to-remediation-teams)
- [Mock Meeting: Post-Initial Discovery Scan (Server Team)](#step-8-mock-meeting-post-initial-discovery-scan-server-team)
- [Mock CAB Meeting: Implementing Remediations](#step-9-mock-cab-meeting-implementing-remediations)
- [Remediation Round 1: Windows OS Updates](#remediation-round-1-windows-os-updates)
- [Remediation Round 2: Guest Account Group Membership](#remediation-round-2-guest-account-group-membership)
- [Remediation Round 3: Outdated Wireshark (Insecure Software)](#remediation-round-3-outdated-wireshark-insecure-software)
- [Remediation Round 4: Disable SMB Signing](#remediation-round-4-disable-smb-signing)
- [Remediation Round 5: RDP Without Network Level Authentication (NLA)](#remediation-round-5-rdp-without-network-level-authentication-nla)
- [Remediation Round 6: Weak LAN Manager Authentication Level](#remediation-round-6-weak-lan-manager-authentication-level)
- [First Cycle Remediation Effort Summary](#first-cycle-remediation-effort-summary)

---

### Vulnerability Management Policy Draft Creation

This phase focuses on drafting a Vulnerability Management Policy as a starting point for stakeholder engagement. The initial draft outlines scope, responsibilities, and remediation timelines, and may be adjusted based on feedback from relevant departments to ensure practical implementation before final approval by upper management.  
[Draft Policy](https://docs.google.com/document/d/1OKJTmrbmXi2_a5D4Pw6wwxP1OqCvLKAZU60fzUQmtdI/edit?tab=t.0)

---

### Step 2) Mock Meeting: Policy Buy-In (Stakeholders)

In this phase, a meeting with the server team introduces the draft Vulnerability Management Policy and assesses their capability to meet remediation timelines. Feedback leads to adjustments, like extending the critical remediation window from 48 hours to one week, ensuring collaborative implementation.

# Vulnerability Remediation Policy Discussion

## Participants
- **Josh** – Security Program Lead
- **Jimmy** – Department Representative

## Meeting Summary

**Josh:** Good morning, Jimmy. How have things been lately? I know everyone has been pretty busy these past few weeks.

**Jimmy:** Good morning, Josh. It's been a bit hectic, but we're managing. Thanks for asking. I had a chance to review the policy draft, and overall, it makes sense. However, given our current staffing levels, we won't be able to meet the aggressive remediation timelines—especially the 48-hour requirement for critical vulnerabilities.

**Josh:** I completely understand. It is fairly aggressive, particularly as we're getting started. Perhaps we could extend the remediation timeline for critical vulnerabilities to one week. That seems like a reasonable compromise for now, while reserving the 48-hour requirement for truly severe zero-day vulnerabilities.

**Jimmy:** That sounds reasonable. We appreciate the flexibility. Would it also be possible to have some leeway during the initial rollout as we get accustomed to the remediation and patching process over the first few months?

**Josh:** Absolutely. Once the policy is finalized, we'll officially launch the program, but we're planning to give all departments about six months to adjust and become comfortable with the new processes. Does that seem fair?

**Jimmy:** Yes, that sounds fair. We'll do our best. I appreciate you including us in the decision-making process. It really helps us feel like we're part of the solution.

**Josh:** Of course. We're all working toward the same goal. Thanks for collaborating with us.

**Jimmy:** No problem. Thanks for the brief meeting.

**Josh:** Those are my favorite kind. Take care.

**Jimmy:** You too. See you later.

---

## Key Outcomes

- The original **48-hour remediation requirement** for critical vulnerabilities was identified as unrealistic given current staffing constraints.
- The parties agreed to extend the remediation timeline to **one week** for most critical vulnerabilities.
- A **48-hour remediation window** will be reserved for severe or actively exploited zero-day vulnerabilities.
- Departments will be given a **six-month transition period** to adapt to the new remediation and patch management processes.
- Both parties emphasized the importance of collaboration and stakeholder involvement in policy implementation.

## Skills Demonstrated

- Security Policy Development
- Stakeholder Management
- Risk-Based Decision Making
- Vulnerability Management
- Negotiation and Consensus Building
- Change Management
- Cross-Functional Communication

---

### Step 3) Policy Finalization and Senior Leadership Sign-Off

After gathering feedback from the server team, the policy is revised, addressing aggressive remediation timelines. With final approval from upper management, the policy now guides the program, ensuring compliance and reference for pushback resolution.  
[Finalized Policy](https://docs.google.com/document/d/1f0Dg-vLPiXpBFjNUC8_YAyypdoX1-tpJQb0iVuAm3sk/edit?tab=t.0)
<div style="text-align: center;">
    <img src="https://github.com/user-attachments/assets/9afcdbc1-0493-4af2-9287-1cb9b8f59b40" alt="image" width="400">
</div>

---

### Step 4) Mock Meeting: Initial Scan Permission (Server Team)

The team collaborates with the server team to initiate scheduled credential scans. A compromise is reached to scan a single server first, monitoring resource impact, and using just-in-time Active Directory credentials for secure, controlled access.  

# Credentialed Vulnerability Scanning Planning Meeting

## Participants
- **Josh** – Vulnerability Management Lead
- **Jimmy** – Infrastructure Team Representative

## Meeting Summary

**Josh:** Good morning, Jimmy.

**Jimmy:** Good morning. I heard you're ready to conduct some scans.

**Josh:** Yep. Now that our vulnerability management policy is in place, I wanted to get started with scheduled credentialed scans of your environment.

**Jimmy:** Sounds good to me. What's involved? How can we help?

**Josh:** We're planning to schedule weekly scans of the server infrastructure. We estimate it will take about four to six hours to scan all 200 assets. We'll need administrative credentials that allow the scanning engine to remotely authenticate to the systems so it can perform a more comprehensive assessment.

**Jimmy:** Hold on a second. What does the scanning process actually entail? I'm concerned about resource utilization. Also, you're asking for administrative credentials to all 200 machines? That doesn't sound very safe.

**Josh:** Those are valid concerns. The scan engine sends various types of traffic to the servers to identify vulnerabilities. This includes checking system configurations, reviewing registry settings, identifying outdated software, and detecting insecure protocols or cipher suites. That's why authenticated access is required.

**Jimmy:** I see. As long as the scans don't impact performance or take servers offline, I think we'll be okay.

**Josh:** Absolutely. Let's start by scanning a single server and monitor resource utilization throughout the process.

**Jimmy:** That's a good idea.

**Josh:** Great. Regarding credentials, could your team create a dedicated Active Directory service account for scanning? The account could remain disabled until scan windows begin, then be enabled temporarily and disabled or deprovisioned afterward. Essentially, a just-in-time access model.

**Jimmy:** That sounds reasonable. I'll ask Susan to begin working on the account provisioning automation.

**Josh:** Excellent. Let's reconnect once everything is ready.

**Jimmy:** Sounds good. I'll get back to you once the credentials are set up.

**Josh:** Perfect. Talk soon.

**Jimmy:** See you later.

**Josh:** See you later.

---

## Key Outcomes

- Agreed to begin a credentialed vulnerability scanning program.
- Weekly scans will be conducted across approximately 200 server assets.
- Initial concerns regarding performance impact and security of administrative credentials were discussed and addressed.
- A pilot scan will be performed on a single server before expanding to the full environment.
- The infrastructure team will create a dedicated Active Directory scanning account.
- The scanning account will follow a **Just-in-Time (JIT) access** model, remaining disabled when not in use.
- Automation will be explored for account provisioning and deprovisioning.

## Technical Concepts Demonstrated

- Credentialed Vulnerability Scanning
- Vulnerability Management Program Implementation
- Active Directory Administration
- Just-in-Time (JIT) Access
- Principle of Least Privilege
- Server Infrastructure Security
- Secure Credential Management
- Vulnerability Assessment Methodologies
- Risk Mitigation
- Security Operations Collaboration

## Skills Demonstrated

- Stakeholder Communication
- Security Program Rollout
- Risk Assessment
- Technical Explanation for Non-Security Teams
- Change Management
- Cross-Functional Collaboration
- Security Governance
- Problem Solving

---

### Step 5) Initial Scan of Server Team Assets

In this phase, an insecure Windows Server is provisioned to simulate the server team's environment. After creating vulnerabilities, an authenticated scan is performed, and the results are exported for future remediation steps.  

<img width="1074" height="736" alt="Screenshot 2026-06-17 at 8 06 15 PM" src="https://github.com/user-attachments/assets/016f8cc7-d2e9-406f-bb2f-363d4096484f" />


[Scan 1 - Initial Scan](https://drive.google.com/file/d/1uJ92Ww9swfZfes9RcnQoHfAFcK5fJ1wf/view?usp=sharing)




---

### Step 6) Vulnerability Assessment and Prioritization

We assessed vulnerabilities and established a remediation prioritization strategy based on ease of remediation and impact. The following priorities were set:

1. Windows OS Updates (Re-enable and apply updates)
2. Guest Account Group Membership (Remove from Administrators)
3. Third-Party Software Removal (Outdated Wireshark)
4. Disable SMB Signing
5. RDP Without Network Level Authentication (NLA)
6. Weak LAN Manager Authentication Level

---

### Step 7) Distributing Remediations to Remediation Teams

The server team received remediation scripts and scan reports to address key vulnerabilities. This streamlined their efforts and prepared them for a follow-up review.  

[Remediation Email](https://github.com/baco604/remediation-email/blob/main/README.md)

---

### Step 8) Mock Meeting: Post-Initial Discovery Scan (Server Team)

The server team reviewed vulnerability scan results, identifying outdated software, insecure accounts, and deprecated protocols. The remediation packages were prepared for submission to the Change Control Board (CAB). 

# Vulnerability Scan Results Review and Remediation Planning Meeting

## Participants
- **Josh** – Vulnerability Management Lead
- **Jimmy** – Infrastructure Team Representative

## Meeting Summary

**Josh:** Good morning, Jimmy. How are you doing?

**Jimmy:** Not bad for a Monday. How about yourself?

**Josh:** I'm still alive, so I can't complain. Before we get into the vulnerability findings, I wanted to check in on the scan itself. How did everything go on your end? Did you experience any outages, performance issues, or resource overutilization?

**Jimmy:** The scan went well. We monitored the environment throughout the process, and aside from seeing the expected increase in open connections, we wouldn't have known a scan was taking place.

**Josh:** That's good news. I expected that we would have minimal impact, but we'll continue monitoring going forward. I don't anticipate any major resource utilization issues. Would you mind if we review the vulnerability findings?

**Jimmy:** Yeah, absolutely.

**Josh:** Great. I'll share my screen.

The majority of the findings appear to be related to **Wireshark installations**. As you can see, several servers have outdated versions installed, which is creating multiple vulnerabilities.

One additional finding that stood out was the **local guest account** on the servers. During further investigation, I found that the guest account is a member of the **local administrators group**, which is a security concern. I'm not sure why that configuration exists.

Some other findings may automatically resolve through standard Windows updates, such as the **Microsoft Edge Chromium vulnerability** and a few other Windows-related issues.

The **self-signed certificate finding** is not a major concern because it appears to be related to the default computer-generated certificate.

However, the findings related to **medium-strength cipher suites** and **TLS 1.0/TLS 1.1** are more important. These protocols and cipher suites are deprecated and should be removed or disabled.

Overall, the main remediation items are:
- Remove outdated Wireshark installations
- Remove the guest account from the local administrators group
- Disable deprecated TLS protocols
- Remove insecure cipher suites
- Apply required Windows updates

**Jimmy:** That's very interesting. The good news is that I suspect most of our servers will have the same vulnerabilities. Hopefully, having a consistent set of findings makes remediation easier.

**Josh:** That's actually good news. A uniform environment should make remediation more efficient. Do you anticipate any issues addressing the deprecated cipher suites or insecure protocols?

**Jimmy:** I highly doubt there will be any major issues. We'll run the changes through the next Change Control Board review.

Removing Wireshark and fixing the guest account should not be a problem since those configurations should not exist on production servers anyway. I'll need to coordinate with our server administrators to address those items.

**Josh:** That sounds good. I'll start building remediation packages to make the process easier when it's time to implement the fixes.

**Jimmy:** That would be great. I also wanted to ask: do you already have a process in place for addressing Windows update-related vulnerabilities? Do you have patch management implemented?

**Josh:** Yes, we do. I'm not concerned about those findings because Windows updates are already handled through our patch management process. The updates should be applied automatically by next week.

**Jimmy:** Excellent. I'll begin researching the best remediation approaches for these findings and will follow up before the next Change Control Board meeting.

**Josh:** Sounds good. Talk to you soon.

**Jimmy:** Talk to you soon.

---

## Key Outcomes

- The credentialed vulnerability scan completed successfully with minimal impact on server performance.
- No outages or significant resource utilization issues were observed during scanning.
- Several recurring vulnerabilities were identified across the server environment.
- Primary remediation tasks were identified:
  - Upgrade or remove outdated Wireshark installations.
  - Remove unnecessary local administrator privileges from the guest account.
  - Disable deprecated TLS 1.0 and TLS 1.1 protocols.
  - Remove weak or insecure cipher suites.
  - Apply outstanding Windows updates through existing patch management processes.
- The infrastructure team confirmed that most servers share similar configurations, which should simplify remediation efforts.
- Changes involving cipher suites and protocols will go through the Change Control Board process.
- Remediation packages will be developed to streamline implementation.

## Technical Concepts Demonstrated

- Vulnerability Assessment Review
- Credentialed Security Scanning
- Vulnerability Remediation Planning
- Patch Management
- TLS Protocol Hardening
- Cipher Suite Management
- Active Directory and Local Account Security
- Least Privilege Principle
- Change Management Processes
- Security Operations Collaboration

## Skills Demonstrated

- Vulnerability Analysis
- Risk Prioritization
- Security Reporting
- Stakeholder Communication
- Remediation Strategy Development
- Infrastructure Security Assessment
- Cross-Functional Collaboration
- Change Control Coordination
- Security Governance

---

### Step 9) Mock CAB Meeting: Implementing Remediations

The Change Control Board (CAB) reviewed and approved the plan to remove insecure protocols and cipher suites. The plan included a rollback script and a tiered deployment approach.  

# Change Advisory Board (CAB) Meeting – Secure Protocol and Cipher Suite Remediation

## Participants
- **Josh** – Risk Department / Vulnerability Management Lead
- **Jimmy** – Infrastructure Team Representative
- **CAB Members** – Change Advisory Board

## Meeting Summary

**CAB Chair:**  
Next on the agenda are two vulnerability remediation changes for the server team:

1. Removal of insecure protocols  
2. Removal of insecure cipher suites  

It looks like Josh from the Risk Department is working together with Jimmy from Infrastructure on this effort. Jimmy, would you like to walk us through the technical aspects of the proposed changes?

**Jimmy:**  
Normally, I would, but would you mind having Josh explain this one? He actually built the solution for us. We're still getting familiar with the process.

**Josh:**  
Sure, I can explain.

The issue with insecure cipher suites and protocols is that their presence on a system means the system is still capable of negotiating and using outdated cryptographic algorithms or deprecated communication protocols.

For example, if a system connects to another server that only supports those outdated protocols, there is a possibility that the connection could fall back to using weaker encryption methods.

These configurations are controlled through the **Windows Registry**.

The remediation itself is straightforward. We created a **PowerShell script** that:

- Identifies insecure protocols and cipher suites.
- Disables deprecated encryption protocols and algorithms.
- Enables approved protocols and cipher suites that align with current security standards.

The goal is to ensure systems only negotiate secure encryption methods.

**CAB Member:**  
That sounds good. However, what happens if something goes wrong? Do we have a rollback plan in place?

**Josh:**  
Yes, absolutely.

First, we are using a **tiered deployment approach**:

1. **Pilot Group** – A small set of systems used for initial validation.
2. **Pre-Production Testing** – Broader testing before deployment.
3. **Production Deployment** – Full rollout across the environment.

In addition, we developed and tested automated rollback scripts for each remediation.

If any unexpected issues occur, the rollback scripts can restore the original protocols and cipher configurations to return systems to their previous state.

**CAB Member:**  
That sounds good. Since the fixes are simple registry updates, I don't anticipate major concerns.

**Josh:**  
Exactly. The technical changes are relatively straightforward, but we still want to follow proper change management procedures and ensure we have testing and rollback capabilities before deployment.

**CAB Chair:**  
Great. Are there any additional questions?

**CAB Members:**  
No further questions.

**CAB Chair:**  
That concludes this week's Change Advisory Board meeting. See everyone next week.

---

# Key Outcomes

- Approved remediation plan for:
  - Removal of insecure communication protocols.
  - Removal of insecure cipher suites.
- A PowerShell-based remediation script was developed to automate configuration changes.
- The remediation modifies Windows Registry settings to disable deprecated security protocols.
- A phased deployment strategy was established:
  - Pilot testing
  - Pre-production validation
  - Production rollout
- Automated rollback scripts were created to restore previous configurations if unexpected issues occur.
- Change management procedures were followed through the CAB review process.

---

# Technical Concepts Demonstrated

- Change Advisory Board (CAB) Process
- Vulnerability Remediation
- Cryptographic Protocol Hardening
- Cipher Suite Management
- TLS Security Configuration
- Windows Registry Administration
- PowerShell Automation
- Secure Configuration Management
- Change Control
- Rollback Planning
- Risk Mitigation

---

# Skills Demonstrated

- Security Automation
- Vulnerability Management
- Change Management
- Technical Documentation
- Risk Assessment
- Security Engineering
- Infrastructure Collaboration
- Incident Prevention
- Stakeholder Communication
- Secure Systems Administration

---
### Step 10 ) Remediation Effort

#### Remediation Round 1: Windows OS Updates

Windows updates were re-enabled and applied until the system was fully up to date. A follow-up scan verified the changes.  

<img width="483" height="273" alt="Scan 2 - PASSED" src="https://github.com/user-attachments/assets/ce9682e4-f97f-4974-b067-048e111d98da" />

[Scan 2 - Windows OS Updates](https://drive.google.com/file/d/1lvDPKc9B1KD9-elIPNEYgjJWgQkcML-I/view?usp=sharing)


#### Remediation Round 2: Guest Account Group Membership

The server team removed the guest account from the administrator group. A new scan confirmed remediation, and the results were exported for comparison.  

<img width="732" height="217" alt="Scan 3 - PASSED" src="https://github.com/user-attachments/assets/06cbcc85-3f5b-45ac-af32-72133d1546f5" />

[Scan 3 - Guest Account Group Removal](https://drive.google.com/file/d/1PFk99NHiRI8HjTdOML1FlXxAJgDYcM1z/view?usp=sharing)


#### Remediation Round 3: Outdated Wireshark (Insecure Software)

The server team used a PowerShell script to remove outdated Wireshark. A follow-up scan confirmed successful remediation.  

<img width="768" height="464" alt="Scan 4 " src="https://github.com/user-attachments/assets/ca0dc272-0107-4169-bec3-0722ada6cb2a" />

[Scan 4 - Third Party Software Removal](https://drive.google.com/file/d/1Kxuu94vrOjxUg877kuc7emvRpebxbwu2/view?usp=sharing)


#### Remediation Round 4: Disable SMB Signing

SMB Signing was enabled on the server to enforce message authentication and prevent man-in-the-middle attacks. A follow-up scan confirmed successful remediation.  

<img width="772" height="418" alt="Scan 5" src="https://github.com/user-attachments/assets/3ff7d567-76d3-4f48-9add-b95608dd5b74" />

[Scan 5 - SMB Signing Remediation](https://drive.google.com/file/d/141rh9HTfvl3whHV5f5PTTN78e4Lw7ULD/view?usp=drive_link)


#### Remediation Round 5: RDP Without Network Level Authentication (NLA)

Network Level Authentication (NLA) was enabled for Remote Desktop connections to require authentication before a session is established. A follow-up scan confirmed successful remediation.  

<img width="785" height="384" alt="Scan 6" src="https://github.com/user-attachments/assets/a2a0e86e-60ca-4342-82db-6696847da3a4" />

[Scan 6 - RDP NLA Remediation](https://drive.google.com/file/d/1SLP0PyHgNcaCjeTElQjGpTfCmkjuE509/view?usp=drive_link)


#### Remediation Round 6: Weak LAN Manager Authentication Level

The LAN Manager authentication level was configured to only allow NTLMv2 responses and refuse LM and NTLM. A follow-up scan confirmed successful remediation.  

<img width="782" height="357" alt="Scan 7" src="https://github.com/user-attachments/assets/e98566c1-ff3b-4349-82ed-d2c6f3aafdae" />

[Scan 7 - LAN Manager Authentication Remediation](https://drive.google.com/file/d/1Ra9dBBUSqF0CPm3pGZEO6hq7CEDtLuZc/view?usp=drive_link)

---

### First Cycle Remediation Effort Summary

The remediation process reduced total vulnerabilities by 81%, from 26 to 5. Critical vulnerabilities were fully resolved (100%), and high vulnerabilities dropped from 8 to 1 (88% reduction). Medium vulnerabilities were reduced from 15 to 3 (80% reduction). The remaining vulnerabilities (SQLite, Microsoft Edge, SSL certificates, and ICMP Timestamp) will be addressed in the next remediation cycle. In an actual production environment, asset criticality would further guide future remediation efforts.

<img width="623" height="388" alt="image" src="https://github.com/user-attachments/assets/da9d11ee-8447-43b3-870a-7e6f696b3b8e" />

[Remediation Data](https://docs.google.com/spreadsheets/d/1FTtFfZYmFsNLU6pm8nTzsKyKE-d2ftXzX_DPwcnFNfA/edit?gid=0#gid=0)

---

### On-going Vulnerability Management (Maintenance Mode)

After completing the initial remediation cycle, the vulnerability management program transitions into **Maintenance Mode**. This phase ensures that vulnerabilities continue to be managed proactively, keeping systems secure over time. Regular scans, continuous monitoring, and timely remediation are crucial components of this phase. (See [Finalized Policy](https://docs.google.com/document/d/1rvueLX_71pOR8ldN9zVW9r_zLzDQxVsnSUtNar8ftdg/edit?usp=drive_link) for scanning and remediation cadence requirements.)

Key activities in Maintenance Mode include:
- **Scheduled Vulnerability Scans**: Perform regular scans (e.g., weekly or monthly) to detect new vulnerabilities as systems evolve.
- **Patch Management**: Continuously apply security patches and updates, ensuring no critical vulnerabilities remain unpatched.
- **Remediation Follow-ups**: Address newly identified vulnerabilities promptly, prioritizing based on risk and impact.
- **Policy Review and Updates**: Periodically review the Vulnerability Management Policy to ensure it aligns with the latest security best practices and organizational needs.
- **Audit and Compliance**: Conduct internal audits to ensure compliance with the vulnerability management policy and external regulations.
- **Ongoing Communication with Stakeholders**: Maintain open communication with teams responsible for remediation, ensuring efficient coordination.

By maintaining an active vulnerability management process, organizations can stay ahead of emerging threats and ensure long-term security resilience.
