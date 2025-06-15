<span style="font-size:0.8em;"><code>ghWebhooksUseSecrets</code></span>  
# Secure GitHub Webhooks with Secrets


<span style="font-size:1.15em;"><b>Github Webhooks Use Secrets</b></span>

<span style="font-size:1.1em;"><b>Why This Matters:</b> Using a secret token to sign and validate incoming webhook payloads prevents attackers from sending forged requests that could manipulate CI/CD workflows or leak sensitive data.</span>

**Project Expectations**

<div align="center">

| Incubating | Active | Archived |
|:-----------:|:--------:|:----------:|
| E | E | E |

</div>


**Implementation:** [Github Docs](https://docs.github.com/en/actions/security-guides/using-secrets-in-github-actions)



**Sources:**
- [OpenSSF Scorecard](https://github.com/ossf/scorecard/blob/main/docs/checks.md)
- [OpenSSF SCM Best Practices](https://github.com/ossf/scorecard/blob/main/docs/checks.md)

**MITRE:**
[CWE-306](https://cwe.mitre.org/data/definitions/306.html)

**OpenPathFinder:** https://openpathfinder.com/docs/checks/githubWebhookSecrets/

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
    <a href="../credentialMgmt">credentialMgmt</a><br> >
    <a href="../properCredUse">properCredUse</a>
  </td>
</tr>
</table>

---

*Part of: [OpenJS Security Compliance Guide](../README.md)* 