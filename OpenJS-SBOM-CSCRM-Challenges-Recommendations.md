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

[image1]: <data:image/png;base64,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>

[image2]: <data:image/png;base64,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>

[image3]: <data:image/png;base64,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>