---
title: Priority Group 2

---

# Priority Group 3

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: | 
| UA:SSH | Use SSH keys for developer access to source code repositories and use a passphrase | E | E | E
| UA:MFN | Multi Factor Authentication (MFA) Enforced Across the npm Organization | E | E | E |
| SA:WHS | Github Webhooks Use Secrets | E | E | E |

### Use SSH keys for developer access to source code repositories and use a passphrase

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| UA:SSH | 1. User Authentication | Expected | Expected | Expected |

* **MITRE References**
    * [CWE-309](https://cwe.mitre.org/data/definitions/309.html)
    * [M1032](https://attack.mitre.org/mitigations/M1032/)
* **Sources**
    * [CNCF SSCP v1.0](https://github.com/cncf/tag-security/blob/main/supply-chain-security/supply-chain-security-paper/sscsp.md#use-ssh-keys-to-provide-developers-access-to-source-code-repositories)
* **HOW TO**
    * [GitHub Docs](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/about-ssh) 

---

### Publish to npm using an MFA-enabled account rather than single factor legacy or granular access tokens

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| SA:NPMP | 3. Service Authentication | Expected | Expected | Expected |

* **MITRE References**
    * [CWE-308](https://cwe.mitre.org/data/definitions/308.html)
* **HOW TO**
    * [npm Docs](https://docs.npmjs.com/creating-and-viewing-access-tokens)

---

### Github Webhooks Use Secrets

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| SA:WHS | 3. Service Authentication | Expected | Expected | Expected |

* **MITRE References**
    * [CWE-306](https://cwe.mitre.org/data/definitions/306)
    * [M1032](https://attack.mitre.org/mitigations/M1032/)
* **Sources**
    * [OpenSSF Scorecard](https://github.com/ossf/scorecard/blob/main/docs/checks.md#webhooks)
    * [OpenSSF SCM Best Practices](https://best.openssf.org/SCM-BestPractices/github/repository/repository_webhook_no_secret.html)
* **HOW TO**
    * [GitHub Docs](https://docs.github.com/en/actions/security-guides/using-secrets-in-github-actions)