# Recommendation Group 2

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: |
| GHW:LCF | Limit changes from forks to workflows by requiring approval for all outside collaborators | R | R | R |
| GHW:UWSS | Use a Workflow Security Scanner | R | R | R |
| GHW:URSS | Use a Github Runner Security Scanner | R | R | R |

### Limit changes from forks to workflows by requiring approval for all outside collaborators

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| GHW:LCF | 4. Github Workflows | Recommended | Recommended | Recommended |

* **MITRE References**
    * [CAPEC-180](https://capec.mitre.org/data/definitions/180.html)
* **HOW TO**
    * [GitHub Docs](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository#controlling-changes-from-forks-to-workflows-in-public-repositories) 

---

### Use a Workflow Security Scanner

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| GHW:UWSS | 4. Github Workflows | Recommended | Recommended | Recommended |

* **MITRE References**
    * [M1047](https://attack.mitre.org/mitigations/M1047/)
* **Sources**
    * [OpenSSF Scorecard](https://github.com/ossf/scorecard/blob/main/docs/checks.md#token-permissions)
    * [OpenSSF SCM Best Practices](https://best.openssf.org/SCM-BestPractices/github/repository/token_default_permissions_is_read_write.html)
* **HOW TO**
    * [Step Security secure-repo](https://github.com/step-security/secure-repo) 

---

### Use a Github Runner Security Scanner

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| GHW:URSS | 4. Github Workflows | Recommended | Recommended | Recommended |

* **MITRE References**
    * [M1047](https://attack.mitre.org/mitigations/M1047/)
* **Sources**
    * [Github Action Hardening Docs](https://docs.github.com/en/actions/security-guides/security-hardening-for-github-actions#hardening-for-self-hosted-runners)
* **HOW TO**
    * [Step Security harden-runner](https://github.com/step-security/harden-runner) 