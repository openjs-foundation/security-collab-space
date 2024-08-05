# List of Priority Groups

# Priority Group 0

| ID  | Guideline | In | AL&I | Ar | 
| :-: | - | :-: | :-: | :-: | 
| CQ:SSDT | At least One Primary Maintainer has taken TBD Training on Secure Software Design | E | E | E |
| CQ:TOPT | At least One Primary Maintainer has taken TBD Training on OWASP Top 10 or Equivalent | E | E | E |

# Priority Group 1

| ID  | Guideline | In | AL&I | Ar | 
| :-: | - | :-: | :-: | :-: | 
| UA:MFG | Multi Factor Authentication (MFA) Enforced Across the Github Organization | E | E | E |
| UA:MFN | Multi Factor Authentication (MFA) Enforced Across the npm Organization | E | E | E |
| UA:MFO | Multi Factor Authentication (MFA) Enforced in All Tools Wherever Techncially Feasible | E | E | E | 
| UA:MFI | Use Multi Factor Authentication (MFA) Methods that Defend Against Impersonation when Available | E | E | E | 

# Priority Group 2

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: | 
| SA:NSSC | No Secrets and Credentials in Source Code | E | E | E |
| SA:GHS | Secrets are injected at runtime, such as environment variables or as a file (eg: use Github Secrets) | E | E | E |
| CQ:CSS | All Commits are Scanned for Secrets and Credentials  | E | E | NA |
| CQ:CWSB | New Commits Containing Secrets or Credentials are Blocked from Merging | E | E | NA |

# Priority Group 3

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: | 
| UA:SSH | Use SSH keys for developer access to source code repositories and use a passphrase | E | E | E
| SA:NPMP | Publish to npm using an MFA-enabled account rather than single factor legacy or granular access tokens | E | E | E |
| SA:WHS | Github Webhooks Use Secrets | E | E | E |

# Priority Group 4

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: |
| UP:GHOP | Default Github Org Member Permissions Should Be Restricted | E | E | E |
| UP:ADMPR | Only Admins Should Be Able To Create Public Repositories | E | E | E |
| UP:ADMBP | [For Projects with Two or more Admins] Do not allow Admins to Bypass Branch Protection Settings | E | E | E |
| UP:RAFR | Define roles aligned to functional responsibilities | E | E | E |
| UP:RWA | Define Individuals/Teams who Write Access to a Github Repo | E | E | E |
| UP:OAC | [For Projects with Two or more Owners] Have at least Two Owners Configured for Access Continuity | E | E | E |

# Priority Group 5

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: |
| VM:AEV30 | Actively Exploited Critical Vulnerabilities Patched within 30 Days | E | E | NA |
| VM:NCV90 | Non-Critical Exploitable Vulnerabilities Patched within 90 Days | E | E | NA |

# Priority Group 6

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: |
| D:IDPV | An automated process to identify dependencies with publicly disclosed vulnerabilities | E | E | E |
| CQ:SAT | Use an Automated Static Code Analysis Tool (eg: ESLInt) | E | E | NA |
| CQ:LINT | Compilers/Linter Warnings Addressed in order to Merge | E | E | NA |
| CQ:SAST | All Commits are Scanned by a Static Application Security Testing Tool | E | E | NA |
| CQ:CSMP | All Required Commit Status Checks must pass before Merging | E | E | NA |

# Priority Group 7

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: | 
| CVD:OJSG | Security.md Meets OpenJS CVD Guidelines  | E | E | E |
| CVD:PVR | Project Leverages a CVD Tool to Privately Receive/Manage External Vulnerability Reports (eg: H1/GH PVR) | E | E | E |
| CVD:SLA14 | All External Vulnerability Reports Responded to <14 Days | E | E | NA |
| CVD:VRP | Establish a Clear Communication and Vulnerability Response Plan | E | E | E |
| CVD:CVE | All Known Security Vulnerabilities are Issued a CVE | E | E | E |
| CVD:RN | Release Notes must Include the CVE ID of Patched Security Vulnerabilities | E | E | E |

# Priority Group 8

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: |
| CQ:RT | Regression Tests for => 50% of Bugs and 100% of Security Vulns | D | E | NA |

# Priority Group 9

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: |
| GHW:DTRO | Github Org Default Workflow Token Permissions are Set to Read Only | E | E | NA |
| GHW:WPR | Workflows are not Allowed To Create or Approve Pull Requests | E | E | E |
| SC:PFP | Prevent Force Push on Default Branch | E | E | E |
| SC:PBD | Prevent Default Branch Deletion | E | E | E |
| SC:UTD | Default Branch must be Up to Date before Merging | E | E | E |

