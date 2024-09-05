# OpenJS Project Generic Minimal Coordinated Vulnerability  Disclosure (CVD) Policy (VDP) TEMPLATE

## Introduction

[project_name](https://) and [The OpenJS Foundation](https://openjsf.org/) are committed to a safe and secure Internet. We're thankful for and welcome ethical security research contributions to our project(s) and support good faith Coordinated Vulnerability Disclosure.

We accept and process all communications regarding potential security vulnerabilities and concerns using [GitHub's Private Security Reporting](https://github.blog/2023-04-19-private-vulnerability-reporting-now-generally-available/) feature.

> *OPTIONAL: For more information about the bugs we're looking for, check out our [Threat Model](https://)!*

> **[Click here to Submit a Security Vulnerability](https://github.com/your_org/your_repo/security/advisories/new)**

## Policy Scope

Assets in-scope for this policy:
- *`[org/project/repo]`* source code hosted on GitHub *`[link]`*.
- *(Optional: `[org/project/repo]` self-hosted development, testing, and CI/CD infrastructure.)*


This Policy does not grant you permission to perform testing or demonstrate the impact of a vulnerability on third party installations of *`[org/project/repo]`* that do not belong to you. It is your responsibility to determine the ownership of an asset or system, discover and adhere to their Vulnerability Disclosure Policy, and contact their recommended Point of Contact to resolve any needed clarifications before performing testing.

## Program Rules

### How to Communicate with Us

- **Acceptable Communications Channel:** We only accept and communicate about potential security concerns and vulnerabilities via a submission to our *`[your_vuln_disclosure_platform]`*. Please DO NOT open a public issue or contact team members via email, Slack, or social media.
- **Let us Know Immediately:** Once you believe you’ve discovered a potential security concern or vulnerability, immediately submit it to us with as much detail as possible so we may quickly begin our investigation.
- **Research Collaborators:** We gladly include all research collaborator(s) who the original submitter agrees should also be credited for the vulnerability during public disclosure.

> For more details, check out **[How to Submit a Vulnerability to Us](#How-to-Report-a-Vulnerability)** below.

### Public Disclosures

- **Time to Disclosure:** When submitting a security concern or vulnerability to us, you agree to not publicly disclose the fact of or any details related to your vulnerability any earlier than ninety (90) days from the day it was submitted.
- **Embargo:** During this time, do not share or disclose the fact of or any information about your security concern or vulnerability with anyone before first coordinating with us. If the 90 day embargo is unusually restrictive for reasons beyond your control (eg: a Call for Papers deadline) let us know and we’ll be happy to collaborate on a solution.

> For more details, check out **[What to Expect after Submitting a Vulnerability](#How-to-Report-a-Vulnerability)** below.

### Expected Behaviors

- Adhere to our *`[contributor_guidelines]`* and do not modify or remove data for the purposes of security testing.
- Do not test or demonstrate a CI/CD vulnerability in *`[org/project/repo_name]`* repositories. If you do this, we will submit a [Content Report](https://docs.github.com/en/communities/maintaining-your-safety-on-github/reporting-abuse-or-spam#reporting-an-issue-or-pull-request) to GitHub.
- Adhere to [GitHub's Acceptable Use Policies](https://docs.github.com/en/site-policy/acceptable-use-policies) and all applicable laws and regulations.


### Security Advisory and CVE Policy

*`[org/project/repo_name]`* is within the scope of The OpenJS Foundation CNA. We issue GitHub Security Advisories and CVEs for valid, In Scope security vulnerabilities when the root cause and code change to implement the mitigation/remediation is in one of our repositories.

To provide high quality security signals to our downstream users/developers, we do not issue Advisories and CVEs when updating vulnerable third party dependencies unless there is demonstrable proof in the form of a Proof of Concept that the dependency’s vulnerability can be exploited within the context of *`[org/project/repo]`*.

### No Bounty Awards

- We are an open source project of [The OpenJS Foundation, a U.S. 501(c\)(6) non-profit organization](https://openjsf.org/governance) and unfortunately are unable to offer a bounty award for your discovery.


### Safe Harbor for Good Faith Security Research

When conducting security vulnerability research according to this Policy, we consider this research to be:

- Authorized concerning any applicable anti-hacking laws, and we will not initiate or support legal action against you for accidental, good-faith violations of this Policy;
- Authorized concerning any relevant anti-circumvention laws, and we will not bring a claim against you for circumvention of technology controls;
- Lawful, helpful to the overall security of the Internet, and conducted in good faith.

You are expected, as always, to comply with all applicable laws. If legal action is initiated by a third party against you and you have complied with this Policy, we will take steps to make it known that your actions were conducted in compliance with this Policy.

If at any time you have concerns or are uncertain whether your security research is consistent with this Policy, please submit a vulnerability report using *`[H1/Github/Other]`* before going further.

> Note that this Safe Harbor applies only to legal claims related to assets under our control and that this Policy does not bind independent third parties.


## Out of Scope Vulnerabilities



### Vulnerabilities in Third Party Dependencies

- Vulnerabilities in our direct and tertiary dependencies are considered Out of Scope unless once can demonstrate actual exploitation using *`[org/project/repo]`* functionality.
- Please report vulnerabilities in dependencies to their respective owners in accordance with their Vulnerability Disclosure Policies so that the true root cause can be properly mitigated or remediated.

In the case of an In Scope vulnerability that also relies on a previously unknown (0day) vulnerability in a third party dependency we will:
1. Ask for proof that you have disclosed the vulnerability per its Vulnerability Disclosure Policy, or
2. If you haven’t done that already, we will ask that you do so.

# How to Report a Vulnerability

Only submit potential security concerns or vulnerabilities to us using *`[your_disclosure_platform]`*. Attempts to send this via other channels (public ticket, email, Slack, social media) will be removed.

To best help us quickly understand and take action on your submission, be sure to include:

### **[Click here to Submit a Security Vulnerability](https://github.com/your_org/your_repo/security/advisories/new)**

> For more information about the bugs we're looking for, check out our [Threat Model](https://)!
> 
| Section | Information |
| -------- | -------- |
| **Brief Summary**     | A one or two sentence high-level summary of the vulnerability, including its impact.     |
| **Detailed Impact**     | A detailed description and impact of how it could be used in a real-world attack chain.   |
| **Reproduction Steps**     | Clearly written and detailed reproduction steps, including tools and environment configuration.   |
| **Location in Source** (if feasible)     | The precise location of the vulnerability in source code.   |
| **Proposed Fix** (if feasible)     | Source code for your proposed fix.   |
| **Proposed CVSSv3 Base Score**     | (Best Effort) [Link to NVD CVSSv3 Calculator](https://nvd.nist.gov/vuln-metrics/cvss/v3-calculator)   |
| **Proposed CWE and/or CAPEC**     | (Best Effort) [MITRE CWE](https://cwe.mitre.org/index.html) and [MITRE CAPEC](https://capec.mitre.org/index.html)   |
| **Collaborators**     | A list of all collaborators and their affiliation who should receive credit upon public disclosure.   |


# What to Expect Next After Submitting

### **[Click here to Submit a Security Vulnerability](https://github.com/your_org/your_repo/security/advisories/new)**

| Status | Events |
| -------- | -------- |
| Acknowledgement     | We will acknowledge receipt of your submission within *`[hours/days]`*.     |
| Triage     | We will attempt to reproduce your findings within *`[hours/days]`*. We may ask you for more information if your submission is unclear or missing data we need to understand and reproduce the behavior you observed.     |
| Acceptance     |  We will let you know when we have successfully reproduced your vulnerability and accepted it as a valid security vulnerability report. We will also share our initial assessment of your vulnerability's CWE and CVSSv3 Base Score, a reserved CVE ID, and what you can expect to happen next regarding mitigation/remediation.     |
| Ongoing Communications     | We will let you know how things are going periodically and when there is new information regarding our mitigation and/or remediation efforts.     |
| Mitigation and/or Remediation     | We endeavor to release patches for security vulnerabilities no later than ninety (90) days of receipt (with most released much earlier). However, if we ask for more time, we will explain the technical reasoning, including the unusual effort and complexity of patch development and downstream user/developer remediation actions.     |
| Coordinating Disclosure     | We will inform you once we know the release date and version of the mitigation and/or remediation. If you plan to publish a blog regarding your vulnerability, we would greatly appreciate the opportunity to review your post in advance for technical accuracy and so we can provide an official statement for you to include.     |
| Public Disclosure     | This is when the GitHub Advisory is published and the CVE is updated to reflect the Advisory. You may then publish your blog post and tell the world about your awesome hax0r skills.     |

#### Comments on this Policy

If you have suggestions on how this process could be improved please submit a pull request against [this version of the policy](https://) or the [OpenJS Template](https://) it's based on. 

