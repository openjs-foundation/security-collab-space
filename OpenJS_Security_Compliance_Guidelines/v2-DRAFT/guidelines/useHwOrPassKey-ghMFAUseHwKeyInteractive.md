<span style="font-size:0.8em;"><code>ghMFAUseHwKeyInteractive</code></span>  
# Use AAL2/3 Passkeys for GitHub Access


<span style="font-size:1.15em;"><b>Github.com: Use WebAuthN via a passkey (AAL2) or hardware key (AAL3) that activates using a password or biometrics</b></span>

**Project Expectations**

<div align="center">

| Incubating | Active | Archived |
|:-----------:|:--------:|:----------:|
| R | R | R |

</div>


**Implementation:** [Github Docs](https://docs.github.com/en/authentication/securing-your-account-with-two-factor-authentication-2fa/configuring-two-factor-authentication)



**Sources:**
- [OpenSSF Great MFA Project Security Rationale](https://github.com/ossf/great-mfa-project/blob/main/security-rationale.md)
- [NIST SP 800-63Bsup1](https://github.com/ossf/great-mfa-project/blob/main/security-rationale.md)

**MITRE:**
- [CWE-308](https://cwe.mitre.org/data/definitions/308.html)
- [M1032](https://attack.mitre.org/mitigations/M1032/)

**OpenPathFinder:** https://openpathfinder.com/docs/checks/useHwKeyGithubAccess/

**Context:** [GitHub](../context-GitHub.md)



---

<table>
<tr>
  <th align="center">Hierarchy 1</th>
  <th align="center">Hierarchy 2</th>
</tr>
<tr>
  <td>
    <a href="../User Authentication">User Authentication</a><br> > 
    <a href="../useHwOrPassKey">useHwOrPassKey</a>
  </td>
  <td>
    <a href="../useHwOrPassKey">useHwOrPassKey</a><br> >
    <a href="../useHwOrPassKey">useHwOrPassKey</a>
  </td>
</tr>
</table>

---

*Part of: [OpenJS Security Compliance Guide](../README.md)* 