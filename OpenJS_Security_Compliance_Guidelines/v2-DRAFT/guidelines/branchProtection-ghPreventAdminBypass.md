<span style="font-size:0.8em;"><code>ghPreventAdminBypass</code></span>  
# Prevent Admins from Bypassing Branch Protection

**Qualifier:** Multiple Contributors

---

<span style="font-size:1.15em;"><b>Do not allow Admins to Bypass Branch Protection Settings</b></span>

<span style="font-size:1.1em;"><b>Why This Matters:</b> Protects against unauthorized or unreviewed changes by ensuring that even administrators must adhere to established branch protection rules.</span>

**Project Expectations**

<div align="center">

| Incubating | Active | Archived |
|:-----------:|:--------:|:----------:|
| E | E | E |

</div>


**Implementation:** [Github Docs](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches)



**Sources:**
- [Github Supply Chain Security Best Practices](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches)

**MITRE:**
[CAPEC-122](https://capec.mitre.org/data/definitions/122.html)

**OpenPathFinder:** https://openpathfinder.com/docs/checks/preventBranchProtectionBypass/

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