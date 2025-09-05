<span style="font-size:0.8em;"><code>adminOnlyRepoCreation</code></span>  
# Allow Only Admins to Create Public Repositories

**Qualifier:** Multiple Contributors

---

<span style="font-size:1.15em;"><b>Only Admins Should Be Able To Create Public Repositories</b></span>

<span style="font-size:1.1em;"><b>Why This Matters:</b> Protects against the accidental or malicious exposure of private assets by ensuring that only trusted maintainers can make repositories publicly accessible.</span>

**Project Expectations**

<div align="center">

| Incubating | Active | Archived |
|:-----------:|:--------:|:----------:|
| E | E | E |

</div>


**Implementation:** [Github Docs](https://docs.github.com/en/organizations/managing-organization-settings/restricting-repository-creation-in-your-organization)



**Sources:**
- [OpenSSF SCM Best Practices](https://github.com/ossf/scorecard/blob/main/docs/checks.md)

**MITRE:**
[CAPEC-122](https://capec.mitre.org/data/definitions/122.html)

**OpenPathFinder:** https://openpathfinder.com/docs/checks/adminRepoCreationOnly/

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
    <a href="../branchProtection">branchProtection</a>
  </td>
  <td>
    <a href="../cicdControls">cicdControls</a><br> >
    <a href="../branchProtection">branchProtection</a>
  </td>
</tr>
</table>

---

*Part of: [OpenJS Security Compliance Guide](../README.md)* 