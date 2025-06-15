<span style="font-size:0.8em;"><code>ghInjectSecretsAtRuntime</code></span>  
# Ensure that the secrets are injected at runtime


<span style="font-size:1.15em;"><b>Secrets are injected at runtime, such as environment variables or as a file (eg: use Github Secrets)</b></span>

<span style="font-size:1.1em;"><b>Why This Matters:</b> Injecting secrets securely at runtime ensures that even if the codebase is made public or an attacker scans the repository, credentials remain inaccessible.</span>

**Project Expectations**

<div align="center">

| Incubating | Active | Archived |
|:-----------:|:--------:|:----------:|
| E | E | E |

</div>


**Implementation:** [Github Docs](https://docs.github.com/en/actions/security-guides/using-secrets-in-github-actions)



**Sources:**
- [OpenSSF Scorecard](https://github.com/ossf/scorecard/blob/main/docs/checks.md)
- [CNCF CNSWP 2.0 #195](https://github.com/cncf/tag-security/blob/main/security-whitepaper/v2/cloud-native-security-whitepaper.md)

**MITRE:**
[CWE-538](https://cwe.mitre.org/data/definitions/538.html)

**OpenPathFinder:** https://openpathfinder.com/docs/checks/injectedSecretsAtRuntime/

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
    <a href="../cicdControls">cicdControls</a><br> >
    <a href="../properCredUse">properCredUse</a>
  </td>
</tr>
</table>

---

*Part of: [OpenJS Security Compliance Guide](../README.md)* 