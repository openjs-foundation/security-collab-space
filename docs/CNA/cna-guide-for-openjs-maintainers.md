# OpenJS CNA Guide for OpenJS Maintainers

### Table of Contents
- [Key Information](#key-information)
- [Help responding to a vulnerability report](#help-responding-to-a-vulnerability-report)
- [Help improving your Vulnerability Disclosure Program](#help-improving-your-vulnerability-disclosure-program)

## 1. Key Information

* [CNA Scope and Disclosure Policy](https://security.openjsf.org)  
* [Published Security Advisories](https://security.openjsf.org/security-advisories.html)  
* [cve.org: OpenJS CNA](https://www.cve.org/PartnerInformation/ListofPartners/partner/openjs)  
* [cve.org: Red Hat Open Source Root CNA](https://www.cve.org/PartnerInformation/ListofPartners/partner/redhat)

### How to Contact the CNA

| Email | [security@openjsf.org](mailto:security@openjsf.org) |
| :---- | :---- |
| OpenJS Slack | \#security in [openjs-foundation.slack.com](https://openjs-foundation.slack.com/) |
| OpenJS Security Collab Space Weekly Meeting | [8:30am PT most Mondays](https://calendar.openjsf.org) *(except US holidays)* |

### OpenJS Security Collab Space CNA Coordinators

| Name | OpenJS Slack | GitHub | Role | Time Zone |
| ----- | ----- | ----- | ----- | :---: |
| Adam ‘rudd’ Ruddermann | @rudd | @ruddermann | Primary CNA Coordinator | [America/Los_Angeles](https://www.timeanddate.com/time/zone/usa/los-angeles) |
| Chris de Almeida | @Chris de Almeida  | @ctcpip | CNA Coordinator |[America/Chicago](https://www.timeanddate.com/time/zone/usa/chicago) |
| Ulises Gascon | @ulisesgascon | @ulisesgascon | CNA Coordinator | [Europe/Madrid](https://www.timeanddate.com/time/zone/spain/madrid) |
| Jordan Harband | @ljharb | @ljharb | CNA Coordinator | [America/Los_Angeles](https://www.timeanddate.com/time/zone/usa/los-angeles) |

# Help responding to a vulnerability report

**For support with a vulnerability report, please contact us at [security@openjsf.org](mailto:security@openjsf.org).**

We may take up to 24 hours to respond but typically will do so within a few hours. You can also reach us on the OpenJS Slack directly using the information above.

### **Get a CVE ID from the OpenJS CNA**

Be sure to provide the following information:

* Your OpenJS Slack handle(s)  
* How many CVEs you need  
* The estimated or confirmed date/time of public disclosure  
* How you would like to grant the CNA Coordinators access to your proposed CVE and information about the vulnerability to ensure CVE meets quality standards

### **Help writing a CVE entry and/or security advisory**

[Check out this guide to writing CVEs on MITRE’s cve.org\!](https://www.cve.org/Resources/Roles/Cnas/CVE_Record_Creation.pptx)

Be sure to provide the following information:

* Your OpenJS Slack handle(s)  
* The estimated or confirmed date/time of public disclosure  
* How severe you believe the issue is  
* How interactions with the security researcher(s) have been  
* How you would like to grant the CNA Coordinators access to the vulnerability report and any information or write-ups you’ve gathered

### **Help with a challenging vulnerability disclosure situation**

Be sure to provide the following information:

* A summary of the challenge(s) and outcome(s) you’re hoping to achieve  
* The plan and current progress towards releasing a fix or why you won’t be releasing a fix  
* If releasing a fix, the estimated or confirmed date/time you expect it to be released

### **A CVE has been published without your permission**

Despite your project being within the scope of the OpenJS CNA, there is a small chance that another CNA may erroneously publish a CVE about your project without coordinating with the OpenJS CNA. Here’s what to expect:

*If the vulnerability is VALID but the technical details of the CVE are erroneous or do not meet OpenJS or your standards, it can’t be retracted but it can be updated for accuracy and completeness.*

* OpenJS CNA will contact the publishing CNA and request changes to the content of the CVE.  
* If the original CVE requestor disagrees with the proposed changes, the CVE will be marked as DISPUTED and its contents potentially updated (depending on the circumstances).

*If the reported vulnerability is NOT VALID (eg: an unproven hypothetical, intended functionality, erroneous) and would not have received a CVE from the OpenJS CNA:*

* OpenJS CNA will contact the publishing CNA and will request that the CVE be retracted. However, there is a chance that they will not adhere to this request.  
* If the CNA refuses to retract the CVE, then OpenJS will request that the CVE be marked as DISPUTED and its contents potentially updated (depending on the circumstances).

# Help improving your Vulnerability Disclosure Program

Thanks to Alpha-Omega funding, the OpenJS Security Collab Space can directly support and implement these improvements to your project:

* Improve your create your Vulnerability Disclosure Policy  
* Transition to a specialized vulnerability disclosure tool (eg: GitHub Private Vulnerability Reporting)  
* Improve or create internal vulnerability disclosure and management processes

To get started, open an issue in the [Security Collab Space repo](https://github.com/openjs-foundation/security-collab-space) and provide the following information:

* What you would like support with  
* Past successes and challenges you’ve had security researchers  
* Link(s) to your current or draft policy if you have one  
* Your preferred timelines for when this work should happen  
* At least two proposed meeting times to answer questions and discuss next steps
