<span style="font-size:0.8em;"><code>ghUpToDateDefaultBranchBeforeMerge</code></span>  
# Require Default Branch Updates Before Merging


<span style="font-size:1.15em;"><b>Default Branch must be Up to Date before Merging</b></span>

<span style="font-size:1.1em;"><b>Why This Matters:</b> Protects against the risk of merging changes that have not been validated against the latest version of the code, which can reintroduce bugs or security vulnerabilities already fixed in recent commits.</span>

**Project Expectations**

<div align="center">

| Incubating | Active | Archived |
|:-----------:|:--------:|:----------:|
| E | E | E |

</div>


**Implementation:** [Github Docs](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches)



**Sources:**
- [OpenSSF Scorecard](https://github.com/ossf/scorecard/blob/main/docs/checks.md)
- [OpenSSF SCM Best Practices](https://github.com/ossf/scorecard/blob/main/docs/checks.md)

**OpenPathFinder:** https://openpathfinder.com/docs/checks/upToDateDefaultBranchBeforeMerge/

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