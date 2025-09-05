# Priority Group 2

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: | 
| SA:NSSC | No Secrets and Credentials in Source Code | E | E | E |
| SA:GHS | Secrets are injected at runtime, such as environment variables or as a file (eg: use Github Secrets) | E | E | E |
| CQ:CSS | All Commits are Scanned for Secrets and Credentials  | E | E | NA |
| CQ:CWSB | New Commits Containing Secrets or Credentials are Blocked from Merging | E | E | NA |

### No Secrets and Credentials in Source Code

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| SA:NSSC | 3. Service Authentication | Expected | Expected | Expected |

* **MITRE References**
    * [CWE-540](https://cwe.mitre.org/data/definitions/540.html)
    * [M1032](https://attack.mitre.org/mitigations/M1032/)
* **Sources**
    * [OpenSSF Best Practices Badge Passing Level [no_leaked_credentials]](https://www.bestpractices.dev/en/criteria#0.no_leaked_credentials)
* **HOW TO**
    * [GitHub Docs](https://docs.github.com/en/code-security/secret-scanning/about-secret-scanning) 

---

###  Secrets are injected at runtime, such as environment variables or as a file (eg: use Github Secrets)

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| SA:GHS | 3. Service Authentication | Expected | Expected | Expected |

* **MITRE References**
    * [CWE-538](https://cwe.mitre.org/data/definitions/538.html)
* **Sources**
    * [CNCF CNSWP 2.0](https://github.com/cncf/tag-security/blob/main/security-whitepaper/v2/cloud-native-security-whitepaper.md#secrets-encryption)
* **HOW TO**
    * [GitHub Docs](https://docs.github.com/en/actions/security-guides/using-secrets-in-github-actions#creating-secrets-for-an-organization) 

---

###  All Commits are Scanned for Secrets and Credentials

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| CQ:CSS | 7. Code Quality | Expected | Expected | Not Applicable |

* **MITRE References**
    * [CWE-540](https://cwe.mitre.org/data/definitions/540.html)
    * [CAPEC-150](https://capec.mitre.org/data/definitions/150.html)
* **Sources**
    * [CNCF SSCP v1.0](https://github.com/cncf/tag-security/blob/main/supply-chain-security/supply-chain-security-paper/sscsp.md#user-content-fnref-21-4e56305414bd02da4843ec1d7d856144)
* **HOW TO**
    * [GitHub Docs](https://docs.github.com/en/code-security/secret-scanning/about-secret-scanning) 

---

###  New Commits Containing Secrets or Credentials are Blocked from Merging

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| CQ:CWSB | 7. Code Quality | Expected | Expected | Not Applicable |

* **MITRE References**
    * [CWE-358](https://cwe.mitre.org/data/definitions/358.html)
* **Sources**
    * [OpenSSF Best Practices Badge Passing Level [no_leaked_credentials]](https://www.bestpractices.dev/en/criteria#0.no_leaked_credentials)
* **HOW TO**
    * [GitHub Docs](https://docs.github.com/en/code-security/secret-scanning/about-secret-scanning) 
