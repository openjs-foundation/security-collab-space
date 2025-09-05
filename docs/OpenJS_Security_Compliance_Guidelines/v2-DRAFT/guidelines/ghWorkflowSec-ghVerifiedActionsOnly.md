<span style="font-size:0.8em;"><code>ghVerifiedActionsOnly</code></span>  
# Limit GitHub Actions to Verified or Trusted Actions


<span style="font-size:1.15em;"><b>GitHub Actions Should Be Limited To Verified or Explicitly Trusted Actions</b></span>

<span style="font-size:1.1em;"><b>Why This Matters:</b> Allowing only verified or trusted GitHub Actions reduces the risk of supply chain attacks from malicious or hijacked third-party workflows. Unverified actions could contain hidden backdoors or exfiltrate secrets during CI/CD runs.</span>

**Project Expectations**

<div align="center">

| Incubating | Active | Archived |
|:-----------:|:--------:|:----------:|
| E | E | N/A |

</div>


**Implementation:** [Github Docs](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository)



**Sources:**
- [OpenSSF SCM Best Practices](https://github.com/ossf/scorecard/blob/main/docs/checks.md)

**MITRE:**
- [CWE-1357](https://cwe.mitre.org/data/definitions/1357.html)
- [CAPEC-17](https://capec.mitre.org/data/definitions/17.html)
- [CAPEC-538](https://capec.mitre.org/data/definitions/538.html)
- [CAPEC-446](https://capec.mitre.org/data/definitions/446.html)

**OpenPathFinder:** https://openpathfinder.com/docs/checks/verifiedActionsOnly/

**Context:** [GitHub](../context-GitHub.md)



---

<table>
<tr>
  <th align="center">Hierarchy 1</th>
  <th align="center">Hierarchy 2</th>
</tr>
<tr>
  <td>
    <a href="../Dependencies">Dependencies</a><br> > 
    <a href="../ghWorkflowSec">ghWorkflowSec</a>
  </td>
  <td>
    <a href="../cicdControls">cicdControls</a><br> >
    <a href="../ghWorkflowSec">ghWorkflowSec</a>
  </td>
</tr>
</table>

---

*Part of: [OpenJS Security Compliance Guide](../README.md)* 