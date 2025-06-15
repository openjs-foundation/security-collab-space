# Recommendation Group 6

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: |
| CR:2PR | [For Projects with Two or more Maintainers] Require Two Party Review | R | R | NA |
| CR:COR | [For Projects with Four or more Maintainers] Require Code Owners Review | R | R | NA |
| SC:RAPR | [For Projects with Two or more Maintainers] Require Approved PRs for all commits to mainline branches | R | R | R |

### [For Projects with Two or more Maintainers] Require Two Party Review

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| CR:2PR | 8. Code Review | Recommended | Recommended | N/A |

* **MITRE References**
    * [CAPEC-670](https://capec.mitre.org/data/definitions/670.html)
    * [CAPEC-443](https://capec.mitre.org/data/definitions/443.html)
    * [CAPEC-438](https://capec.mitre.org/data/definitions/438.html)
* **Sources**
    * [OpenSSF Scorecard](https://github.com/ossf/scorecard/blob/main/docs/checks.md#code-review)
    * [OpenSSF Best Practices Badge Gold Level [two_person_review]](https://www.bestpractices.dev/en/criteria?details=true&rationale=true#2.two_person_review)
* **HOW TO**
    * [Github Docs](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches#require-pull-request-reviews-before-merging) 

---

### [For Projects with Four or more Maintainers] Require Code Owners Review

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| CR:COR | 8. Code Review | Recommended | Recommended | N/A |

* **MITRE References**
    * [CAPEC-670](https://capec.mitre.org/data/definitions/670.html)
    * [CAPEC-443](https://capec.mitre.org/data/definitions/443.html)
    * [CAPEC-438](https://capec.mitre.org/data/definitions/438.html)
* **Sources**
    * [OpenSSF Scorecard](https://github.com/ossf/scorecard/blob/main/docs/checks.md#code-review)
* **HOW TO**
    * [Github Docs](https://docs.github.com/en/code-security/secret-scanning/about-secret-scanning) 

---

### [For Projects with Two or more Maintainers] Require Approved PRs for all commits to mainline branches

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| SC:RAPR | 9. Source Control | Recommended | Recommended | Recommended |

* **MITRE References**
    * [CAPEC-670](https://capec.mitre.org/data/definitions/670.html)
    * [CAPEC-443](https://capec.mitre.org/data/definitions/443.html)
    * [CAPEC-438](https://capec.mitre.org/data/definitions/438.html)
* **Sources**
    * [OpenSSF Scorecard](https://github.com/ossf/scorecard/blob/main/docs/checks.md#branch-protection)
    * [CNCF SSCP v1.0](https://github.com/cncf/tag-security/blob/main/supply-chain-security/supply-chain-security-paper/sscsp.md#use-branch-protection-rules)
* **HOW TO**
    * [Github Docs](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches) 