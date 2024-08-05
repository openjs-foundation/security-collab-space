# Priority Group 1

| ID  | Guideline | In | AL&I | Ar | 
| :-: | - | :-: | :-: | :-: | 
| UA:MFG | Multi Factor Authentication (MFA) Enforced Across the Github Organization | E | E | E |
| UA:MFN | Multi Factor Authentication (MFA) Enforced Across the npm Organization | E | E | E |
| UA:MFO | Multi Factor Authentication (MFA) Enforced in All Tools Wherever Techncially Feasible | E | E | E | 
| UA:MFI | Use Multi Factor Authentication (MFA) Methods that Defend Against Impersonation when Available | E | E | E | 

### Multi Factor Authentication (MFA) Enforced Across the Github Organization

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| UA:MFG | 1. User Authentication | Expected | Expected | Expected |

* **MITRE References**
    * [CWE-308](https://cwe.mitre.org/data/definitions/308.html)
    * [M1032](https://attack.mitre.org/mitigations/M1032/)
* **Sources**
    * [OpenSSF SCM Best Practices](https://best.openssf.org/SCM-BestPractices/github/enterprise/enterprise_enforce_two_factor_authentication.html)
    * [OpenSSF Best Practices Badge Gold Level [require_2FA]](https://www.bestpractices.dev/en/criteria#2.require_2FA)
* **HOW TO**
    * [GitHub Docs](https://docs.github.com/en/organizations/keeping-your-organization-secure/managing-two-factor-authentication-for-your-organization/requiring-two-factor-authentication-in-your-organization) 

---

### Multi Factor Authentication (MFA) Enforced Across the npm Organization

| ID | Category | Incubating | At Large & Impact | Archived |
| - | - | - | - | - |
| UA:MFN | 1. User Authentication | Expected | Expected | Expected |

* **MITRE References**
    * [CWE-308](https://cwe.mitre.org/data/definitions/308.html)
    * [M1032](https://attack.mitre.org/mitigations/M1032/)
* **Source**
    * [OpenSSF npm Best Practices](https://github.com/ossf/package-manager-best-practices/blob/main/published/npm.md)
* **HOW TO**
    * [npm Docs](https://docs.npmjs.com/requiring-two-factor-authentication-in-your-organization)

---

### Multi Factor Authentication (MFA) Enforced in Other Tools Wherever Techncially Feasible

| ID | Category | Incubating | At Large & Impact | Archived |
| - | - | - | - | - |
| UA:MFO | 1. User Authentication | Expected | Expected | Expected |

* **MITRE References**
    * [CWE-308](https://cwe.mitre.org/data/definitions/308.html)
    * [M1032](https://attack.mitre.org/mitigations/M1032/)
* **Source**
    * [CNCF CNSWP v1.0](https://github.com/ossf/package-manager-best-practices/blob/main/published/npm.md](https://github.com/cncf/tag-security/blob/main/security-whitepaper/v2/cloud-native-security-whitepaper.md))
* **HOW TO**
    * TBD 

---

###  Use Multi Factor Authentication (MFA) Methods that Defend Against Impersonation when Available

| ID | Category | Incubating | At Large & Impact | Archived |
| :-: | :-: | :-: | :-: | :-: |
| UA:MFI | 1. User Authentication | Expected | Expected | Expected |

* **MITRE References**
    * [CWE-290](https://cwe.mitre.org/data/definitions/290.html)
    * [M1032](https://attack.mitre.org/mitigations/M1032/)
    * [CAPEC-151](https://capec.mitre.org/data/definitions/151.html)
    * [T1621](https://attack.mitre.org/techniques/T1621)
* **Sources**
    * [OpenSSF Best Practices Badge Gold Level [secure_2FA]](https://www.bestpractices.dev/en/criteria/2#2.secure_2FA)
* **HOW TO**
    * [GitHub Docs](https://docs.github.com/en/authentication/securing-your-account-with-two-factor-authentication-2fa) 
