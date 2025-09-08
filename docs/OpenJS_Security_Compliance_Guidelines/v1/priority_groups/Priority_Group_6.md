# Priority Group 6

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: |
| D:IDPV | An automated process to identify dependencies with publicly disclosed vulnerabilities | E | E | E |
| CQ:SAT | Use an Automated Static Code Analysis Tool (eg: ESLInt) | E | E | NA |
| CQ:LINT | Compilers/Linter Warnings Addressed in order to Merge | E | E | NA |
| CQ:SAST | All Commits are Scanned by a Static Application Security Testing Tool | E | E | NA |
| CQ:CSMP | All Required Commit Status Checks must pass before Merging | E | E | NA |

### An automated process to identify dependencies with publicly disclosed vulnerabilities

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| D:IDPV | 10. Dependencies | Expected | Expected | Expected |

* **MITRE References**
    * [CWE-1395](https://cwe.mitre.org/data/definitions/1395.html)
    * [M1016](https://attack.mitre.org/mitigations/M1016/)
* **Sources**
    * [OWASP SCVS L1 5.4](https://scvs.owasp.org/scvs/v5-component-analysis/)
    * [OpenSSF Scorecard](https://github.com/ossf/scorecard/blob/main/docs/checks.md#dependency-update-tool)
    * [OpenSSF Best Practices Badge Passing Level [dependency_monitoring]](https://www.bestpractices.dev/en/criteria?details=true&rationale=true#1.dependency_monitoring)
* **HOW TO**
    * [GitHub Docs](https://docs.github.com/en/code-security/dependabot/dependabot-security-updates/configuring-dependabot-security-updates#managing-dependabot-security-updates-for-your-repositories) 

---

### Use an Automated Static Code Analysis Tool (eg: ESLInt)

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| CQ:SAT | 7. Code Quality | Expected | Expected | Not Applicable |

* **MITRE References**
    * [CWE-1076](https://cwe.mitre.org/data/definitions/1076.html)
    * [CWE-1078](https://cwe.mitre.org/data/definitions/1078.html)
    * [M1016](https://attack.mitre.org/mitigations/M1016/)
* **Sources**
    * [OWASP SCVS L1 5.1](https://scvs.owasp.org/scvs/v5-component-analysis/)
    * [OpenSSF Best Practices Badge Silver Level [coding_standards_enforced]](https://www.bestpractices.dev/en/criteria?details=true&rationale=true#1.coding_standards_enforced)
* **HOW TO**
    * [ESLint Docs](https://eslint.org/docs/latest/use/getting-started#installation-and-usage) 

---

### Compilers/Linter Warnings Addressed in order to Merge

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| CQ:LINT | 7. Code Quality | Expected | Expected | Not Applicable |

* **MITRE References**
    * [CWE-1127](https://cwe.mitre.org/data/definitions/1127.html)
* **Sources**
    * [OpenSSF Best Practices Badge Silver Level [warnings_strict]](https://www.bestpractices.dev/en/criteria?details=true&rationale=true#1.warnings_strict)
* **HOW TO**
    * [ESLint Docs](https://eslint.org/docs/latest/use/getting-started#installation-and-usage) 

---

### All Commits are Scanned by a Static Application Security Testing Tool

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| CQ:SAST | 7. Code Quality | Expected | Expected | Not Applicable |

* **MITRE References**
    * [CWE-1076](https://cwe.mitre.org/data/definitions/1076.html)
    * [CWE-1078](https://cwe.mitre.org/data/definitions/1078.html)
    * [M1016](https://attack.mitre.org/mitigations/M1016/)
* **Sources**
    * [OWASP SCVS L1 6.6](https://scvs.owasp.org/scvs/v6-pedigree-and-provenance/)
    * [OpenSSF Scorecard](https://github.com/ossf/scorecard/blob/main/docs/checks.md#sast)
    * [OpenSSF Best Practices Badge Gold Level [static_analysis_common_vulnerabilities]](https://www.bestpractices.dev/en/criteria?details=true&rationale=true#1.static_analysis_common_vulnerabilities)
    * [OpenSSF Best Practices Badge Gold Level [test_continuous_integration]](https://www.bestpractices.dev/en/criteria?details=true&rationale=true#2.test_continuous_integration)
* **HOW TO**
    * [CodeQL Docs](https://docs.github.com/en/code-security/code-scanning/introduction-to-code-scanning/about-code-scanning-with-codeql) 

---

### All Required Commit Status Checks must pass before Merging

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| CQ:CSMP | 7. Code Quality | Expected | Expected | Not Applicable |

* **MITRE References**
    * [CWE-358](https://cwe.mitre.org/data/definitions/358.html)
* **Sources**
    * [OpenSSF Scorecard](https://github.com/ossf/scorecard/blob/main/docs/checks.md#branch-protection)
    * [OpenSSF SCM Best Practices](https://best.openssf.org/SCM-BestPractices/github/repository/requires_status_checks.html)
* **HOW TO**
    * [GitHub Docs](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches#require-status-checks-before-merging) 

---