# Priority Group 4

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: |
| UP:GHOP | Default Github Org Member Permissions Should Be Restricted | E | E | E |
| UP:ADMPR | Only Admins Should Be Able To Create Public Repositories | E | E | E |
| UP:ADMBP | [For Projects with Two or more Admins] Do not allow Admins to Bypass Branch Protection Settings | E | E | E |
| UP:RAFR | Define roles aligned to functional responsibilities | E | E | E |
| UP:RWA | Define Individuals/Teams who Write Access to a Github Repo | E | E | E |
| UP:OAC | [For Projects with Two or more Owners] Have at least Two Owners Configured for Access Continuity | E | E | E |

### Use SSH keys for developer access to source code repositories and use a passphrase

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| UP:GHOP | 2. User Account Permissions | Expected | Expected | Expected |

* **MITRE References**
    * [CAPEC-180](https://capec.mitre.org/data/definitions/180.html)
    * [M1026](https://attack.mitre.org/mitigations/M1026/)
* **Sources**
    * [OpenSSF SCM Best Practices](https://best.openssf.org/SCM-BestPractices/github/organization/default_repository_permission_is_not_none.html)
* **HOW TO**
    * [GitHub Docs](https://docs.github.com/en/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/setting-base-permissions-for-an-organization) 

---

### Only Admins Should Be Able To Create Public Repositories

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| UP:ADMPR | 2. User Account Permissions | Expected | Expected | Expected |

* **MITRE References**
    * [CAPEC-122](https://capec.mitre.org/data/definitions/122.html)
* **Sources**
    * [OpenSSF SCM Best Practices](https://best.openssf.org/SCM-BestPractices/github/organization/non_admins_can_create_public_repositories.html)
* **HOW TO**
    * [GitHub Docs](https://docs.github.com/en/organizations/managing-organization-settings/restricting-repository-creation-in-your-organization) 

---

### [For Projects with Two or more Admins] Do not allow Admins to Bypass Branch Protection Settings

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| UP:ADMBP | 2. User Account Permissions | Expected | Expected | Expected |

* **MITRE References**
    * [CAPEC-122](https://capec.mitre.org/data/definitions/122.html)
* **Sources**
    * [Github Supply Chain Security Best Practices](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches)
* **HOW TO**
    * [GitHub Docs](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches#do-not-allow-bypassing-the-above-settings)

---

### Define roles aligned to functional responsibilities

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| UP:RAFR | 2. User Account Permissions | Expected | Expected | Expected |

* **MITRE References**
    * [CAPEC-122](https://capec.mitre.org/data/definitions/122.html)
    * [M1018](https://attack.mitre.org/mitigations/M1018/) 
* **Sources**
    * [CNCF SSCP v1.0](https://github.com/cncf/tag-security/blob/main/supply-chain-security/supply-chain-security-paper/sscsp.md#define-roles-aligned-to-functional-responsibilities)
    * [OpenSSF Best Practices Badge Silver Level [roles_responsibilities]](https://www.bestpractices.dev/en/criteria?details=true&rationale=true#1.roles_responsibilities)
* **HOW TO**
    * [GitHub Docs](https://docs.github.com/en/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/repository-roles-for-an-organization)

---

### Define Individuals/Teams who Write Access to a Github Repo

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| UP:RWA | 2. User Account Permissions | Expected | Expected | Expected |

* **MITRE References**
    * [CAPEC-180](https://capec.mitre.org/data/definitions/180.html)
    * [M1026](https://attack.mitre.org/mitigations/M1026/) 
* **Sources**
    * [CNCF SSCP v1.0](https://github.com/cncf/tag-security/blob/main/supply-chain-security/supply-chain-security-paper/sscsp.md#define-individualsteams-that-are-responsible-for-code-in-a-repository-and-associated-coding-conventions)
* **HOW TO**
    * [GitHub Docs](https://docs.github.com/en/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/repository-roles-for-an-organization)

---

### [For Projects with Two or more Owners] Have at least Two Owners Configured for Access Continuity

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| UP:OAC | 2. User Account Permissions | Expected | Expected | Expected |

* **MITRE References**
    * [M1026](https://attack.mitre.org/mitigations/M1026/) 
* **Sources**
    * [OpenSSF Best Practices Badge Silver Level [access_continuity]](https://www.bestpractices.dev/en/criteria?details=true&rationale=true#1.access_continuity)
* **HOW TO**
    * [GitHub Docs](https://docs.github.com/en/organizations/managing-peoples-access-to-your-organization-with-roles/maintaining-ownership-continuity-for-your-organization)