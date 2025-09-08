<span style="font-size:0.8em;"><code>checkCommits4Creds</code></span>  
# Check All Commits for Credentials


<span style="font-size:1.15em;"><b>All commits are scanned for secrets and credentials</b></span>

<span style="font-size:1.1em;"><b>Why This Matters:</b> Secret scanning prevents sensitive information like API keys, credentials, or tokens from being accidentally committed and exposed, which attackers can use to exploit systems or data.</span>

**Project Expectations**

<div align="center">

| Incubating | Active | Archived |
|:-----------:|:--------:|:----------:|
| E | E | N/A |

</div>


**Implementation:** [Github Docs](https://docs.github.com/en/code-security/secret-scanning/about-secret-scanning)

**References:**
- [Uber breach (2016)](https://techcrunch.com/2017/11/21/uber-paid-hackers-to-keep-data-breach-quiet/)
- [Toyota API keys leaked (2022)](https://www.bleepingcomputer.com/news/security/toyota-exposed-customer-data-after-git-credentials-were-published-online/)



**Sources:**
- [CNCF SSCP v1.0 #184](https://github.com/cncf/tag-security/blob/main/supply-chain-security/supply-chain-security-paper/sscsp.md)

**MITRE:**
- [CWE-540](https://cwe.mitre.org/data/definitions/540.html)
- [CAPEC-150](https://capec.mitre.org/data/definitions/150.html)

**OpenPathFinder:** https://openpathfinder.com/docs/checks/scanCommitsForSensitiveInfo/

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