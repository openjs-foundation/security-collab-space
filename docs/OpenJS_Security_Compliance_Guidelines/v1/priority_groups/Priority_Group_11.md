# Priority Group 11

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: |
| GHW:CEAC | Build Pipeline Cannot Execute Arbitrary Code from Outside of a Build Script | E | E | NA |
| GHW:JLWP | Only Allow Workflows Write Permissions at the Job-Level | E | E | E |
| GHW:ASI | Avoid Script Injection from Untrusted Context Variables | E | E | NA |

### Build Pipeline Cannot Execute Arbitrary Code from Outside of a Build Script

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| GHW:CEAC | 4. Github Workflows | Expected | Expected | N/A |

* **MITRE References**
    * [CWE-94](https://cwe.mitre.org/data/definitions/94.html)
    * [CAPEC-19](https://capec.mitre.org/data/definitions/19.html)
* **Sources**
    * [OpenSSF SCM Scorecard](https://github.com/ossf/scorecard/blob/main/docs/checks.md#dangerous-workflow)

---

### Only Allow Workflows Write Permissions at the Job-Level

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| GHW:JLWP | 4. Github Workflows | Expected | Expected | Expected |

* **MITRE References**
    * [CWE-250](https://cwe.mitre.org/data/definitions/250.html)
    * [CAPEC-69](https://capec.mitre.org/data/definitions/69.html)
* **Sources**
    * [OpenSSF Scorecard](https://github.com/ossf/scorecard/blob/main/docs/checks.md#token-permissions)
    * [OpenSSF SCM Best Practices](https://best.openssf.org/SCM-BestPractices/github/repository/actions_can_approve_pull_requests.html)
* **HOW TO**
    * [GitHub Docs](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions#permissions) 

---

### Avoid Script Injection from Untrusted Context Variables

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| GHW:ASI | 4. Github Workflows | Expected | Expected | N/A |

* **MITRE References**
    * [CWE-454](https://cwe.mitre.org/data/definitions/454.html)
    * [CAPEC-242](https://capec.mitre.org/data/definitions/242.html)
* **Sources**
    * [OpenSSF Scorecard](https://github.com/ossf/scorecard/blob/main/docs/checks.md#dangerous-workflow)
* **HOW TO**
    * [GitHub Docs](https://securitylab.github.com/research/github-actions-untrusted-input/) 