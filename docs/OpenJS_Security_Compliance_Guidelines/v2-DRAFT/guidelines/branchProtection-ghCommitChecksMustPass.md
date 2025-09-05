<span style="font-size:0.8em;"><code>ghCommitChecksMustPass</code></span>  
# All Commit/PR Checks (including any Warnings) must Pass before merging


<span style="font-size:1.15em;"><b>Checks such as: Code SAST, Credential SAST, Linters, Dependency Scanner must pass by addressing all items (eg: compiler and linter warnings) before berging. </b></span>

<span style="font-size:1.1em;"><b>Why This Matters:</b> This enforcement control ensures no code can be merged unless it passes all automated checks, including tests, linters, and security scans.</span>

**Project Expectations**

<div align="center">

| Incubating | Active | Archived |
|:-----------:|:--------:|:----------:|
| E | E | N/A |

</div>


**Implementation:** [Github Docs](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches)



**Sources:**
- [OpenSSF Scorecard](https://github.com/ossf/scorecard/blob/main/docs/checks.md)
- [OpenSSF SCM Best Practices](https://github.com/ossf/scorecard/blob/main/docs/checks.md)

**MITRE:**
[CWE-358](https://cwe.mitre.org/data/definitions/358.html)

**OpenPathFinder:** https://openpathfinder.com/docs/checks/commitStatusChecks/

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