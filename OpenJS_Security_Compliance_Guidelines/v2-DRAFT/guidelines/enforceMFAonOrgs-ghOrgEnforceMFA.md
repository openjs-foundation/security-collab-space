<span style="font-size:0.8em;"><code>ghOrgEnforceMFA</code></span>  
# Enforce MFA in GitHub Organization(s)


<span style="font-size:1.15em;"><b>Multi Factor Authentication (MFA) enforced on Member user accounts at the Github Organization level.</b></span>

<span style="font-size:1.1em;"><b>Why This Matters:</b> Ensures all contributors with access to the GitHub organization are using MFA.</span>

**Project Expectations**

<div align="center">

| Incubating | Active | Archived |
|:-----------:|:--------:|:----------:|
| E | E | E |

</div>


**Implementation:** [Github Docs](https://docs.github.com/en/organizations/keeping-your-organization-secure/managing-two-factor-authentication-for-your-organization/requiring-two-factor-authentication-in-your-organization)



**Sources:**
- [OpenSSF SCM Best Practices](https://github.com/ossf/scorecard/blob/main/docs/checks.md)
- [OpenSSF Best Practices Badge Gold Level [require_2FA]](https://www.bestpractices.dev/en/criteria)

**MITRE:**
- [CWE-308](https://cwe.mitre.org/data/definitions/308.html)
- [M1032](https://attack.mitre.org/mitigations/M1032/)

**OpenPathFinder:** https://openpathfinder.com/docs/checks/githubOrgMFA/

**Context:** [GitHub](../context-GitHub.md)



---

<table>
<tr>
  <th align="center">Hierarchy 1</th>
  <th align="center">Hierarchy 2</th>
</tr>
<tr>
  <td>
    <a href="../User Authentication">User Authentication</a><br> > 
    <a href="../enforceMFAonOrgs">enforceMFAonOrgs</a>
  </td>
  <td>
    <a href="../enforceMFAonOrgs">enforceMFAonOrgs</a><br> >
    <a href="../enforceMFAonOrgs">enforceMFAonOrgs</a>
  </td>
</tr>
</table>

---

*Part of: [OpenJS Security Compliance Guide](../README.md)* 