# CVD Step-by-Step Runbook Guide Checklist TEMPLATE

## How to use this Checklist

This checklist is meant to be used in conjunction with:

* [CVD Step-by-Step Runbook Guide for Teams](./CVD-Step-by-Step-Runbook-and-Guide.md)
* [Researcher Communications Templates](./Researcher-Communications.Primer.md)

This checklist uses GitHub's Tasklist feature for when used as a template for a GitHub issue. You can use this template to provide visibility into which Step the Report is currently in and stay aware of the upcoming Steps.

>[!TIP]
>In several Steps (eg: 2, 5, 11), you'll only use one of the available sub-Steps. Be sure to remove the other sub-steps to shorten the length of the checklist and only see which steps were followed!

## Phase 0: Report Submission

- [ ] **1. The Reporter submits a potential security concern or vulnerability**
    - [ ] 1a. Optional: Reporter creates a temporary private fork (if they want to)

## Phase 1: Tier 1 Triage

- [ ] **2. On Call Performs Tier 1 Triage and Drafts an Initial Acknowledgement**
    - [ ] 2a. Security Escalation
    - [ ] 2b. Need More Information?
    - [ ] 2c. Not a Security Vulnerability Report?
    - [ ] 2d. Abuse Escalation
    - [ ] 2e. Routine Security Vulnerability Report
- [ ] **3. On Call Begins Organizing Internal Discussion by Creating a Tracking Discussion for the Vulnerability**
- [ ] **4. On Call Drafts a Tier 1 Summary**
- [ ] **5. On Call Sends the Reporter an Initial Acknowledgement of Receipt**
    - [ ] 5a. If the Report meets Security Escalation Criteria
    - [ ] 5b. If the Report Appears to be Missing Basic Information
    - [ ] 5c. If the Report Appears to be a Valid and Routine
    - [ ] 5d. If the Report is not a Security Vulnerability

## Phase 2: Tier 2 Triage

- [ ] **6. Assign Tier 2 Triage Roles**
- [ ] **7. Triage Analyst Attempts to Reproduce the Vulnerability as Reported**
- [ ] **8. Coordinator Notifies Reporter of Reproduction Progress**
    - [ ] 8a. First Notification: Unable to Reproduce / NMI
    - [ ] 8b. Second/Ongoing Comms: Still Unable to Reproduce
    - [ ] 8c. Notification: Successful Reproduction
- [ ] **9. Triage Analyst Performs Tier 2 Triage**
    - [ ] 9a. Identify and Document True Root Cause(s)
    - [ ] 9b. Assess and Document Impact and Exploitability
    - [ ] 9c. Document Initial Mitigation/Remediation Options
- [ ] **10. Coordinator Facilitates Consensus Building Discussions**
    - [ ] 10a. Reach Technical Consensus on Tier 2 Triage
    - [ ] 10b. Agree to Completely Remediate the Vulnerability 
    - [ ] 10c. Assign Remediation Roles and Agree on Mitigation/Remediation Next Steps
- [ ] **11. Coordinator Notifies the Reporter of Tier 2 Triage Decision**
    - [ ] 11a. If the Vulnerability Meets the Security Escalation Criteria
    - [ ] 11b. If the Vulnerability is Routine

## Phase 3: Fix Development

- [ ] **12. Remediation Developer(s) Gather Information and Validate Tier 2 Triage**
    - [ ] 12a. (OPTIONAL) Gather Additional Information
    - [ ] 12b. Validate Tier 2 Triage Consensus
    - [ ] **13. Remediation Developer(s) Draft Mitigation/Remediation Plans**
    - [ ] **14. Coordinator Facilitates Feedback and Consensus on Draft Mitigation/Remediation Plans**
    - [ ] **15. Remediation Developer(s) Tentatively Complete and Verify Remediation with Support from Reviewer(s) and Verifiers(s)**

## Phase 4: Release

- [ ] **16. Coordinator Prepares the Security Advisory for Publication**
    - [ ] 16a. Preparing the Security Advisory
    - [ ] 16b. Request a CVE ID from GitHub's CNA
- [ ] **17. Coordinator Updates Reporter to Validate Remediation and Coordinate Public Disclosure**
    - [ ] 17a. Request Feedback on the Security Advisory
    - [ ] 17b. Request Reporter Verification of Implementation Efficacy and Completeness
    - [ ] 17c. Ask to Review or Provide a Statement for their Blog
- [ ] **18. Remediation Developer(s) Release the Patch While Coordinator Publishes Security Adviso**ry