# Priority Group 10

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: |
| GHW:SRSR | GitHub Organization Secrets are Restricted to Selected Repositories | E | E | NA |
| GHW:ALTA | GitHub Actions Should Be Limited To Verified or Explicitly Trusted Actions | E | E | NA |
| GHW:SHR | Disable use of Self-Hosted Runners in Github Org | E | E | E |

# Priority Group 11

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: |
| GHW:CEAC | Build Pipeline Cannot Execute Arbitrary Code from Outside of a Build Script | E | E | NA |
| GHW:JLWP | Only Allow Workflows Write Permissions at the Job-Level | E | E | E |
| GHW:ASI | Avoid Script Injection from Untrusted Context Variables | E | E | NA |

# Priority Group 12

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: |
| GHW:ABP | Consistent and Automated Build Process is Documented and Used | E | E | NA |
| VM:UPP | Commonly Used Older Versions Supported or Upgrade Path Provided/Documented | E | E | NA |
| CR:DSA | [For Projects with Two or more Maintainers] Document Software Architecture | D | E | NA |

# Priority Group 13

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: |
| GHW:PAWS | Pin Actions with Access to Secrets to a Full Length Commit SHA | E | E | NA |

# Priority Group 14

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: |
| D:ALD | Automated Process is Used to Monitor for and Maintain a List of Out of Date Dependencies | E | E | E |
| D:MDUI | Modified dependencies are uniquely identified and distinct from origin dependency | E | E | E |
| D:DTD | [Freestanding Applications Only] A Machine Readable List of all Direct and Transitive Dependencies is Available for the Software | E | E | E |
| VM:RD | A new release to refresh dependencies occurs at least annually | E | E | NA |

# Recommendation Group 1

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: |
| UA:AAL3I | Github.com: Use a passkey (AAL2) or hardware key (AAL3) that activates using a password or biometrics | R | R | R |
| UA:AAL3NI | Non-Interactive Github: Use a passkey (AAL2) or hardware key (AAL3) that activates using a password or biometrics | R | R | R |
| UA:AAL3O | All Other Contexts: Use a passkey (AAL2) or hardware key (AAL3) that activates using a password or biometrics | R | R | R |

# Recommendation Group 2

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: |
| GHW:LCF | Limit changes from forks to workflows by requiring approval for all outside collaborators | R | R | R |
| GHW:UWSS | Use a Workflow Security Scanner | R | R | R |
| GHW:URSS | Use a Github Runner Security Scanner | R | R | R |

# Recommendation Group 3

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: |
| UP:GHADA | Github Organization Admins Should Have Activity In The Last 6 Months | R | R | NA |
| UP:GHWPA | Github Organization Members with Write Permissions Should Have Activity In The Last 6 Months | R | R | NA |

# Recommendation Group 4

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: |
| SC:MPR | Require Pull Requests before Merging | R | R | R |
| SC:OCS | Github Org Requires Commit Signoff for Web-Based Commits | R | R | R |
| SC:RSC | Require Signed Commits | R | R | R |
| SC:RAPR | [For Projects with Two or more Maintainers] Require Approved PRs for all commits to mainline branches | R | R | R |

# Recommendation Group 5

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: |
| D:CPL | [Freestanding Applications Only] Commit a package-lock.json file with each release | R | R | R |

# Recommendation Group 6

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: |
| CR:2PR | [For Projects with Two or more Maintainers] Require Two Party Review | R | R | NA |
| CR:COR | [For Projects with Four or more Maintainers] Require Code Owners Review | R | R | NA |
| SC:RAPR | [For Projects with Two or more Maintainers] Require Approved PRs for all commits to mainline branches | R | R | R |

# Recommendation Group 7

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: |
| UP:LGHO | Limit Number of Github Org Owners (ideally Fewer Than Three) | R | R | R |
| UP:LGHAD | Limit Number of Github Repository Admins (ideally Fewer Than Three) | R | R | R |

# Recommendation Group 8

| ID  | Guideline | In | AL&I | Ar |
| :-: | - | :-: | :-: | :-: |
| VM:AEV14 | Actively Exploited Critical and High Vulnerabilities Patched within 14 Days | R | R | NA |
| VM:NCV60 | Non-Critical Expoitable Vulnerabilities Patched within 60 Days | R | R | NA |
