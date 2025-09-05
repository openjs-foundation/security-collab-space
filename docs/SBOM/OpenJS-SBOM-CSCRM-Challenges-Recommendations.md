# JavaScript SBOM and Software Attestation Challenges and Recommendations

### **Purpose**

This document captures observations and lessons learned on the challenges to achieve broad adoption by the JavaScript and Node.js ecosystems of Software Bill of Materials (SBOM) and Software Attestation (including Provenance) Cybersecurity Supply Chain Risk Management (C-SCRM) capabilities.

Based on these observations and lessons learned, we include recommendations for maintainers, policy makers, and GitHub/npm.

## **Executive Summary**
### **Background**

Since 2020, the number of actively exploited security vulnerabilities in open source software (OSS) has significantly increased, along with attacks on core software supply chain infrastructure and individual community members. Awareness of the heightened threat environment has led to substantial responses from regulators and software consumers, including: 

* EU mandates via the recently adopted [Cyber Resilience Act](https://www.europarl.europa.eu/doceo/document/TA-9-2024-0130_EN.pdf).
* US mandate related to [SBOMs](https://www.cisa.gov/sbom) supply chain security in [EO 14028](https://www.whitehouse.gov/briefing-room/presidential-actions/2021/05/12/executive-order-on-improving-the-nations-cybersecurity/) implemented via [OMB M-23-16](https://www.whitehouse.gov/wp-content/uploads/2023/06/M-23-16-Update-to-M-22-18-Enhancing-Software-Security-1.pdf) and CISA’s [Secure Software Development Self Attestation Form](https://www.cisa.gov/sites/default/files/2024-04/Self_Attestation_Common_Form_FINAL_508c.pdf).

In particular, these two technologies have been promoted by policy makers and open source software consumers and advocates to address these challenges:

* **SBOMs**: provide an inventory of components included in a software product in an ecosystem-neutral format  
* **Software Provenance Attestation**: a trusted and verifiable claim of where a software component, artifact or product came from

### **Conclusions and Recommendations**

While well intended, when assessing the real world security impact these technologies provide and the level of effort they demand of open source software Maintainers to implement, it’s clear these technologies are still in their infancy.

The OpenJS Foundation supports the intent of the regulatory regime governments are seeking to build. However, broad adoption of these technologies by volunteer, part-time maintainers in many cases is hard to justify. Based on our analysis, we recommend that:

* **SBOMs in the Node.js ecosystem**
    * Should only be generated for end-user facing JavaScript applications and never for individual Javascript libraries that do not provide functionality for end users. This is due to npm’s dependency resolution algorithm, which produces dependency trees for isolated libraries that should not be expected to represent the dependencies of that library when resolved in the context of a JavaScript application. Thus, only JavaScript applications should generate SBOMs.  
* **npm Package Provenance**
    * I not recommended for JavaScript libraries and applications as currently implemented as it does not provide the real world security value that many assume it does. We’ve recommended several substantial improvements to npm and GitHub to resolve these gaps so that the sometimes substantial effort needed to implement package provenance can be justified.

Below is a detailed analysis of the relevant features and real world scenarios that explain how we came to these conclusions. We look forward to hearing feedback and engaging with open source advocates, regulators, and GitHub on our recommendations so that we can help make the Internet a safer place.

# **Software Bill of Materials (SBOM)**
### **SBOM Definition and Purpose**

According to the U.S. Cybersecurity and Infrastructure Security Agency’s (CISA) [*SBOMs at a Glance*](https://www.ntia.gov/sites/default/files/publications/sbom_at_a_glance_apr2021_0.pdf), SBOMs are:

>*“A formal, machine-readable inventory of software components and dependencies, information about those components, and their hierarchical relationships. These inventories should be comprehensive – or should explicitly state where they could not be.”* 

CISA further identifies several business compliance and security benefits of SBOMs, including software supply chain transparency, software license management, and vulnerability management. In the event of a publicly known vulnerability/cyber attack, CISA views SBOMs as a key asset for incident responders:

> *“When flaws or vulnerabilities are discovered in a given component, SBOMs are used to quickly identify software that is affected by the vulnerable component, to assess its usage, and to understand the risk introduced by the vulnerable component. The ability to identify vulnerabilities allows software suppliers to produce patches or provide other remediation options, allows consumers to apply mitigations independently of the software supplier, and allows the identification of software that is not affected.”*

## **Challenges for SBOMs in the npm Ecosystem**

The U.S. Government’s objectives for SBOMs are laudable and valid. In many ecosystems, most notably those of compiled languages, SBOMs provide software producers and operators necessary transparency into software composition.

However, in the context of the npm ecosystem, there are a number of challenges and risks to the mass use of SBOMs that should give JavaScript library package maintainers and consumers pause before publishing or utilizing them.

* The ecosystem’s large number of average transitive dependencies make it impractical to expect package maintainers to manually deprecate or update abandoned or vulnerable dependencies  
* npm’s dependency resolution methodology produces SBOMs for isolated libraries that should be expected to accurately reflect that library’s dependency versions when resolved in the context of any given application  
* npm natively produces comprehensive component manifests that account for its non-idempotent dependency version resolution methodology

These challenges are not necessarily true or as relevant to complete JavaScript applications.

### **Large numbers of smaller transitive dependencies**
---

The npm Package Registry is the largest software ecosystem registry on the Internet. One of the reasons for this is that, unlike other language ecosystems, JavaScript packages often have a large number of small transitive dependencies. Packages in npm average over 300 transitive dependencies, while the next closest (Ruby) averages less than 100\.

![image1]  
*Source: [Veracode](https://www.veracode.com/blog/research/look-vulnerabilities-and-dependencies-language)*

This introduces a number of challenges for software producers wishing to publish and leverage SBOMs. According to Anchore’s [*Open Source is Bigger than you can Imagine*](https://anchore.com/blog/open-source-is-bigger-than-you-imagine/), most npm packages have one maintainer. Managing hundreds of dependencies is a challenging and time consuming task for professional software engineering organizations, much less a solo or small group of volunteer maintainers.

* Generating a “quality” SBOM that meets the [NTIA’s Minimum Elements for an SBOM](https://www.ntia.doc.gov/files/ntia/publications/sbom_minimum_elements_report.pdf) relies on metadata provided by a proportionally huge population of likely solo package maintainers.  
* Large and deep dependency trees that may have multiple instances of the same package make it practically impossible for maintainers to deprecate or update vulnerable dependencies without risking unpredictable behaviors and bugs due to hard-to-test for incompatibilities.

### **Non-idempotent dependency resolution**
---

According to research from Google’s Open Source Insights Team, transitive dependency version resolution in npm is non-idempotent when resolving different sets of dependencies in libraries or applications.

Unlike JavaScript applications, for any given JavaScript library package (“A”) in isolation its transitive dependencies:

* Are likely to be idempotent within a small time window  
* Are less likely to be idempotent over an extended time window

In the context of a JavaScript application with other dependencies that may have shared transitive dependencies, if library *A*’s dependencies were resolved at the same time as library *A* in isolation, npm’s dependency resolver should be expected to produce an entirely different sets of transitive dependency versions for library *A*.

![][image2]  
*Source: [Google](https://blog.deps.dev/zillions-of-sboms/)*

This means that:

* Isolated library package SBOMs should never be expected to accurately represent the dependency tree of that library when it’s used in an application.  
* The dependency tree of library packages should be expected to widely differ between the applications they’re used in.  
* It appears to be potentially dangerous to publish SBOMs for isolated library packages outside of their application as their inaccuracy may lead to data pollution of authoritative sources ingesting SBOM data for vulnerability alerting.  
* Only SBOMs for standalone JavaScript applications contain accurate and actionable dependency information.  
* SBOMs for standalone JavaScript applications may change considerably between releases, depending on feature velocity of the application itself and the feature velocity of direct and transitive dependencies.

## SBOM Conclusion and Recommendations

The use case for npm-sbom is considerably different for JavaScript library packages and complete JavaScript application packages. Many of the challenges above are specific to when SBOMs are generated for JavaScript library packages in isolation and not part of a JavaScript application.

### **Recommendations for JavaScript library packages**
---

1. **Library Maintainers:** Individual library packages that **DO NOT** include compiled language tools (eg: CLI tools), binaries or containers should not publish SBOMs.  
   * These SBOMs should not be expected to accurately represent the library’s dependencies when used with other direct dependencies in an application.  
   * These SBOMs are likely to pollute services that consume them with erroneous data.  
2. **Library Maintainers:** Individual library packages that **DO** include compiled language tools, binaries (eg: CLI tools) or container images should publish SBOMs for those artifacts but not publish an SBOM for JavaScript library itself.  
   * While compiled language SBOMs are out of scope for this document, they are a critical transparency tool and help avoid the need to perform after-the-fact binary analysis.  
   * These SBOMs are necessary and consumed by Application Developers when generating their own comprehensive SBOM(s).  
   * If there’s a question of prioritization, compiled language tools expected to be installed by end user customers should generally be prioritized before developer-only tools.  
3. **Software Supply Chain Monitoring Services:** When consuming SBOMs to determine the potential scope of vulnerabilities across products, they **SHOULD NOT** consume individual JavaScript library package SBOMs as this is expected to produce mostly false positives.  
4. **Software Supply Chain Monitoring Services:** When consuming SBOMs to determine the potential scope of vulnerabilities across products, they **SHOULD** consume SBOMs for compiled language tools, binaries, and containers published by JavaScript libraries.  
5. **Open Source Advocates and Regulators:** SBOM guidance they generate should be clarified to explicitly exclude individual JavaScript libraries.  
6. **npm**: Include a note in the npm-sbom command documentation to reflect this guidance for library packages.

### **Recommendations for JavaScript Applications**
---

7. **Application Maintainers:** JavaScript Applications **SHOULD** publish SBOMs for their application, that also **INCLUDE** SBOMs for compiled code tools, binaries, and containers.  
   * The challenges related to library SBOM accuracy do not apply to application SBOMs.  
   * Despite the presence of ecosystem native  package-lock.json and npm-shrinkwrap.json manifest files this information is more easily consumed by end users in an cross-ecosystem standard format.   
8. **Software Supply Chain Monitoring Services:** When consuming SBOMs to determine the potential scope of vulnerabilities across products, these services should limit their intake to exclusively consuming JavaScript Application SBOMs.

# **Attestation and Package Provenance**



### **Attestation Definition**


According to OpenSSF’s [SLSA Project](https://slsa.dev/attestation-model), software attestation is “*an authenticated statement (metadata) about a software artifact or collection of software artifacts.*”

Software attestation comes in many forms, including:

* Application Code Signing (eg: [Apple](https://developer.apple.com/documentation/security/code-signing-services), [Google](https://developer.android.com/studio/publish/app-signing), [Microsoft](https://learn.microsoft.com/en-us/windows/security/application-security/application-control/app-control-for-business/deployment/use-code-signing-for-better-control-and-protection))  
* Attestations of Containers and their SBOMs (eg: [Open Container Initiative](https://opencontainers.org/community/certified/))  
* Package Provenance (eg: [npm](https://github.blog/security/supply-chain-security/introducing-npm-package-provenance/), [pypi](https://github.com/trailofbits/pypi-attestations))

### **Package Provenance Definition and Purpose**

In the npm CLI and package registry, package provenance comes in the form of software attestation that provides package consumers proof that a given package was:

1. Published from the source repository it claims to be from  
2. Using a specific build file executed on a GitHub hosted runner

In GitHub’s [announcement](https://github.blog/security/supply-chain-security/introducing-npm-package-provenance/) their stated objective was to establish a root of trust for npm packages by:

* Providing a direct line from the registry package to the source repository and commit it was published from  
* Providing visibility into the build process and runner that generated the published package

GitHub’s announcement referenced three attacks that they are seeking to prevent with package provenance: [malware in ua-parser-js](https://github.com/advisories/GHSA-pjwm-rvh2-c87w), [malware in coa](https://github.com/advisories/GHSA-73qr-pfmq-6rp8), [malware in rc](https://github.com/advisories/GHSA-g2q5-5433-rhrf). These attacks were all accomplished by malicious actors who:

1. [ATT\&CK T1586.003](https://attack.mitre.org/techniques/T1586/003/): Compromised a maintainer’s npm account through undisclosed means  
2. [CAPEC-538](https://capec.mitre.org/data/definitions/538.html): Added malware to the package and published the now malicious package to npm as an updated version of the legitimate package

## **Challenges to Adopting Package Provenance**

This report discusses npm’s built-in package provenance functionality while using GitHub, including:

* Gaps in the real world and perceived security value of npm/GitHub’s current implementation  
* The effort maintainers must make to support package provenance which challenge adoption  
* Recommendations based on these gaps and challenges

### **Effort to implement package provenance**
---

To publish a package with provenance on GitHub, a maintainer must transition from publishing locally, as is common for most Node.js and OpenJS projects, to publishing using an automated [GitHub Action](https://github.com/features/actions).

To do this properly, for each package a maintainer must:

* Generate an npm Granular Access Token that is:  
  * Scoped to the package in question  
  * Limits use of the token to the [CIDR blocks of GitHub Hosted Runners](https://api.github.com/meta)  
* Add the npm Access Token to the [GitHub](https://docs.github.com/en/actions/security-for-github-actions/security-guides/using-secrets-in-github-actions) repository, environment, or organization  
* Write a new and [securely configured GitHub Action](https://docs.github.com/en/actions/security-for-github-actions/security-guides/security-hardening-for-github-actions) for for any build activities currently being done by script to publish the package to npm with provenance

This transition is not always easily boilerplated or one-click and should be expected to require a rewrite of working build and publishing processes for each package. For part-time maintainers this means prioritizing a non-trivial amount of engineering effort for this transition over their feature roadmap. Many core-to-the-Internet packages are also maintained by a single maintainer who supports multiple packages, multiplying the time these individuals must dedicate to supporting package provenance.

As is common in the software development industry and through the outreach of OpenJS to its project maintainers, we’ve consistently observed the need to have very clear and strong real world security impact stories about the security improvements we propose to maintainers to get buy-in and help them to justify prioritizing security over feature roadmaps.

### **Gaps in package provenance challenge its security value**
---

To justify the effort of transitioning to publishing via GitHub Actions, npm package provenance should demonstrate strong, real world security value to maintainers and package consumers.

Unfortunately, this does not appear to be the case. Below is a review of the gaps that challenge the assumed value of package provenance, including:

* Lack of support for MFA prompts in GitHub Actions requires maintainers to use single factor access tokens and stop using credentials that support MFA  
* Use of GitHub Actions increases the attack surface for package hijacking by:  
  * Likely increasing the number users able to publish a given package  
  * Inserting other attack vectors, such as takeover of other GH Actions used during the build process  
* Requiring manual log analysis to validate that only code in the source repository is included in the published package  
* Short maximum and configurable log retention limits the timeframe for when this manual log analysis can happen  
* No built-in functionality to warn package consumers when the latest release of a package does not provide provenance contrary to past releases

### **npm Account and Token Management Gaps**
---

In the examples GitHub mentioned and in other package hijacking attacks, it’s rare for the impacted maintainer to publicly disclose which type of npm credentials were used or how they were compromised. Without any additional insight into these particular attacks, below is an overview of npm’s account types and a brief summary of potential credential compromise scenarios.

* #### **Background: Accounts and 2FA Configuration for Publishing**

npm has three types of credentials that can publish packages:

* **User Accounts** with optional support for 2FA  
* **Legacy Tokens** (no longer recommended):  
  * **Automation Tokens** with no support for 2FA  
  * **Publish Tokens** with optional support for 2FA  
* **Granular Access Tokens** for automation (recommended, [introduced in 2022](https://github.blog/changelog/2022-12-06-limit-scope-of-npm-tokens-with-the-new-granular-access-tokens/)):  
  * No support for 2FA  
  * Supports limiting users to specific source IPs and CIDR ranges

npm account publish access settings have three options:

![][image3]  
*Source: [npm](https://docs.npmjs.com/requiring-2fa-for-package-publishing-and-settings-modification)*

* #### **Background: Hypothetical methods of compromise**

Research consistently shows that about half of cyber attacks happen via account compromises that use valid credentials.

In the example account compromises GitHub mentions, if their Publishing access configuration was set to **Option 1** or **Option 2** there are a number of methodologies available to execute these attacks:

* [CAPEC-49](https://capec.mitre.org/data/definitions/49.html) (Password Brute Forcing and its child attacks)  
* [CAPEC-50](https://capec.mitre.org/data/definitions/50.html) (Password Recovery Exploitation)  
* [CAPEC-600](https://capec.mitre.org/data/definitions/600.html) (Credential Stuffing via Password Reuse)  
* [T1598](https://attack.mitre.org/techniques/T1598/) (Social Engineering)  
* [CWE-256](https://cwe.mitre.org/data/definitions/256.html) (Plain Text Storage of Credentials)

As use of MFA has increased, the number of attacks that bypass [MFA methods vulnerable to social engineering](https://www.cisa.gov/sites/default/files/publications/fact-sheet-implementing-phishing-resistant-mfa-508c.pdf) or device exploitation has also increased.

These attacks could also be possible with **Option 3** if the 2FA code generator for the npm account was:

* Installed on a rooted device, had [malware which captures 2FA codes](https://www.fortinet.com/blog/threat-research/fortinet-reverses-flutter-based-android-malware-fluhorse), or the device was compromised by another means  
* Used a 2FA method used is vulnerable to phishing, such as:  
  * Mobile push notifications (supported by GitHub)  
  * SMS (supported by GitHub)  
  * One-time Password (OTP) (supported by npm and GitHub)  
  * Token-based OTP (supported by npm and GitHub)

It’s worth noting that GitHub, in the context of GitHub Repositories, announced in 2023 a [mandate for all GitHub accounts to enable some form of MFA](https://github.blog/news-insights/product-news/raising-the-bar-for-software-security-github-2fa-begins-march-13/) and in 2024 have [published a report on their progress](https://github.blog/security/supply-chain-security/securing-millions-of-developers-through-2fa/#user-experience-and-support) towards achieving this mandate, with a particular emphasis on phishing-resistant MFA like FIDO/WebAuthn Passkeys.

### **GitHub Actions require publishing without 2FA**
---

* #### **GitHub Actions does not support CLI 2FA prompts** 

GitHub Actions do not have the ability to pause for an MFA prompt from a CLI tool. There are free third party services with GitHub Actions that provide this functionality such as the [wait-for-secrets GitHub Action](https://github.com/step-security/wait-for-secrets) by [StepSecurity](https://www.stepsecurity.io) and [Wombat Dressing Room](https://github.com/GoogleCloudPlatform/wombat-dressing-room) by [GCP](https://opensource.googleblog.com/2020/01/wombat-dressing-room-npm-publication_10.html). Unfortunately, in this model the maintainer must provide their npm credentials to a third party server.

* #### **Publishing via GH Action removes isolation between npm and GitHub accounts** 

Maintainers who publish locally are able to configure their separate npm and GitHub accounts with [phishing-resistant MFA](https://www.cisa.gov/sites/default/files/publications/fact-sheet-implementing-phishing-resistant-mfa-508c.pdf). To control a maintainer’s npm package and GitHub source repository, an attacker must compromise these two isolated accounts. This isolation allowed the hijacked package maintainers mentioned earlier to quickly recover once the attack was discovered.

When publishing using a GitHub Action, maintainers must use single factor Granular Access Tokens stored in GitHub. This elevates the threat to GitHub accounts and increases the risk of account compromise. In this model, an attacker must only compromise the maintainer’s GitHub account to gain control of a maintainer’s source repository and npm package.

In the event a maintainer’s GitHub account is compromised, the attacker could still insert malware and publish the malicious package with provenance ([CAPEC-206](https://capec.mitre.org/data/definitions/206.html)).

* #### **Storing credentials in GitHub likely increases the number of users able to publish**

Maintainers who publish locally are able to separately control who has permission to perform routine actions in the source repository (such as approving pull requests) and who has permission to publish the package.

This is not possible when publishing using GH Actions. GitHub’s repository permission model provides the [Write role](https://docs.github.com/en/enterprise-cloud@latest/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/repository-roles-for-an-organization#permissions-for-each-role), which has permission to accept pull requests, view secrets, and run GitHub Actions. This effectively increases the number of users and attack surface for publishing packages to npm. Buying an [Enterprise Cloud GitHub](https://docs.github.com/en/enterprise-cloud@latest/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/managing-custom-repository-roles-for-an-organization) license is required to configure a custom role and resolve this gap.

## **Gaps in Real World Security Value**

* #### **Package Provence links the published package to a repository, but not the source code**

When the GH Action publishes the package with provenance, it is easy to incorrectly assume that the code from the source repository is what was included in the package tarball.

This is an incorrect and dangerous assumption.

npm Package Provenance only signs and captures the artifacts of the build process to allow for manual analysis by package consumers so they can attempt to validate that the source code in the repository was included in the package. One must manually analyze the build log, the publishing GH Action’s workflow, and the workflows of all other GH Actions included in the publishing GH Action’s workflow to ensure that no other code was added to the GitHub runner before the package was published to npm.

* #### **Three month log retention limits time to verify the build process**


The build logs that npm’s package provenance references that provides consumers transparency into what happened during the build are only retained by GitHub for three months. An example of what the logs look like after this short retention window has been met can be observed in the package GitHub referenced in their announcement: [sigstore-js](https://github.com/sigstore/sigstore-js/actions/runs/9116405766/job/25064948815).

It could be argued that this information is most valuable for the short period after a package is published when a malicious package is most likely to be detected. This also does not eliminate the theoretical benefit of having assurance that a package was published from the repository it claims it did.

This significantly challenges the real world security value of package provenance compared to other potential security improvements a part-time maintainer could prioritize instead.

* #### **Unclear signals for consumers when a package stops publishing with provenance**

Imagine a npm package has routinely published with provenance for the past year. If an npm account or Access Token is compromised and a malicious actor publishes a malicious package update without provenance, what happens?

Today, npm does not automatically notify those package consumers in a way that may give them pause. For package consumers to detect this event and investigate, they would need to write their own GH Action to use npm audit and track each of their dependencies that were previously published with provenance and identify whether the latest version of a package stopped providing provenance.

What conclusion should a package consumer come to when this happens? Did the maintainer make a mistake? Is it an indicator of compromise? Are they just not doing package provenance anymore?

The unfortunate real world impact of this means that connection intended to provide an ongoing root of trust between the published package and source repository is unlikely to actually be used except when choosing a new package. This makes it very challenging to justify the transition effort with package maintainers over other more impactful security improvements. 

## **npm Package Provenance Conclusion and Recommendations**


In its current state, npm’s package provenance functionality does not appear to provide sufficient real world security value to justify the potentially substantial effort required to implement it.

For this reason, the OpenJS Foundation’s Security Collab Space removed all initially proposed provenance related entries from its v1 Security Compliance Guidelines for OpenJS projects. We recommend that OpenJS projects focus their security improvement efforts on higher impact guidelines.

There is much potential in the concept of provenance attestation and we hope engineering continues to improve on the foundation that has been built. To this end, we recommend npm and GitHub implement the following functionality:

| Context | Recommendation |
| :---: | :---- |
| **GitHub** | 1\. Native support for MFA prompts in GitHub Actions |
| **GitHub** | 2\. Ability for maintainers to indefinitely retain GH Action logs of the most recent package publication run |
| **GitHub** | 3\. A separate permission system or a new repository role so that allows maintainers can limit who has access to secrets and the ability to run GH Actions |
| **npm** | 4\. A configurable canary that allows package maintainers to choose whether the absence of package provenance should be a signal of potential compromise to downstream developers |
| **npm** | 5\. A configurable option to require a confirmation email to complete publication of a new package version |
| **Both** | 6\. A two-tier system for npm and GitHub organization member 2FA requirement configuration: Require phishing-resistant two-factor authentication Require two-factor authentication Disable SMS |

# Appendix

### Native Dependency Manifests in npm

Independent of SBOMs, npm can generate three different manifest files, each with their own purposes. One file \-  package-lock.json \- is the closest equivalent to an SBOM and can optionally be used exclusively by the npm sbom command to generate a properly formatted SBOM.

* #### **package-lock.json**

In the npm ecosystem, the closest equivalent to a SBOM is the package-lock.json file. This file contains an exact description of the JavaScript package’s fully resolved hierarchical package dependency tree as found in the node\_modules folder. It is automatically generated when npm performs an action that adds, updates, or removes a dependent package (ie: when node\_modules is modified).

It is not possible to publish the  package-lock.json to the npm Registry in its standard file location and it is not used by npm when package consumers resolve that package’s dependencies. It is typically stored in the source repository and serves as a reference of a given local environment’s hierarchical package dependency tree.

* #### **npm-shrinkwrap.json**

This file’s syntax and contents are identical to package-lock.json but it is able to be published to the npm Registry. However, it is rarely used and only published to the npm Registry when the package maintainer wishes to prescriptively enforce their package dependency tree on downstream users. npm-shrinkwrap.json files, though rarely used, are most typically found in freestanding JavaScript application packages rather than library packages.

* #### **package.json**

This is the metadata file that describes the package in the npm Registry. Among several other things, the package.json file contains the package’s authoritative list of direct package dependencies and the file paths and metadata for any binary dependencies included in the package.

Since the package.json dependency list only contains direct package dependencies, the remainder of the dependency tree in node\_modules is dynamically resolved by npm upon installation and non-deterministic. If present,  npm-shrinkwrap.json will be used instead and replicate the package dependency tree prescribed by the maintainer.

### **SBOM Tooling for npm**

The npm sbom command generates a SBOM describing the package and its dependencies in either [CycloneDX](https://cyclonedx.org/specification/overview/) or [SPDX](https://spdx.dev/learn/overview/) format. Maintainers have the choice of generating an SBOM based on the observed contents of the node\_modules folder (default) or only based on the contents of the package-lock.json file.

[image1]: https://github.com/user-attachments/assets/0ae907d3-b2e5-47ca-a28c-f57605957567
[image2]: https://github.com/user-attachments/assets/c9bd9d1d-37ed-41de-9a24-585466d1b037
[image3]: https://github.com/user-attachments/assets/1e78569e-5946-4806-bf17-45cb4b305ab6
