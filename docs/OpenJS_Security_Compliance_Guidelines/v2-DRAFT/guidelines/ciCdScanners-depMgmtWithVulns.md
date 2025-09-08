<span style="font-size:0.8em;"><code>depMgmtWithVulns</code></span>  
# Automate Dependency Vulnerability Identification


<span style="font-size:1.15em;"><b>An automated process (such as dependabot) is to identify dependencies with publicly disclosed vulnerabilities</b></span>

<span style="font-size:1.1em;"><b>Why This Matters:</b> Being aware of vulnerable dependencies enables a quick response to protect the project's users and maintainers.</span>

**Project Expectations**

<div align="center">

| Incubating | Active | Archived |
|:-----------:|:--------:|:----------:|
| E | E | N/A |

</div>


**Implementation:** [Github Docs](https://docs.github.com/en/code-security/dependabot/dependabot-security-updates/configuring-dependabot-security-updates)



**Sources:**
- [OWASP SCVS L1 5.4](https://scvs.owasp.org/scvs/v5-component-analysis/)
- [OpenSSF Scorecard](https://github.com/ossf/scorecard/blob/main/docs/checks.md)
- [OpenSSF Best Practices Badge Passing Level [dependency_monitoring]](https://www.bestpractices.dev/en/criteria)

**MITRE:**
- [CWE-1395](https://cwe.mitre.org/data/definitions/1395.html)
- [M1016](https://attack.mitre.org/mitigations/M1016/)

**OpenPathFinder:** https://openpathfinder.com/docs/checks/automateVulnDetection/

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
    <a href="../ciCdScanners">ciCdScanners</a>
  </td>
  <td>
    <a href="../dependencyManagement">dependencyManagement</a><br> >
    <a href="../ciCdScanners">ciCdScanners</a>
  </td>
</tr>
</table>

---

*Part of: [OpenJS Security Compliance Guide](../README.md)* 