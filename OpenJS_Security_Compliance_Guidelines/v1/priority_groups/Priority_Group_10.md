# Priority Group 10

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: |
| GHW:SRSR | GitHub Organization Secrets are Restricted to Selected Repositories | E | E | NA |
| GHW:ALTA | GitHub Actions Should Be Limited To Verified or Explicitly Trusted Actions | E | E | NA |
| GHW:SHR | Disable use of Self-Hosted Runners in GitHub Org | E | E | E |

### GitHub Organization Secrets are Restricted to Selected Repositories

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| GHW:SRSR | 4. Github Workflows | Expected | Expected | N/A |

* **MITRE References**
    * [CWE-250](https://cwe.mitre.org/data/definitions/250.html)
    * [CAPEC-69](https://capec.mitre.org/data/definitions/69.html)
* **Sources**
    * [OpenSSF SCM Best Practices](https://best.openssf.org/SCM-BestPractices/github/actions/all_repositories_can_run_github_actions.html)
* **HOW TO**
    * [GitHub Docs](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository#managing-github-actions-permissions-for-your-repository) 

---

### GitHub Actions Should be Limited To Verified or Explicityly Trusted Actions

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| GHW:ALTA| 4. Github Workflows | Expected | Expected | N/A |

* **MITRE References**
    * [CWE-1357](https://cwe.mitre.org/data/definitions/1357.html)
    * [CAPEC-17](https://capec.mitre.org/data/definitions/17.html)
    * [CAPEC-538](https://capec.mitre.org/data/definitions/538.html)
    * [CAPEC-446](https://capec.mitre.org/data/definitions/446.html)
* **Sources**
    * [OpenSSF SCM Best Practices](https://best.openssf.org/SCM-BestPractices/github/actions/all_github_actions_are_allowed.html)
* **HOW TO**
    * [GitHub Docs](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository#allowing-select-actions-and-reusable-workflows-to-run) 

---

### Disable use of Self-Hosted Runnders in GitHub Org

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| GHW:SHR | 4. Github Workflows | Expected | Expected | Expected |

* **MITRE References**
    * [CAPEC-439](https://capec.mitre.org/data/definitions/439.html)
* **Sources**
    * [Github Action Hardening Docs](https://docs.github.com/en/actions/security-guides/security-hardening-for-github-actions#hardening-for-self-hosted-runners)
* **HOW TO**
    * [GitHub Docs](https://docs.github.com/en/organizations/managing-organization-settings/disabling-or-limiting-github-actions-for-your-organization#limiting-the-use-of-self-hosted-runners) 