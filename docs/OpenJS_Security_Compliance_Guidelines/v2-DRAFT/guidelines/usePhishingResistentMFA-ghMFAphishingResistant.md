<span style="font-size:0.8em;"><code>ghMFAphishingResistant</code></span>  
# Do not use MFA methods vulnerable to phishing attacks


<span style="font-size:1.15em;"><b>Do not use Multi Factor Authentication (MFA) methods that are vulnerable to phishing attacks. Methods supported by GitHub that should not be used:</b></span>

<span style="font-size:1.1em;"><b>Why This Matters:</b> Methods like SMS and push-based 2FA are susceptible to SIM swapping, phishing, and "MFA fatigue" attacks,</span>

**Project Expectations**

<div align="center">

| Incubating | Active | Archived |
|:-----------:|:--------:|:----------:|
| E | E | E |

</div>


**Implementation:** [Github Docs](https://docs.github.com/en/authentication/securing-your-account-with-two-factor-authentication-2fa)



**Sources:**
- [OpenSSF Best Practices Badge Gold Level [secure_2FA]](https://www.bestpractices.dev/en/criteria)
- [CISA: Implementing Phishing Resistent MFA](https://www.bestpractices.dev/en/criteria/2)

**MITRE:**
- [CWE-290](https://cwe.mitre.org/data/definitions/290.html)
- [CAPEC-151](https://capec.mitre.org/data/definitions/151.html)
- [T1621](https://attack.mitre.org/techniques/T1621/)
- [M1032](https://attack.mitre.org/mitigations/M1032/)

**OpenPathFinder:** https://openpathfinder.com/docs/checks/MFAImpersonationDefense/

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
    <a href="../usePhishingResistentMFA">usePhishingResistentMFA</a>
  </td>
  <td>
    <a href="../usePhishingResistentMFA">usePhishingResistentMFA</a><br> >
    <a href="../usePhishingResistentMFA">usePhishingResistentMFA</a>
  </td>
</tr>
</table>

---

*Part of: [OpenJS Security Compliance Guide](../README.md)* 