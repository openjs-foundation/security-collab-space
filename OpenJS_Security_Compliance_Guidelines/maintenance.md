# OpenJS Security Compliance Guidelines Maintenance Runbook


## Expectations Reference Table

| Expectation Letter | Expectation Word |
| :- | :- |
| E | Expected |
| D | Deferrable |
| R | Recommended |
| NA | Not Applicable |

# 1) Update the [Category List HackMD](https://hackmd.io/@rudd/ry6JwxCuC)

`(FUTURE NON-HACKMD LINK: https://github.com/openjs-foundation/security-collab-space/security_compliance_guidelines/categories.md)`

The Category List is updated first and acts as the authoriative source of truth for:
* Guideline IDs
* Guideline Expectations

#### Category List Template

    # [Category Name]
    | ID  | Guideline | In | AL&I | Ar |
    | :-: | :- | :-: | :-: | :-: | 
    | [ID] | [Guideline Text] | [Expectation Letter] | [Expectation Letter] | [Expectation Letter] | 

# 2) Update the [Priority Group List HackMD](https://hackmd.io/@rudd/rygTVZROC)

`(FUTURE NON-HACKMD LINK: https://github.com/openjs-foundation/security-collab-space/security_compliance_guidelines/priority_groups.md)`

The Priority Group List is updated after the Category List and acts as the authoritative source of truth for Guideline Priority Group assignment.

#### Priority Group List Template

    ## Priority Group [Number]
    | ID  | Guideline | In | AL&I | Ar | 
    | :-: | - | :-: | :-: | :-: | 
    | [ID] | [Guideline Text] | [Expectation Letter] | [Expectation Letter] | [Expectation Letter] |

# 3) Update the Relevant Priority Group Details Page

`(FUTURE NON-HACKMD LINK: https://github.com/openjs-foundation/security-collab-space/security_compliance_guidelines/priority_groups/priority_group_N.md)`

* [HackMD Priority Group 1](https://hackmd.io/@rudd/rJchQ-AdR)

#### Priority Group Details Page List Template

        ## Priority Group [Number]
        | ID  | Guideline | In | AL&I | Ar | 
        | :-: | - | :-: | :-: | :-: | 
        | [ID] | [Guideline Text] | [Expectation Letter] | [Expectation Letter] | [Expectation Letter] |


#### Priority Group Guideline Details Template

    ### [Guideline Text]

    | ID | Category | Incubating | At Large & Impact | Archived |
    | :-: | :-: | :-: | :-: | :-: |
    | [ID] | [Category Name] | [Expectation Word] | [Expectation Word] | [Expectation Word] |

    [optional explanitory text]

    * **MITRE Reference(s)**
        * [[ID]](https://)
    * **Source(s)**
        * [OpenSSF SCM Best Practices](https://)
        * [OpenSSF npm Best Practices](https://github.com/ossf/package-manager-best-practices/blob/main/published/npm.md)
        * [CNCF CNSWP v1.0](https://github.com/ossf/package-manager-best-practices/blob/main/published/npm.md](https://github.com/cncf/tag-security/blob/main/security-whitepaper/v2/cloud-native-security-whitepaper.md))
        * [OpenSSF Best Practices Badge [Level Name] Level [slug]](https://www.bestpractices.dev/en/criteria#__SLUG_LINK__)
    * **HOW TO**
        * [[Source Name]](https://) 
    
    ---

# 4) Update the Project Tracker Templates

* [HackMD Tracker Template for Incubating Projects](https://hackmd.io/@rudd/rk1SUbRd0)
* [HackMD Tracker Template for At Large and Impact Projects](https://hackmd.io/@rudd/SJoDKbR_C)
* [HackMD Tracker Template for Archived Projects](https://hackmd.io/@rudd/B1X3KZ0OC)

        FUTURE NON-HACKMD LINKS:
        [Tracker Template for Incubating Projects](https://github.com/openjs-foundation/security-collab-space/security_compliance_guidelines/project_templates/incubating.md)
        [Tracker Template for At Large and Impact Projects](https://github.com/openjs-foundation/security-collab-space/security_compliance_guidelines/project_templates/atlarge_impact.md)
        [Tracker Template for Archived Projects](https://github.com/openjs-foundation/security-collab-space/security_compliance_guidelines/project_templates/archived.md)


# 5) (Optional) Update the OpenJS Security Compliance Guidelines [Readme (HackMD)](https://hackmd.io/@rudd/BkhV9Z0O0)

`(FUTURE NON-HACKMD LINK: https://github.com/openjs-foundation/security-collab-space/security_compliance_guidelines/readme.md)`

The landing page readme file is updated last and only once all other content is updated. For the purposes of this Runbook, the readme is only updated when adding an entirely new Category or Priority Group.





