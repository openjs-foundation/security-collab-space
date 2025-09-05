# Coordinated Vulnerability Disclosure (CVD) Step-by-Step Runbook Guide for Teams

# Purpose and Scope

### When to use this Guide

This step-by-step runbook guide is designed for those with limited exposure and experience working with coordinated vulnerability disclosure. The approach taken with this guide can be quite heavy and is designed for Projects with medium and large maintainer teams responding to external security vulnerability disclosures.

### When this Runbook Should Not be Used

Please be mindful that this runbook IS NOT an incident response plan. Unlike an Incident Response Plan, this runbook does not provide guidance on how to handle scenarios when there is concern or evidence of compromise of an Project’s infrastructure, tools, source code, communications, or maintainer devices.

# How to use this Runbook

## Take it Step by Step

Recommendation: Folow the steps in order. Steps are written with the assumption of knowledge being available after the completion of previous steps. Steps that can or should happen in parallel to each other are identified and also have supporting guidance.

## Associated Resources

This guide is meant to be used in conjunction with:

* [TEMPLATE Step-by-Step CVD Guide Checklist](https://../TEMPLATE-CVD-Step-by-Step-Runbook-Checklist.md)
* [Researcher Communications Templates](https://../Researcher-Communications.Primer.md)

# Roles and Responsibilities

Besides the On Call Role, this runbook uses the roles defined the GitHub Private Vulnerability Reporting (PVR) [documentation](https://docs.github.com/en/code-security/security-advisories/working-with-repository-security-advisories/creating-a-repository-security-advisory#about-credits-for-repository-security-advisories).

* Finder
* Reporter
* On Call
* Triage Analyst
* Coordinator
* Remediation Developer
* Remediation Reviewer
* Remediation Verifier

## Introduced in Phase 0: Report Submission

### Responsibilities: Finder

* Identifies the security vulnerability

### Responsibilities: Reporter

* Submits the vulnerability Report
* Adds othe Finder(s) who discovered the security vulnerability as Collaborators
* Responds to questions and coordination requests from the Project
* Validates the remediation patch

>[!NOTE]
>In most cases the Reporter likely to also be the Finder. The role of Reporter is used throughout this runbook.

## Introduced in Phase 1: Tier 1 Triage

### Responsibilities: On Call (credited in GH as Triage Analyst)
* Determine if the Report is a potential Security Vulnerability
* Determine if the Report Needs More Information (NMI) to Triage and Reproduce
* Send the appropriate initial acknowledgement to the Reporter
* Summarize the vulnerability and next steps for others on the team

### Responsibilities: Coordinator

* Assist Triage Analyst w Documentation
* Gather Feedback, Edit and Send NMI Response
* Fasciliate Discussions with Team
* Organize and Track Fix Action Items
* Informs Reporter of Tier 2 Triage Decision
* Send Reporter Regular Updates (as appropriate)
* Drafts and Gathers Feedback on Public Security Advisory
* Propose Updated CVSS v3.1
* Propose Updated CWE

>[!NOTE]
>It's possible that the Triage Analyst and Coordinator roles will be performed by the same individual during Tier 1 Triage. In some Projects, the Coordinator role may transition to another person dedicated person during the Tier 2 Triage or Fix Phases.

## Introduced in Phase 2: Tier 2 Triage

### Responsibilities: Triage Analyst

* Reproduce the Vulnerability
* (if NMI to repro) Document Reproduction Challenges and Steps Taken
* Assess and Document Impact
* Validate and/or Document Erroneous Reporter Assertions
* Assess and Document True Root Cause(s)
* Propose Fix Options (Mitigation and/or Remediation)
* Identify Fix Resourcing and Time Requirements 

### Responsibilities: Remediation Developer

* Reproduce the Vulnerability for Themselves
* Perform Additional Root Cause Analysis (as needed)
* Draft the Technical Portion of the Short-Term Mitigation Plan (as needed)
* Draft the Technical Mitigation/Remediation Plan(s)
* Author Code Changes per the Plan(s)
* Test Repro Steps the Against Patch to Verify Fix Efficacy
* Author Documentation Changes (as needed)

### Responsibilities: Remediation Reviewer

* Reproduce the Vulnerability for Themselves
* Review and Provide Inputs to Mitigation/Remediation Plans
* Review Mitigation/Remediation Pull Requests

### Responsibilities: Remediation Reviewer

* Reproduce the Vulnerability for Themselves
* Review and Provide Input to Mitigation/Remediation Plans
* Perform Testing to Verify Remediation Efficacy

# Start of Runbook

# 1. The Reporter submits a potential security concern or vulnerability

A Reporter can use [this workflow in GitHub](https://docs.github.com/en/code-security/security-advisories/guidance-on-reporting-and-writing-information-about-vulnerabilities/privately-reporting-a-security-vulnerability#privately-reporting-a-security-vulnerability) to create a new Security Advisory. This is the first step of the Coordinated Vulnerability Disclosure process!

Once they click ***Submit Report*** on the Report a Vulnerability page, three things happen:

1. A new Security Advisory is created in the repository they reported in.
2. Members of the Repository's Owners group are notified.
3. The Reporter will receive a confirmation email.

> [!NOTE]
> #### GitHub Security Advisory Triage State Transitions
> GitHub Security Advisories are created in the `Triage` state. Only two state transitions are available from `Triage`:
> - `Closed` by clicking ***Close Security Advisory*** under the Advisory's Comment box.
> - `Draft` by clicking ***Accept and open as Draft***

### 1a. (Optional) Reporter creates a temporary private fork

This feature cannot be disabled. [Click here](https://docs.github.com/en/code-security/security-advisories/working-with-repository-security-advisories/collaborating-in-a-temporary-private-fork-to-resolve-a-repository-security-vulnerability) to read more about the pros/cons and limitations of GitHub Temporary Private Forks.

![Screenshot](https://docs.github.com/assets/cb-51900/mw-1440/images/help/security/advisory-start-a-temporary-private-fork-button.webp)

# 2. [T1] On Call Performs Tier 1 Triage and Drafts an Initial Acknowledgement

In this Step, it is the On Call's responsibility to to determine which of the following criteria are relevant to the Report in order to determine the best way to proceed with an Initial Acknowledgement.

- 2a. Contains any of the Security Escalation Criteria
- 2b. Is missing data to understand or reproduce the vulnerability
- 2c. Is not a security vulnerability report 
- 2d. Contains any of the Abuse Escalation Criteria
- 2e. Is a routine security vulnerability Report

> [!TIP]
Remember, it's not necessary during Tier 1 to have a full understanding of the vulnerability. It is not necessary to reproduce the issue at this time.

## 2a. Security Escalation Criteria

| Reason | Description |
| -------- | -------- | 
| **Already Publicly Disclosed (0day)** |  The vulnerability has been disclosed publicly regardless of intent, context, or whether it has since been taken down. |
| **Active Exploitation** | The vulnerability has a functional exploit and there is evidence it has been weaponized by a malicious actor. |
| **Critical Severity** | Obviously critical or CVSS Score => 9.0. Be sure to validate using the CVSS Calculator and/or phone a friend first.   |
| **Disclosure Threats** | Threats of uncoordinated public disclosure not within our [VDP] without implied exortion. |

> If the Report passes the Step 2 checks, draft your response using the [Initial Acknowledgement: Security Escalation Template].

## 2b. Need More Information?

Our [Vulnerability Disclosure Policy] describes what fields and information we need to independently triage and reproduce potential security vulnerabilities.

Be sure to read the entire report for any obviously information that would be needed during later triage. It's ok if you miss something subtle and we have to go back and ask for more information latter. While all information is important, key points to focus on are:

- Steps to Reproduce
- Proposed Impact
- Proof of Exploitability

> If the Report is missing information but passes the other Step 2 checks, draft your response by listing the information you believe is needed using the [Initial Acknowledgement: Need More Information Template].

## 2c. Not a security vulnerability report?

Our initial acknowledgement should demonstrate that the Report was at least read for comprehension and that a templated response just not just blindly sent to meet a published SLAs. Be sure to check for:

- Spam
- Feature Requests
- Bug Reports
- Questions and Other Requests

> - If the Report does not meet any other criteria in Step 2 and isn't spam: draft your response using the [Initial Acknowledgement: Non-Security Report Template] and customize it to help Reporter with the non-security issue or question they have.
> 
> - If the Report is spam: Do not respond and move the Report to the `Closed` stateby clicking *Close Security Advisory* and report the user for spam using [GitHub’s Reporting Abuse or Spam instruction](https://docs.github.com/en/communities/maintaining-your-safety-on-github/reporting-abuse-or-spam).

## 2d. Abuse Escalation Criteria

| Reason | Description |
| -------- | -------- | 
| **Extortion Threats** | Demands for money to provide a detailed bug report or to not prematurely disclose the vulnerability.   |
| **Personal Threats** | Subtle and non-subtle threats against the Project or individuals   |

> [!CAUTION]
> Do not respond to the report or change its state. Without more specific insight to the situation, at the minimum immediately report the user for abuse using [these instructions](https://docs.github.com/en/communities/maintaining-your-safety-on-github/reporting-abuse-or-spam).

## Roles and Responsibilities

### On Call
| Responsibilities | 
| -------- | 
| Determine if the Report is a potential Security Vulnerability      |
| Determine if the Report Needs More Information (NMI) to Triage and Reproduce       | 
| Send the appropriate initial acknowledgement to the Reporter      | 
| Summarize the vulnerability and next steps for others on the team      |


# 3. [T1] On Call Begins Organizing Internal Discussion by Creating a Tracking Discussion for the Vulnerability

If the Report appears to contain a valid security vulnerability or meets an escalation criteria, the On Call begins documenting the Report and their Tier 1 Triage by creating a new GitHub Discussion in the [Private SecurityWG Repo].

1. The body of the discussion should be a copy/paste of the initial vulnerability Report.
2. The Tier 1 Summary (discussed in Step 4) is added to the discussion as the first comment.
3. The proposed Initial Acknowledgement response (discussed in Step 2) is added to the discussion as the second comment.

> [!TIP]
> The Tier 1 Summary and proposed Initial Acknowledgement are added as comments to leverage GitHub Discussion threading functionality. 

# 4. [T1] On Call Drafts a Tier 1 Summary

### Kicking Off Internal Comms with a Tier 1 Summary 

Filling out a [Security Vulnerability Tier 1 Summary Template] is designed to help the On Call quickly and in a standardized way communicate their perspective and understanding of the reported vulnerability to others.

By answering a set of early questions, it gives others an easy-to-consume tl;dr to kick off discussion and next steps about the vulnerability.

| Template | Description | Use
| -------- | -------- | -- |
| [Security Vulnerability] | For use with Security Escalations and Routine vulnerability reports      | Required
| [Non-Security Report]     | For use when the On Call wants to prompt discussion on how to handle/respond to a non-security topic      | Optional
| [Abuse Escalation] | For use when a Report that meets Abuse Criteria       | Required

### Request and Incorporate Feedback on the Initial Acknowledgement

This Step comes before sending the Initial Acknowledgement to the Reporter so the On Call can hear any internal feedback. 

> [!IMPORTANT]
> Remember, during Tier 1 Triage it is expected that responses are preliminary and potentially accurate pending further triage. 

# 5. [T1] On Call Sends the Reporter an Initial Acknowledgement of Receipt



This Initial Acknowledgement is probably the first time you have ever communicated with this Reporter/Security Researcher. The first few days after submitting a vulnerability report to a Bug Bounty or CVD Program are the most uncertain for a security researcher, especially if this is the first time they've submitted a vulnerability to your Program.

The most important thing your Initial Acknowledgement should do is:
- Demonstrate that you have actually read and understand their Report by matching tone and urgency if the Report matches the [Security Escalation Criteria].
- Clearly set expectations on what and when they can expect to hear from you next.

> [!IMPORTANT]
> Do not click `Accept and Open as Draft` during Tier 1 Triage. This should only happen once Tier 1 Triage is complete and the [SecurityWG] agrees to fix the vulnerability.

### 5a. If the Report meets Security Escalation Criteria

- Using a templated response is fine so long as the tone meets their expectations. The [Initial Acknowledgement: Security Escalation Template] is available for this purpose.
- You may want to consider brief Report-specific customizations to the situation.
- Enter your Response the Comment box and send by clicking `Comment`.

### 5b. If the Report Appears to be Missing Basic Information

- Be thoughtful on whether to ask for this information at this stage using the [Initial Acknowledgement: Need More Information Template].
- You're asking the Reporter to do work they didn't think to do or maybe don't think they should have to do with this request. Only use this Template if you're confident that the missing data would prevent you from completing Tier 2 Triage.
- Enter your customized response the Comment box and send by clicking `Comment`.

### 5c. If the Report Appears to be a Valid and Routine

- Enter the [Initial Acknowledgement: Routine Template] in the Comment box and send by clicking `Comment`.

### 5d. If the Report is not a Security Vulnerability

- Enter a [Initial Acknowledgement: Not a Vulnerability Template] customized to the situation in the Comment box and send by clicking `Close Security Advisory`

> [!NOTE]
> The Tier 1 Triage Phase is now complete and you transition to the Tier 2 Triage Phase! Congrats! \ o /

# 6. [T2] Assign Tier 2 Triage Roles

Depending on the size of the [SecurityWG], a sizable number of individuals can effectively participate in order to distribute the load of effectively handling CVD.

During the Tier 2 Triage Phase, the two minimum Roles to assign are:
- Triage Analyst
- Coordinator

## Roles and Responsibilities

### Roles and Responsibilities: Triage Analyst

| Responsibilities | 
| -------- | 
| Reproduce the Vulnerability     |
| (If NMI to Repro) Document Challenges and Steps Taken      | 
| Assess and Document Impact     | 
| Validate and/or Document Erroneous Reporter Assertions      |
| Assess and Document True Root Cause(s)     | 
| Propose Fix Options (Mitigation and/or Remediation)     |
| Identify Fix Resourcing and Time Requirements      | 

### Roles and Responsibilities: Coordinator 

| Responsibilities | 
| -------- | 
| Assist Triage Analyst w Documentation     |
| Gather Feedback, Edit and Send NMI Response     |
| Fasciliate Discussions with Team     | 
| Organize and Track Fix Action Items     |
| Informs Reporter of Tier 2 Triage Decision
| Send Reporter Regular Updates (as Appropriate) |
| Drafts and Gathers Feedback on Public Security Advisory      | 
| Propose Updated CVSSv3     | 
| Propose Updated CWE     | 

# 7. [T2] Triage Analyst Attempts to Reproduce the Vulnerability as Reported 

During this Step, the Triage Analyst's primary responsibility is to reproduce the vulnerability as described in the Report. The information gathered by this work will be the basis for future decision making.

### Document More Detailed Reproduction Steps

While attempting reproduction, it is common to find omissions and errors in the Reporter's Repro Steps. Using the original Report as a base, the Triage Analyst should - as needed - clean up and more thoroughly document the their environment, tools, and steps that were not captured by the Reporter for use by others on the team.

#### Success: Two Person Verification

This runbook recommends that once the vulnerability is successfully reproduced by the Triage Analyst, a second team member should validate this using the updated Repro Steps.

> [!IMPORTANT]
> The Reporter should be notified using the [guidance in Step 8b] as soon as the vulnerability in their Report is repeatedly reproducable. The additional root cause and impact analysis work described below in [Step 9] **should not block** this notification.

### Unable to Reproduce: Need More Information (NMI)

It's not uncommon for errors and omissions in initial vulnerability Reports to prevent a team from successfully reproducing the vulnerability the first few times. The Triage Analyst should capture the detailed Repro Steps they have followed and use this information to identify where they encountered challenges or discrepencies from the original Report.

Despite the inability to reproduce and validate the vulnerability, at this Step the Report should continue to be treated as a valid vulnerability until definitively proven otherwise.

#### NMI: Two Person Verification

This runbook recommends that if the Triage Analyst is unable to reproduce the vulnerability, another member of the team should make an independent attempt in order to control for environmental factors and natural human error. Te Reporter be notified of this only once two team members have independently failed to reproduce the vulnerability.

> [!TIP]
> Guidance on how to optimize for comms success when requesting more information from the Reporter is discussed in [Step 8a].

# 8. [T2] Coordinator Notifies Reporter of Reproduction Progress

This notification is probably the first in-depth communication you've ever had with this Reporter. Be sure to check out the [Researcher Comms Primer] to help set you up for success! 

## 8a. First Notification: Unable to Reproduce / NMI

Informing a Reporter that you're unable to reproduce their vulnerability is something that should be done carefully and thoughtfully:
- It's not a great look if it turns out you missed something silly or obvious.
- Some may misinterpret it as the first step towards claiming their vulnerability is invalid.
- You're potentially asking them to go back and do work they didn't think to do originally, don't think they should have to do, or can't do because they dont know how.

Use the [Tier 2 Triage Response: NMI Template] as the basis for your request. Be sure to include as much detail as possible from your own Repro Steps in the template so they see that you have taken their Report seriously and understand what they sent. This template also asks them to send a video demonstrating that they can execute the attack.

- Enter your response in the Comment box and click `Comment`.

## 8b. Second/Ongoing Comms: Still Unable to Reproduce

- If the Reporter has not yet provided a video demonstrating their ability to execute the exploit, you may want to consider closing the Report.

## 8c. Notification: Successful Reproduction

As soon as at least two members of the team have been able to independently reproduce the vulnerability, you should notify the Reporter. The [Tier 2 Triage Response: Successful Reproduction Template] can be used without customization, but probably should if the Report meets the Security Escalation Criteria.

- Enter your response in the Comment box and click `Comment`.

> [!IMPORTANT]
> The template provided assumes that the true root cause and remediation plan are not yet fully understood. Only transition the Report's state from `Triage` by clicking ***Accept and Open as Draft*** once there is consensus on the true root cause and the remediation plan. Guidance for this state transition is found in [Step 11].

# 9. [T2] Triage Analyst Determines the True Root Cause(s), Impact, and Severity 

## 9a. Identify and Document True Root Cause(s)

Determining the true root cause(s) allows the Triage Analyst and the team to gain a more thorough understanding of the real vulnerability underlying the Report's behavior.

> [!TIP]
> This runbook recommends that vulnerabilities that have been successfully reproduced should not be considered validated until the true root cause(s) are known. The reason for this is that the behavior demonstrated in the Reporter's Reproduction Steps may only represent one of many ways to exploit the vulnerability.

The true root cause(s) should be documented in simple, short language that does not require extensive context of the product to understand. More complex writing happens when capturing the Impact of the vulnerabilities caused by the root cause(s) and proposing potential mitigations or remediations that address the true root cause(s).

Specific information that should be captured during root cause analysis also includes:

> - The pull request(s) that introduced the vulnerability
> - List of vulnerable products and version numbers

## 9b. Assess and Document Impact and Exploitability

Once the true root cause(s) are known, for each root cause the Triage Analyst should independently assess and document the impact and exploitability of the the actual vulnerability (which may differ from the Report) in **detail** and in a **brief summary**.

### Important Details to Capture

- **Problem:** The flaw/software defect of the root cause..
- **Attack:** What would a real world attack using this vulnerability look like? Be sure to include the target conditions needed for success.
- **Impact:** When successfully exploited, what are the direct and indirect impacts?

### Assess the Reporter's Assertions

As part of this, the Triage Analyst should also explicitly identify and any unsupported or erroneous assertions in the original Report in a fact-based, dispassionate tone to to ensure the team and Reporter have a shared understanding of the actual vulnerability.

### Brief Security Advisory Description

In addition to the detailed description of the vulnerability and its root cause(s), the initial first draft of the brief Security Advisory should be written. This should be written with sufficient detail to demonstrate that the vulnerability is unique. Descriptions often follow this template:

     [PROBLEM TYPE] in [PRODUCT/VERSION] causes [IMPACT] when [ATTACK]

- First draft of the proposed Security Advisory Description
- First draft of the proposed CVSSv3 Base Score
- First draft of the proposed CWE

> [!NOTE]
> It's likely that this description will evolve over time. There are reminders to keep this updated throughout this runbook to help the [SecurityWG] stay aligned on their understanding of the vulnerability.

## 9c. Document Initial Mitigation/Remediation Options

For each root cause, the Triage Analyst should *briefly* document initial proposed:

- **Mitigations:** if being actively exploited and/or for those are  unlikely to upgrade
- **Breaking Remediation:** code changes that fully remediate the true root cause(s) of the vulnerability that are breaking changes for users
- **Non-Breaking Remediation:** Alternative code changes that fully remediate the true root cause(s) of the vulnerability that ARE NOT breaking changes for users

> [!IMPORTANT]
> This brief, initial proposal by the Triage Analyst and Coordinator is not meant to be the final fix plan as the Triage Analyst may not be the same person who should design and author the remediating code changes. This deliverable is intended to provide a foundation for team-wide collaboration and consensus building only.

# 10. [T2] Coordinator Facilitates Consensus Building Discussions

Once data gathering and analysis for Tier 2 Triage is complete, the final step for Tier 2 Triage is for the [SecurityWG] to reach a consensus on:

- 10a. Their shared understanding of the draft Tier 2 Triage deliverables
- 10b. Whether to completely remediate the security vulnerability
- 10c. The Remediation Developers who will actually write the mitigation(s)/remediation(s)

> [!TIP]
> The Tier 2 Triage analysis and deliverables should be treated as an early initial analysis of the vulnerability and should not be considered a complete or "final" analysis or understanding of the vulnerability. This is because it is common for additional insights to be discovered in later stages, particularly during Remediation Developering.

## 10a. Reach Technical Consensus on Tier 2 Triage

The [SecurityWG] should use the draft Tier 2 Triage deliverables as a foundation for discussion and consensus building.

The Triage Analyst and Coordinator should update the initial draft Tier 2 Triage deliverables to include new information and perspectives from this discussion.

At the minimum, to complete Tier 2 Triage the [SecurityWG] must agree on the following as currently understood, including any caviats and gaps that arise during the discussion:

- Root cause(s) and the pull requests that introduced the vulnerability
- Vulnerability Impact and Exploitability
- List of vulnerable products and version numbers
- Draft of the Security Advisory Description
- CVSSv3 Base Score and CWE
- Whether the vulnerability meets the Security Escalation Criteria

It is not necessary for there to be consensus on the initial, brief Tier 2 Triage Mitigation and/or Remediation Options to complete Tier 2 Triage.

> [!TIP]
> As more eyes look into the vulnerability using the initial Tier 2 Triage deliverables as a guide, the Triage Analyst should expect a flood of new information and perspective, leading to substantial changes in their work product. This is common and not a reflection of quality of the Tier 2 Triage or of the Triage Analyst.

## 10b. Agree to Completely Remediate the Vulnerability 

In a perfect world all known security vulnerabilities would be completely remediated.

However, in practice there are scenarios where it may not be appropriate or possible to immediately prioritize a code change that completely remediates the reported behavior.

This runbook assumes that the [SecurityWG] will choose to completely remediate the vulnerability whenever possible, even if this choice requires negotiating a longer disclosure timeline with the Reporter due to the effort required for remediation.

#### Common Won't Fix Scenarios

- The attack is theoretical and not proven to be exploitable after real world testing.
- Exploitation is only proven in artificial scenarios that are unlikely to be encountered in the real world due to their rarity or complexity.
- Impact is extremely low for the required engineering effort.
- Complete remediation requires substantial refactoring of a feature for which the required engineering resources do not exist.
- Exploitation is only possible when the target intentionally disables one or more default security features or protections.
- Exploitation is only possible when the target is using antiquated EoL software that should no longer be used due to the absence of modern security protections.

> [!NOTE]
> This runbook makes a binary assumption that a CVD Report is either a security vulnerability or is not a security vulnerability.
> 
> However, not all valid Reports from security researchers and pen testers are actually security vulnerabilities. They may actually be describing the absence of a security feature or functionality that has a security-positive impact for which the target is expected to have compensating controls.


## 10c. Assign Remediation Roles and Agree on Mitigation/Remediation Next Steps

Only once a consensus is reached on their shared technical understanding of the vulnerability is established, the [SecurityWG] can then agree on a vision and next steps to fix the security vulnerability.

- Additional information needed to prepare Mitigation/Remediation Plan(s)
- A tentative patch release date, especially if this is expected to be >90 days 
- Which editions and versions will be patched
- Whether a Mitigation Plan is possible for older versions
- Whether to ask the Reporter for feedback on the Mitigation/Remediation Plan(s)

The [SecurityWG] should also identify the who individuals who will act as:

- Remediation Developer(s) who will build the Mitigation/Remediation Plan(s)
- Remediation Developer(s) who will build the Release Plan
- Remediation Reviewer(s) who will review pull requests and test the fix
- Fix Approver(s) who will accept the pull requests and test the fix

> [!TIP]
> To complete Tier 2 Triage it is not necessary to have a fully fleshed out Mitigation/Remediation or Release Plans. All that is needed is to agree on next steps and identify the individuals responsible for building out the plans.

## Roles and Responsibilities

### Roles and Responsibilities: Remediation Developer

| Responsibilities | 
| -------- | 
| Reproduce the Vulnerability for Themselves     |
| Perform Additional Root Cause Analysis (as needed)      | 
| Draft the Technical Portion of the Short-Term Mitigation Plan (as needed)     | 
| Draft the Technical Mitigation/Remediation Plan(s)         |
| Author Code Changes per the Plan(s)     |
| Test Repro Steps the Against Patch to Verify Fix Efficacy     |
| Author Documentation Changes (as needed)      | 

### Roles and Responsibilities: Remediation Reviewer

| Responsibilities | 
| -------- | 
| Reproduce the Vulnerability for Themselves     |
| Review and Provide Inputs to Mitigation/Remediation Plans     |
| Review Mitigation/Remediation Pull Requests     |


### Roles and Responsibilities: Remediation Verifier

| Responsibilities | 
| -------- | 
| Reproduce the Vulnerability for Themselves     |
| Review and Provide Input to Mitigation/Remediation Plans     |
| Perform Testing to Verify Remediation Efficacy     |

## Extreme Situation Options 
 
 > [!Caution]
 > These are extremely rare and hard to manage situations. If the [SecurityWG] finds itself facing any of these, it should seek help from the OpenJS Security Collab Space so an experienced security practitioner can be available to advise decision making.

### When to Consider a Short-Term Mitigation 

The use of short-term mitigations is rare. In practice the [SecurityWG] should only consider publishing a short-term mitigation in one of the following situations:

- Already public and likely to be weaponized
- There is evidence of active exploitation
- High risk of *immenant* active exploitation due to disclosure of a proven exploit

AND ONLY when both of these are true:

- Patch development will take an inappropriate amount of time for the risk
- The mitigation's effort and effects are reasonably worth the cost to implement when compared to the risk of waiting for a patch


### When to Publicly Disclose Before a Fix is Ready

The [SecurityWG] should only consider disclosing an unpatched vulnerability if there is:

- Evidence of current active exploitation
- Evidence of *imminent* active exploitation AND patch development will take an inappropriate amount of time for the risk

# 11. [T2] Coordinator Notifies the Reporter of Tier 2 Triage Decision

As soon as the [SecurityWG] decides to fix the Reported vulnerability, the Coordinator should:

- Inform the Reporter and manage their expectations on next steps
- Transition the Security Advisory state from `Triage` to `Draft`

> [!TIP]
> If you decide to proactively share your Mitigation/Remediation Plan(s) with the Reporter for feedback, the runbook separates Reporter comms into two events:
> 
> - Update 1: Tier 2 Triage Complete + Mitigation/Remediation In Progress
> - Update 2: Mitigation/Remediation Plan(s) Complete + Feedback Request
> 
> This is due to an assumption that that a clean write-up of the Plan(s) that is ready for external feedback *should not be rushed* and also should not block informing the Reporter that you've finished Tier 2 Triage and are working on a fix.
>
> Be aware that the Update 1 templates are written assuming you're *not* asking the Reporter for feedback on your Plan(s) in case you want to tweak wording a bit.

### 11a. If the Vulnerability Meets the Security Escalation Criteria

Use the [Tier 2 Triage Complete: Security Escalation Template] and customize it to the situation. If you're developing a Short-Term Mitigation Plan be sure to let them know in your update.

1. Enter your response in the Comment box and click ***Comment***.
2. Transition the Security Advisory from `Triage` to `Draft` by clicking ***Accept and Open as Draft***

### 11b. If the Vulnerability is Routine

Use the [Tier 2 Triage Complete: Routine Template]. Customize your response if you wish to add a personal touch.

1. Enter your response in the Comment box and click ***Comment***.
2. Transition the Security Advisory from `Triage` to `Draft` by clicking ***Accept and Open as Draft***

![Screenshot](https://docs.github.com/assets/cb-83825/mw-1440/images/help/security/advisory-maintainer-options.webp)

> [!NOTE]
> The Tier 2 Triage Phase is now complete and you transition to the Remediation Developering Phase! Congrats! \ o /

# 12. [FIX] Remediation Developer(s) Gather Information and Validate Tier 2 Triage

During this Step it is the Remediation Developer(s) responsibility to:

- Gather any additional information needed to draft the Plan(s)
- Validate Tier 2 Triage Deliverables

## 12a. (OPTIONAL) Gather Additional Information

The additional information previously identified as needed to develop the Mitigation/Remediation Plans may change the consensus understanding of the vulnerability. The Remediation Developer(s) should update the Tier 2 Triage deliverables to reflect the new information they've learned.

## 12b. Validate Tier 2 Triage Consensus

Before beginning to work on the draft Mitigation and Remediation Plans, the Remediation Developer(s) should validate the Tier 2 Triage deliverables used to establish a consensus understanding of the vulnerability.

### Validate Reproduction Steps

If the Remediation Developer(s) was not the Triage Analyst and hasn't done so already, they should begin validation by testing the Reporter and Triage Analyst's Reproduction Steps.

### Validate True Root Cause(s)

- Root cause(s) and the pull requests that introduced the vulnerability
- List of vulnerable products and versions

### Validate Impact and Exploitability

- **Attack scenario(s):** What would a real world attack using this vulnerability look like? Be sure to include the target conditions needed for success.
- **Impact:** When successfully exploited, what are the direct and indirect impacts?

If necessary, the Remediation Developer(s) and Coordinators should also update:

- The Security Advisory/CVE Description
- CVSSv3 Base Score

> [!TIP]
> This information gathering and validation Step may cause a meaningful change to the consensus understanding of the vulnerability. If so, the Remediation Developer(s) and Coordinator may decide that another [SecurityWG] consensus meeting is appropriate before they draft the Mitigation and Remediation Plans.

# 13. [FIX] Remediation Developer(s) Draft Mitigation/Remediation Plans

During this Step, it is the Remediation Developer(s) responsibility to to draft the complete Mitigation and Remediation Plans.

The Mitigation and Remediation Plans should be explicitly traced from the Mitigation and Remediation Options discussed at the end of Tier 2 Triage.

- Proposed non-breaking code changes and how they resolve each root cause
- Proposed breaking code changes and how they resolve each root cause 
- Proposed unit tests that verify the efficacy of code changes
- Proposed interactive tests to verify real world patch efficacy 
- Proposed changes to product documentation
- High confidence estimated completion date for patch development
- High confidence estimated time for patch testing
- High confidence proposed patch release date
- The patch release version number(s)

> [!TIP]
> Under normal circumstances, once the remediation patch is complete you should budget a week for the Reporter to verify its efficacy and completeness.

### Remediation Reviewer and Verifier Involvement

The Remediation Reviewer(s) and Fix Approver(s) should be generally aware of and monitoring progress and providing inputs asynchronously to minimize the need for extensive feedback and consensus building once the draft Plans are complete.

> [!NOTE]
> Steps 12 and 13 assume that Projects have their own established norms on how to document and come to decision on proposed fixes and breaking changes to resolve software defects.

# 14. [FIX] Coordinator Facilitates Feedback and Consensus on Draft Mitigation/Remediation Plans



Once the draft Mitigation and Remediation Plans are complete, the Coordinator should facilitate feedback and consensus on the proposed plan.

While there should be consensus on the entirity of both Plans, special attention should be focused on ensuring there is agreement on:

- The necessity of proposed breaking changes
- The quality and completeness of the testing methodology
- The liklihood of meeting of proposed development timelines

# 15. [FIX] Remediation Developer(s) Tentatively Complete and Verify Remediation with Support from Reviewer(s) and Verifiers(s)

In this Step, responsibilities are:

- **Remediation Developer:** Follow the Remediation Plan to complete development and Update the Plan as new information is learned during development
- **Remediation Reviewer:**
    - Support the Remediation Developer as needed during development, particularly if new information is learned that changes the Plan
    - Execute the Test Plan
- **Remediation Verifier:** Execute the Test Plan

> [!IMPORTANT]
> When testing a remediation patch, it's possible the Reporter will identify additional attack vectors they didn't think of when originally performing their research. Before the [SecurityWG] considers a remediation patch complete and ready for release, be sure to ensure that the Reporter agrees that they're unlikely to find workarounds.

# 16. [RELEASE] Coordinator Prepares the Security Advisory for Publication

In this Step, the Coordinator, with Remediation Developer support, is responsible for:

- 16a. Preparing the Security Advisory 
- 16b. Requesting a CVE ID from GitHub's CNA

## 16a. Preparing the Security Advisory

### Relevant JSON Schemas

GitHub Private Vulnerability Reporting (PVR) can publish GitHub Security Advisories (GHSAs) to two locations:

- [GitHub's Advisory Database](https://github.com/advisories), which is used by ***npm audit*** and ***dependabot***.
- [MITRE's CVE List](https://www.cve.org/) by the [GitHub M CNA](https://www.cve.org/PartnerInformation/ListofPartners/partner/GitHub_M)

GHSAs are stored in [OpenSSF's Open Source Vulnerability (OSV) JSON Schema](https://ossf.github.io/osv-schema/) developed by Google as part of their [osv.dev](https://osv.dev/) open source vulnerability database. 

When publishing a CVE, GitHub PVR converts OSV to [MITRE's CVE JSON Schema](https://github.com/CVEProject/cve-schema/blob/main/schema/docs/CVE_Record_Format_bundled.json).

### Security Advisory Metadata

#### CVSS Scoring Recommendations

- **Version:** CVSS v3.1 is used by PVR's CVSS calculator and remains the most commonly used and understood.
- **Calculator:** [First.org's CVSS v3.1 Calculator](https://nvd.nist.gov/vuln-metrics/cvss/v3-calculator) displays more information, which makes it easier to determine an initial CVSS score.

#### Weakness (CWE) Recommendations

The MITRE Common Weakness Enumeration framework categorizes the root cause software defects of security vulnerabilities. It can be challenging to identify the most appropriate CWE and selecting more than one CWE is recommended when appropriate. The best ways to search the CWE List are:

- CWE Quick Access Search on the [CWE front page](https://cwe.mitre.org/index.html).
- Directly searching Google for "mitre cwe [a description of your vulnerability]"

> [!TIP]
> GHSA's CWE tool only searches CWE titles and is not recommended.

#### Ecosystem

GHSA determines how to structure a security advisory in OSV using the `ecosystem` field. Failing to select `npm` will lead to incorrect processing by security tools.

#### Affected Versions

See [GitHub's Private Vulnerability Reporting documentation](https://docs.github.com/en/code-security/security-advisories/guidance-on-reporting-and-writing-information-about-vulnerabilities/best-practices-for-writing-repository-security-advisories#affected-versions) for guidance on how to best capture vulnerable versions in a format for use by downstream security tools.

#### Giving Credit

See [GitHub's Private Vulnerability Reporting documentation](https://docs.github.com/en/code-security/security-advisories/working-with-repository-security-advisories/creating-a-repository-security-advisory#about-credits-for-repository-security-advisories) for role definitions.

> [!TIP]
> GHSA automatically gives *Reporter* credit to the account that submited the Report. If they also discovered the vulnerability, be sure to correctly credit them as *Finder*.

## Security Advisory Details

### Title Recommendations

PVR's `Title` field is stored in the [OSV](https://ossf.github.io/osv-schema/) `Summary` field and the [CVE](https://github.com/CVEProject/cve-schema/blob/main/schema/docs/CVE_Record_Format_bundled.json) `Title` field. For best display in security write a brief but unique title as follows without Markdown formatting:

     [PRODUCT] [PROBLEM] in [FEATURE/FUNCTION]

### Description Recommendations

#### CVE JSON Generation

PVR's `Description` field is stored in the [OSV](https://ossf.github.io/osv-schema/) `details` field in Markdown. The [CVE](https://github.com/CVEProject/cve-schema/blob/main/schema/docs/CVE_Record_Format_bundled.json) `descriptions` field does not support Markdown and [CVE.org](https://www.cve.org) and other security tools display `descriptions` as a single paragraph without Markdown formatting.

When publishing a CVE, PVR does not use `details` verbatim when populating the `descriptions` field and results can be unpredictable. Because of how PVR generates this field, use PVR's default template to ensure the best results.

> [!NOTE]
> GitHub's CNA manually reviews CVEs and appears to edit `description` as needed. If you do a good job following PVR's default template your results should be predictable!

##### When using PVR's Default Template

     ### Impact
     ### Patches
     ### Workarounds
     ### References

When using this template, PVR will generate a string that concatinates the following elements:

1. A single sentence description of the repository (whose source is unclear)
2. The text (but not tables) found after *Impact*, *Patches*, and *Workarounds*

#### When NOT using PVR's Default Template 

PVR will populate `descriptions` by generating a string with unpredictable results that may include concatinating the following elements:

1. A single sentence description of the repository (whose source is unclear)
2. The text of `details` found between the first Markdown header (if present) and the next Markdown header or a URL, including any Markdown found in this text.
3. A single sentence listing all remediated version(s)

> [!TIP]
> Markdown links found in these sections will be displayed raw by [CVE.org](https://www.cve.org).

## 16b. Request a CVE ID from GitHub's CNA

Once this information is prepared and approved by [SecurityWG], the Coordinator can request a CVE ID. Requesting this ID will not publish the security advisory.

While not necessary, it's a good practice to have a CVD ID ready to share with the Reporter when asking them to review the remediation patch.

![Screenshot](https://docs.github.com/assets/cb-55619/mw-1440/images/help/security/security-advisory-request-cve-button.webp)

> [!NOTE]
> GitHub's CNA officially takes up to three days to review CVE Requests, so this should be done before the planned disclosure/release date.


# 17. [RELEASE] Coordinator Updates Reporter to Validate Remediation and Coordinate Public Disclosure

In this Step, the Coordinator, with Remediation Developer support, is responsible for:

- 17a: Requesting Reporter feedback on the Security Advisory 
- 17b: Ensuring the Reporter agrees that remediation is complete
- 17c: Reviewing the Reporter's blog post for accuracy

## 17a. Request Feedback on the Security Advisory

When reviewing the draft Security Advisory, the Reporter may ask for additional information to better understand the Remediation Plan. The situation and Reporter themselves will determine the appropriate amount information from the Remediation Plan to share. This can be an important education moment for the Reporter if they:

- Do not appear to have a software engineering background
- Made assertions that later proved erronenous or incomplete

The [Fix Complete: Researcher Verification Template] also asks the Reporter to share the GitHub Profiles of others who contributed to the vulnerability so they also have the opportunity to review and recieve credit.

## 17b. Request Reporter Verification of Implementation Efficacy and Completeness

With remediation internally verified and tentatively complete, it's now possible to ask the Reporter to provide feedback on the patch. During this Step, the Reporter should:

- Verify the efficacy of the remediation patch thus far
- Agree that remediation is complete and that additional methods of attack that should be remediated before the Patch is released are unlikely to be found

When using the [Fix Complete: Researcher Verification Template], be sure to customize your response to the situation and audience, and especially any specific test verification requests you may have.

## 17c. Ask to Review or Provide a Statement for their Blog

The [Fix Complete: Researcher Verification Template] also asks the Reporter if they are planning on publishing a blog post and to share it so it can be reviewed for technical accuracy. As an alternative, it also asks if you can provide statement they can include.

This is a sensitive and potentially contentious request and the Reporter may decline to provide it in advance of publication. If given this opportunity, treat it with respect and be mindful to avoid overstepping the boundaries of the request.

- DO use the technical documention previously generated that identified and discussed flaws in the original Report to professionally suggest changes
- DO NOT comment on or attempt to change on any personal opinions about the vulnerability or your Project
- DO NOT provide spelling or grammar suggestions

> [!TIP]
> It's not uncommon for Reporters to be slow or not respond to remediation verification and disclosure coordination requests. The template takes this possibility into account and gives the Reporter a week to perform verification.
> 
> If having this response from the Reporter is important, it's recommended to only follow-up with them after three days.

# 18. [RELEASE] Remediation Developer(s) Release the Patch While Coordinator Publishes Security Advisory

On the planned disclosure/release date, the Coordinator and Remediation Developer(s) are responsible for:

- Releasing the remediation patch
- Publishing the Security Advisory
- Updating the website (as needed)
- Updating product documentation (as needed)

> [!Warning]
> GitHub manually reviews security advisories before they are published, so it may take some time for this to happen after clicking Publish Advisory. If you've requested a CVE for the advisory will likely be published quickly as it was already manually reviewed during that request.

![Screenshot](https://docs.github.com/assets/cb-56518/mw-1440/images/help/security/publish-advisory-button.webp)
