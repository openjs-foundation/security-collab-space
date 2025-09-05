<span style="font-size:0.8em;"><code>ghDefaultBranchNoForcePush</code></span>  
# Disable Force Push on Default Branch

**Qualifier:** Multiple Contributors

---

<span style="font-size:1.15em;"><b>Prevent Force Push on Default Branch</b></span>

<span style="font-size:1.1em;"><b>Why This Matters:</b> By disallowing force pushes, projects maintain a transparent and auditable history, making it much harder to remove evidence of injected vulnerabilities or circumvent CI checks.</span>

**Project Expectations**

<div align="center">

| Incubating | Active | Archived |
|:-----------:|:--------:|:----------:|
| R | R | N/A |

</div>


**Implementation:** [Github Docs](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches)



**Sources:**
- [OpenSSF Scorecard](https://github.com/ossf/scorecard/blob/main/docs/checks.md)
- [OpenSSF SCM Best Practices](https://github.com/ossf/scorecard/blob/main/docs/checks.md)

**OpenPathFinder:** https://openpathfinder.com/docs/checks/noForcePushDefaultBranch/

**Context:** [GitHub](../context-GitHub.md)



---

<table>
<tr>
  <th align="center">Hierarchy 1</th>
  <th align="center">Hierarchy 2</th>
</tr>
<tr>
  <td>
    <a href="../Source Control">Source Control</a><br> > 
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