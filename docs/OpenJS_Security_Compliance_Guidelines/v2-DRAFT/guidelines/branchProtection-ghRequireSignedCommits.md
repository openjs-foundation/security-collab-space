<span style="font-size:0.8em;"><code>ghRequireSignedCommits</code></span>  
# Require Signed Commits


<span style="font-size:1.15em;"><b>Require Signed Commits</b></span>

<span style="font-size:1.1em;"><b>Why This Matters:</b> Protects against impersonation in the event of account (but not workstation) compromise by requiring a cryptographic signature stored and accessed separately from authentication credentials.</span>

**Project Expectations**

<div align="center">

| Incubating | Active | Archived |
|:-----------:|:--------:|:----------:|
| R | R | N/A |

</div>


**Implementation:** [Github Docs](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches)



**Sources:**
- [CNCF SSCP 1.0 #325](https://github.com/cncf/tag-security/blob/main/supply-chain-security/supply-chain-security-paper/sscsp.md)
- [OpenSSF SCM Best Practices](https://github.com/ossf/scorecard/blob/main/docs/checks.md)

**OpenPathFinder:** https://openpathfinder.com/docs/checks/requireSignedCommits/

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