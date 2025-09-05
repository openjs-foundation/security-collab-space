<span style="font-size:0.8em;"><code>staticAppSecTesting</code></span>  
# Use Static Application Security Testing for All Commits


<span style="font-size:1.15em;"><b>All commits are scanned by a Static Application Security Testing (SAST) tool</b></span>

<span style="font-size:1.1em;"><b>Why This Matters:</b> Scanning just the commit (not the entire app) helps find bugs incrementally rather than all at once when a build is produced.</span>

**Project Expectations**

<div align="center">

| Incubating | Active | Archived |
|:-----------:|:--------:|:----------:|
| E | E | N/A |

</div>


**Implementation:** [CodeQL Docs](https://docs.github.com/en/code-security/code-scanning/introduction-to-code-scanning/about-code-scanning-with-codeql)



**Sources:**
- [OWASP SCVS L1 6.6](https://scvs.owasp.org/scvs/v5-component-analysis/)
- [OpenSSF Scorecard](https://github.com/ossf/scorecard/blob/main/docs/checks.md)
- [OpenSSF Best Practices Badge Gold Level [static_analysis_common_vulnerabilities]](https://www.bestpractices.dev/en/criteria)
- [OpenSSF Best Practices Badge Gold Level [test_continuous_integration]](https://www.bestpractices.dev/en/criteria)

**MITRE:**
- [CWE-1076](https://cwe.mitre.org/data/definitions/1076.html)
- [CWE-1078](https://cwe.mitre.org/data/definitions/1078.html)
- [M1016](https://attack.mitre.org/mitigations/M1016/)

**OpenPathFinder:** https://openpathfinder.com/docs/checks/staticAppSecTesting/

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
    <a href="../ciCdScanners">ciCdScanners</a>
  </td>
  <td>
    <a href="../cicdChecks">cicdChecks</a><br> >
    <a href="../ciCdScanners">ciCdScanners</a>
  </td>
</tr>
</table>

---

*Part of: [OpenJS Security Compliance Guide](../README.md)* 