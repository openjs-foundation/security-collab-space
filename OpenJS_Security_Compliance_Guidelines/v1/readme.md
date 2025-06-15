# The OpenJS Foundation Security Compliance Guide v1.0 DRAFT<a id="the-openjs-foundation-security-compliance-guide-v10-draft"></a>

[OpenJS Security Compliance Standard v1.0](https://docs.google.com/spreadsheets/d/1GwIsAudAn89xv9DAbr1HUaY4KEVBsYfg--_1cW0uIB0/edit#gid=0)


## Executive Summary<a id="executive-summary"></a>

### Background<a id="background"></a>

Since 2020, the number of actively exploited security vulnerabilities in open source software (OSS) has significantly increased, along with attacks on core software supply chain infrastructure and individual community members. Awareness of the heightened threat environment has led to substantial responses from software consumers and regulators.

- The United States, European Union, and other nation states are actively funding efforts to build the modern institutional functions needed to regulate the software supply chains and inclusion of OSS in software they procure.

* Commercial software vendors have responded to regulator and customer awareness of their Software Supply Chain Security risks and ubiquitous use of OSS by increasingly funding and formalizing internal DevOps, Cybersecurity Supply Chain Risk Management (C-SCRM), and Open Source Program Office (OSPO) initiatives.

- A new generation of Application Security startups have raised VC funding to support these emerging initiatives. With the promise of regulator-induced demand Software Supply Chain Security, Software Bill of Materials (SBOM), and OSPO products achieved the same Peak status as Generative AI in the 2023 Gartner Hype Cycle.

* Large commercial consumers of OSS, and more recently governments, have funded new and existing non-profit infrastructure to support defining best practices, tool development, and selectively engaging with maintainers to improve the security posture of their projects. Newer software supply chain security startups are sometimes engaged in these non-profit activities by open sourcing and integrating parts of their tool chains.


### Observations<a id="observations"></a>

#### Community Outreach Efforts<a id="community-outreach-efforts"></a>

The OSS community’s response to these trends and the expectations thrust upon them by their newfound criticality in national security and for-profit business risk assessments have varied.

Observations and research strongly signal that a majority of maintainers have an accurate understanding of their threat environment, desire to proactively protect themselves, and value external support and guidance that tangibly improves their security posture. However, they are generally allergic to dedicating personal time implementing security controls that appear to satisfy low impact checkbox compliance rules without a locally relevant attack chain (“security theater”) or the risk management interests of commercial OSS consumers.

- [Congratulations: We Now Have Opinions on Your Open Source Contributions](https://lucumr.pocoo.org/2022/7/9/congratulations/)

- [OpenSSF Maintainer Experiences Lessons Learned](https://github.com/ossf/tac/issues/169)

- [Atlantic Council Research on Paying Maintainers](https://dfrlab.org/2024/04/18/more-money-better-security/)


#### Prior Art<a id="prior-art"></a>

There exist countless cybersecurity and software security best practices, maturity models, and standards for commercial software developers. Most of these are intended for internal use and assume facilitation by dedicated security practitioners in full time equivalent roles. Others are intended to provide their customers a standard way of measuring security program completeness and efficacy via a 3rd party audit.

There are few equivalents designed for OSS maintainers today. Those that exist often combine OSS project health, legal compliance, and technical security concepts together into a single score or maturity model for community and industry audiences. This choice fills a very real market need, but is not without controversy and appears at times to distract from the important work of implementing and celebrating incremental security posture improvements.

Sources for Guidelines include:

- [CNCF Cloud Native Security Whitepaper](https://github.com/cncf/tag-security/blob/main/security-whitepaper/v2/cloud-native-security-whitepaper.md)

- [CNCF Software Supply Chain Best Practices](https://github.com/cncf/tag-security/blob/main/supply-chain-security/supply-chain-security-paper/sscsp.md)

- [OpenSSF Best Practices Badge](https://www.bestpractices.dev/en/criteria)

- [OpenSSF Scorecard](https://github.com/ossf/scorecard/blob/main/docs/checks.md)

- [OpenSSF Source Code Management Best Practices](https://best.openssf.org/SCM-BestPractices)

- [OWASP SCVS](https://scvs.owasp.org/scvs/)

- Various npm and GitHub documentation


### Approach<a id="approach"></a>

Informed by these insights, this Standard is designed to serve as an achievable minimum security baseline for OpenJS Foundation Project maintainers. More plainly said, this is intended to be used as an easily digested and actioned security checklist.

In the spirit of allyship, this approach above all seeks to respect group and individual maintainer’s limited resources by focusing their time on the most impactful security controls and activities that enable them to:

- Protect their projects from threat actors, and

- Produce software that is safe to use in the modern threat environment.

This Standard makes heavy use of the plethora of prior art available to commercial software makers and OSS. References to OpenSSF, CNCF, and OWASP resources are found throughout and an in-depth analysis ([Standards and Best Practices Analysis](https://docs.google.com/spreadsheets/d/17PSYPGfOwVVVdjl2zTWbB8xT2PyLSv-EvqpHRuXnHo8/edit#gid=0)) to align their best practices and guidance are the basis of this Standard.


## Scope <a id="scope"></a>

**Tooling**

In its initial iteration, this Standard focuses on the common case of OpenJS software tooling. This means it is currently focused on GitHub and npm configuration best practices. As this Standard is iterated upon, additional tools are likely to be added.

**Relation to Best Practices Guides**

In other contexts, OpenJS provides best practice guidance for JavaScript OSS projects based on OpenSSF Best Practices Badge and OpenSSF Scorecard. This Standard is more narrowly focused on the work needed to secure OpenJS projects. Thus it does not include:

- OSS project health concepts without a demonstrable security impact

Multiple open source and proprietary OSS project health measurement systems exist and use various security and non-security signals to provide singular or multi-faceted health scores. These systems are used by OSS consumers when auditing their existing OSS dependencies and when choosing new ones. The security signals typically used by these systems can be grouped into three categories: Vulnerability Management, Intentional Insider Threat, and Unintentional Insider Threat. These groups are discussed further in Assumptions.

- Security architecture and feature hardening best practices

This Standard does not address secure design and defense-in-depth feature hardening concepts. In their most useful form, these best practices are specific to the frameworks used. Examples include [Node.js' Security Best Practices](https://nodejs.org/en/learn/getting-started/security-best-practices) and [Electron's Security Best Practices](https://www.electronjs.org/docs/latest/tutorial/security).


## How to Use the Standard<a id="how-to-use-the-standard"></a>

The Standard is organized around three concepts:

- Categories that organize the different types of Guidelines by security domain:

1. User Authentication

2. User Account Permissions

3. Service Authentication

4. Github Workflows

5. Vulnerability Management

6. Coordinated Vulnerability Disclosure

7. Code Quality

8. Code Review

9. Source Control

10. Dependency Inventory

11. Dependency Management

- Priority Groups that break up the 72 Guidelines into 22 smaller, sequenced chunks of work. Maintainers can use the Priority Groups to prioritize, sequence, and establish milestones to communicate and celebrate incremental security successes.

* Applicability of the Guideline based on the Project’s Status in OpenJS’ Project Lifecycle:

- Incubating Projects

  - For use as part of their processes  to mature and maintain their security posture to graduate into an Active Project.

- Active Projects (eg: At Large and Impact)

  - For use as part of their own processes to mature and maintain their security posture.

- Retiring Projects (eg: Emeritus Projects)

  - For use when winding down and ending support for an Active Project in order to establish a durable, long-term baseline security posture.

These Project types represent very different phases of an OSS project’s lifecycle, including their process maturity and available resources. To acknowledge these potentially enormous variances, for each Project type and Item, the Standard offers four different types of Guidance:

- Deferrable

  - This Guidance is only to be used with Incubating Projects seeking graduation and Active Projects seeking Retirement.

  - This is used on Items whose effort is potentially high enough where it may require longer-term roadmapping due to competing priorities and/or resourcing and should not block the Graduation or Retirement of an OpenJS Project.

- Expected

  - This Guidance views the Item as achievable by the vast majority of OpenJS Projects and that a decision to not pursue it comes with a reasonable long-term technical or short-term resource justification.

- Recommended

  - This Guidance is reserved for Items that are industry and regulator-expected best practices that are not reasonably achievable by most JavaScript OSS projects due to the resourcing needed.

  - These resourcing challenges include:

    - Monetary costs

    - Number of trusted maintainers

    - Low real-world security impact

- Not Applicable (N/A)

  - This Guidance is reserved for Items that are no longer relevant for Projects once they are formally Retired.
