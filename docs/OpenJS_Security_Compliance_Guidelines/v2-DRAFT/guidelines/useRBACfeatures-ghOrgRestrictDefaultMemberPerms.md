<span style="font-size:0.8em;"><code>ghOrgRestrictDefaultMemberPerms</code></span>  
# Restrict Default GitHub Org Member Permissions

**Qualifier:** Multiple Contributors

---

<span style="font-size:1.15em;"><b>Default Github Org Member Permissions Should Be Restricted</b></span>

<span style="font-size:1.1em;"><b>Why This Matters:</b> Protects against unintentional over permissioning by ensuring that new organization members do not automatically receive permissions to view or modify repositories.</span>

**Project Expectations**

<div align="center">

| Incubating | Active | Archived |
|:-----------:|:--------:|:----------:|
| E | E | E |

</div>


**Implementation:** [Github Docs](https://docs.github.com/en/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/setting-base-permissions-for-an-organization)



**Sources:**
- [OpenSSF SCM Best Practices](https://github.com/ossf/scorecard/blob/main/docs/checks.md)

**MITRE:**
- [CAPEC-180](https://capec.mitre.org/data/definitions/180.html)
- [M1026](https://attack.mitre.org/mitigations/M1026/)

**OpenPathFinder:** https://openpathfinder.com/docs/checks/restrictedOrgPermissions/

**Context:** [GitHub](../context-GitHub.md)



---

<table>
<tr>
  <th align="center">Hierarchy 1</th>
  <th align="center">Hierarchy 2</th>
</tr>
<tr>
  <td>
    <a href="../User Account Permissions">User Account Permissions</a><br> > 
    <a href="../useRBACfeatures">useRBACfeatures</a>
  </td>
  <td>
    <a href="../accessGovernance">accessGovernance</a><br> >
    <a href="../useRBACfeatures">useRBACfeatures</a>
  </td>
</tr>
</table>

---

*Part of: [OpenJS Security Compliance Guide](../README.md)* 