# Priority Group 9

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: |
| GHW:DTRO | Github Org Default Workflow Token Permissions are Set to Read Only | E | E | NA |
| GHW:WPR | Workflows are not Allowed To Create or Approve Pull Requests | E | E | E |
| SC:PFP | Prevent Force Push on Default Branch | E | E | E |
| SC:PBD | Prevent Default Branch Deletion | E | E | E |
| SC:UTD | Default Branch must be Up to Date before Merging | E | E | E |


### Github Org Default Workflow Token Permissions are Set to Read Only

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| GHW:DTRO |4. Github Workflow Permissions | Expected | Expected | N/A |

* **MITRE References**
    * [CWE-250](https://cwe.mitre.org/data/definitions/250.html)
    * [CAPEC-69](https://capec.mitre.org/data/definitions/69.html)

---

### Workflows are not Allowed To Create or Approve Pull Requests

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| GHW:WPR | 4. Github Workflow Permissions | Expected | Expected | Expected |

* **MITRE References**
    * [CWE-250](https://cwe.mitre.org/data/definitions/250.html)
    * [CAPEC-69](https://capec.mitre.org/data/definitions/69.html)
* **Sources**
    * [OpenSSF Scorecard](https://github.com/ossf/scorecard/blob/main/docs/checks.md#token-permissions)
    * [OpenSSF SCM Best Practices](https://best.openssf.org/SCM-BestPractices/github/repository/actions_can_approve_pull_requests.html)
* **HOW TO**
    * [GitHub Docs](https://docs.github.com/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-policies-for-github-actions-in-your-enterprise#preventing-github-actions-from-creating-or-approving-pull-requests) 

---

### Prevent Force Push on Default Branch

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| SC:PFP | 9. Source Control | Expected | Expected | Expected |

* **Sources**
    * [OpenSSF Scorecard](https://github.com/ossf/scorecard/blob/main/docs/checks.md#branch-protection)
    * [OpenSSF SCM Best Practices](https://best.openssf.org/SCM-BestPractices/github/repository/missing_default_branch_protection_force_push.html)
* **HOW TO**
    * [GitHub Docs](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches) 

---

### Prevent Default Branch Deletion

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| SC:PBD | 9. Source Control | Expected | Expected | Expected |

* **MITRE References**
    * [CWE-267](https://cwe.mitre.org/data/definitions/267.html)
* **Sources**
    * [OpenSSF Scorecard](https://github.com/ossf/scorecard/blob/main/docs/checks.md#branch-protection)
    * [OpenSSF SCM Best Practices](https://best.openssf.org/SCM-BestPractices/github/repository/missing_default_branch_protection_deletion.html)
* **HOW TO**
    * [GitHub Docs](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches) 

---

### Default Branch must be Up to Date before Merging

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| SC:UTD | 9. Source Control | Expected | Expected | Expected |

* **Sources**
    * [OpenSSF Scorecard](https://github.com/ossf/scorecard/blob/main/docs/checks.md#branch-protection)
    * [OpenSSF SCM Best Practices](https://best.openssf.org/SCM-BestPractices/github/repository/requires_branches_up_to_date_before_merge.html)
* **HOW TO**
    * [GitHub Docs](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches#require-status-checks-before-merging) 