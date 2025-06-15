<span style="font-size:0.8em;"><code>credsNotInProjectRepoFiles</code></span>  
# Credentials are not stoerd in repositories


<span style="font-size:1.15em;"><b>Do not store secrets or credentials in source code</b></span>

<span style="font-size:1.1em;"><b>Why This Matters:</b> Secrets stored in source code can be discovered by searching open source repositories and file analysis.</span>

**Project Expectations**

<div align="center">

| Incubating | Active | Archived |
|:-----------:|:--------:|:----------:|
| E | E | E |

</div>


**Implementation:** [Github Docs](https://docs.github.com/en/code-security/secret-scanning/about-secret-scanning)



**Sources:**
- [OpenSSF Best Practices Badge Passing Level [no_leaked_credentials]](https://www.bestpractices.dev/en/criteria)

**MITRE:**
[CWE-540](https://cwe.mitre.org/data/definitions/540.html)

**OpenPathFinder:** https://openpathfinder.com/docs/checks/noSensitiveInfoInRepositories/

**Context:** [GitHub](../context-GitHub.md)



---

<table>
<tr>
  <th align="center">Hierarchy 1</th>
  <th align="center">Hierarchy 2</th>
</tr>
<tr>
  <td>
    <a href="../Service Authentication">Service Authentication</a><br> > 
    <a href="../properCredUse">properCredUse</a>
  </td>
  <td>
    <a href="../cicdChecks">cicdChecks</a><br> >
    <a href="../properCredUse">properCredUse</a>
  </td>
</tr>
</table>

---

*Part of: [OpenJS Security Compliance Guide](../README.md)* 