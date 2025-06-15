<span style="font-size:0.8em;"><code>ghRequirePrApprovals</code></span>  
# Require Approved PRs for Mainline Commits (Two+ Maintainers)

**Qualifier:** Multiple Contributors

---

<span style="font-size:1.15em;"><b>Require Approved PRs for all commits to mainline branches</b></span>

<span style="font-size:1.1em;"><b>Why This Matters:</b> Safeguards the integrity of the codebase by ensuring that every change undergoes peer review before merging.</span>

**Project Expectations**

<div align="center">

| Incubating | Active | Archived |
|:-----------:|:--------:|:----------:|
| R | R | N/A |

</div>


**Implementation:** [Github Docs](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches)



**Sources:**
- [OpenSSF Scorecard](https://github.com/ossf/scorecard/blob/main/docs/checks.md)
- [CNCF SSCP v1.0 #190](https://github.com/cncf/tag-security/blob/main/supply-chain-security/supply-chain-security-paper/sscsp.md)

**MITRE:**
- [CAPEC-670](https://capec.mitre.org/data/definitions/670.html)
- [CAPEC-443](https://capec.mitre.org/data/definitions/443.html)
- [CAPEC-438](https://capec.mitre.org/data/definitions/438.html)

**OpenPathFinder:** https://openpathfinder.com/docs/checks/requirePRApprovalForMainline/

**Context:** [GitHub](../context-GitHub.md)



---

<table>
<tr>
  <th align="center">Hierarchy 1</th>
  <th align="center">Hierarchy 2</th>
</tr>
<tr>
  <td>
    <a href="../Code Review">Code Review</a><br> > 
    <a href="../multiPartyReviews">multiPartyReviews</a>
  </td>
  <td>
    <a href="../multiPartyReviews">multiPartyReviews</a><br> >
    <a href="../multiPartyReviews">multiPartyReviews</a>
  </td>
</tr>
</table>

---

*Part of: [OpenJS Security Compliance Guide](../README.md)* 