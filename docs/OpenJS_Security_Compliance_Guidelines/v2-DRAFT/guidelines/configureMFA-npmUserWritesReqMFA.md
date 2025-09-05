<span style="font-size:0.8em;"><code>npmUserWritesReqMFA</code></span>  
# Require MFA for User Account Writes


<span style="font-size:1.15em;"><b>Multi Factor Authentication (MFA) enabled and set to 'Authorization and writes' on maintainer user accounts</b></span>

**Project Expectations**

<div align="center">

| Incubating | Active | Archived |
|:-----------:|:--------:|:----------:|
| E | E | E |

</div>


**Implementation:** [npm Docs](https://docs.npmjs.com/requiring-two-factor-authentication-in-your-organization)



**Sources:**
- [OpenSSF npm Best Practices](https://github.com/ossf/package-manager-best-practices/blob/main/published/npm.md)

**MITRE:**
- [CWE-308](https://cwe.mitre.org/data/definitions/308.html)
- [M1032](https://attack.mitre.org/mitigations/M1032/)

**OpenPathFinder:** https://openpathfinder.com/docs/checks/npmPublicationMFA/

**Context:** [npm](../context-npm.md)



---

<table>
<tr>
  <th align="center">Hierarchy 1</th>
  <th align="center">Hierarchy 2</th>
</tr>
<tr>
  <td>
    <a href="../User Authentication">User Authentication</a><br> > 
    <a href="../configureMFA">configureMFA</a>
  </td>
  <td>
    <a href="../cicdControls">cicdControls</a><br> >
    <a href="../configureMFA">configureMFA</a>
  </td>
</tr>
</table>

---

*Part of: [OpenJS Security Compliance Guide](../README.md)* 