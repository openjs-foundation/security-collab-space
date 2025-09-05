<span style="font-size:0.8em;"><code>ghRestrictSecretsToRepos</code></span>  
# Restrict GitHub Org Secrets to Specific Repositories


<span style="font-size:1.15em;"><b>GitHub Organization Secrets are Restricted to Selected Repositories</b></span>

<span style="font-size:1.1em;"><b>Why This Matters:</b> Reduces the risk of accidental leakage, misuse, and compromise if an adjacent repo or user is compromised.</span>

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
- [CWE-250](https://cwe.mitre.org/data/definitions/250.html)
- [CAPEC-69](https://capec.mitre.org/data/definitions/69.html)

**OpenPathFinder:** https://openpathfinder.com/docs/checks/restrictOrgSecrets/

**Context:** [GitHub](../context-GitHub.md)



---

<table>
<tr>
  <th align="center">Hierarchy 1</th>
  <th align="center">Hierarchy 2</th>
</tr>
<tr>
  <td>
    <a href="../Service Authorization">Service Authorization</a><br> > 
    <a href="../properCredUse">properCredUse</a>
  </td>
  <td>
    <a href="../cicdPermissions">cicdPermissions</a><br> >
    <a href="../properCredUse">properCredUse</a>
  </td>
</tr>
</table>

---

*Part of: [OpenJS Security Compliance Guide](../README.md)* 