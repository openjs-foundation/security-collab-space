# Incident Response Plan

## Purpose  
This document outlines the process for handling security incidents affecting any OpenJS project. Incidents may include platform changes with security implications, account compromise, or other security events that require coordinated response.

The Foundation’s role is to:  
1. **Receive and triage the Incident Reports**  
2. **Connect reporters and affected maintainers with the right experts**  
3. **Facilitate coordinated response** across multiple projects when needed  
4. **Communicate clearly and act as the contact point** while respecting confidentiality and responsible disclosure principles  

---

## Scope  

This plan covers incidents such as:  
- **Platform changes or providers outages** (e.g., GitHub UI change) that create security or operational risk.  
- **Account or registry access issues** (e.g., npm lockdown, compromised maintainer account).  
- **Supply chain attacks** (e.g. XZ, phishing campaign, etc.. )  
- **Third-party service compromises** affecting Foundation projects (e.g., data leaks in external services)  
- **Legal-related operational threats**, including:
  - License disputes (e.g., GPL/MIT compliance challenges)
  - Patent-related threats impacting project distribution
  - DMCA takedown requests
  - Trademark misuse or brand impersonation


Incidents that are not in scope:
- **Code-level security vulnerabilities** in projects maintained within the Foundation (handled by the project or the OpenJS CNA Team)
- **Non-Foundation projects** — see the [list of supported projects](https://openjsf.org/projects)  

---

### Incident Categories  

- 🍿 @Discussion: Probably we can think on more scenarios together 


| Category | Examples | Primary Response Role |
|----------|----------|-----------------------|
| **Vulnerability Report** | Code exploit, CVE disputes, escalations... | Redirect to the project or delegate to the CNA Team |
| **Platform Change Risk** | GitHub UI update causing accidental info exposure | Triage → Escalate to platform contacts → Provide mitigations |
| **Account Access Issue** | npm account lockout, GitHub MFA issues | Triage → Help restore access via platform → Provide temporary mitigation |
| **Supply Chain Attack** | Malicious dependency version | Coordinate with affected projects → Security advisories |
| **External Incident Impact** | Cloud provider compromise, service outage | Facilitate communication between impacted maintainers and providers |

---


## Action plan  

We may not directly solve incidents, but we help **unblock situations** and **support projects at risk**.

### Roles & Responsibilities


#### RACI Diagram

_You can find more information about RACI in this [link](https://www.atlassian.com/work-management/project-management/raci-chart)_


| Process Step                          | Reporter | Response Team (Foundation) | Coordinator (SRC) | SME |
|---------------------------------------|----------|-----------------------------|-------------------|-----|
| File Report                       | R, A     | C                           | I                 |     |
| Assign Coordinator                | I        | R                           | A                 |     |
| Assess Impact & Severity          | I        | C                           | A                 | C   |
| Identify & assign SMEs            | I        | C                           | A                 | C   |
| Make a resolution / recommend mitigation | I  | C                           | A                 | C   |
| Document findings                 | I        | C                           | A                 | I, C   |
| Publish and share (if approved)   | I        | R, A                        | C                 | C   |

- 🍿 @Discussion: who should be in the team? 
- 🍿 @Discussion: Should we publish the learning/findings when possible publickly to help the community?

#### Reporter

This person submits an Incident Report to the Foundation Security Team and provides detailed information about the incident.

**Responsibilities**

- Submit an Incident Report to the Foundation Security Team.

**Expectations**

- Provide detailed information about the suspected vulnerability.
- Follow responsible disclosure guidelines (adapted to this context).
- Cooperate with the Foundation Security Team by providing additional details when needed.
- Respect security timelines and avoid premature public disclosure.



#### Coordinator (SRC)

This person acts as the focal point for a specific Incident Report and ensures the report follows all responsible disclosure guidelines. The SRC coordinates the remediation process if the situation is confirmed and ensures that the Incident Report follows the process and necessary actions are taken. While the SRC is not necessarily responsible for performing a detailed analysis or remediation.

**Responsibilities**

- Acknowledge receipt of Incident Reports within the required timeframe.
- Orchestrate the embargo and identify the minimum set of individuals involved.
- Remind everyone involved that they must not notify/involve any other individuals. If someone else needs to be involved, that must go through the Coordinator.
- Assign one or multiple SMEs.
- Ensure communication with the reporter and the affected projects throughout the process.
- Track all the Incident Reports for visibility and reporting.

#### Subject Matter Expert (SME)
Experts brought in for technical insight, platform liaison work, or domain-specific advice.  

**Responsibilities**:  
- Provide expert input to help assess impact and options  
- Advise on mitigation strategies  
- Help unblock the situations when feasible

### Reporting method


In [this webform](https://report-incident.openjsf.org/) is possible to create a new security report


## Runbook

- 🍿 @Discussion: What is the best approach? Some ideas:
    1. **Incident Report Received**  
    2. **Assign Coordinator** and consolidate report details  
    3. **Review** severity and affected projects  
    4. **Identify SMEs** and brief them  
    5. **Coordinate** with projects, platforms, or third parties  
    6. **Document** findings and lessons learned  
    7. **Publish** partial or full summary if appropriate  
    8. **Social Media Team** prepare and posts where needed 

## General Response Workflow  

- 🍿 @Discussion: early-stage idea, based on the Runbook:

```mermaid
flowchart TD
    A[Incident Report Received] --> B[Assign Coordinator]
    B --> C{Is valid, qualified and can be verified?}
    C -- No --> D[Request Clarification from Reporter]
    D --> C
    C -- Yes --> E[Assess Impact and Severity]
    E --> F{Single Project or Multi-Project?}
    F -- Single --> G[Engage Project Maintainers]
    F -- Multi --> H[Engage Multiple Maintainers + Foundation Network]
    G --> I[Coordinate Response: Bring SMEs...]
    H --> I
    I --> J[Update Reporter and Stakeholders]
    J --> K[Document and Close Incident]


