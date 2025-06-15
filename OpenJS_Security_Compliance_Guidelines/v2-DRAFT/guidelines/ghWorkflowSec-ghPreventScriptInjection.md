<span style="font-size:0.8em;"><code>ghPreventScriptInjection</code></span>  
# Avoid Script Injection from Untrusted Variables


<span style="font-size:1.15em;"><b>Avoid Script Injection from Untrusted Context Variables</b></span>

<span style="font-size:1.1em;"><b>Why This Matters:</b> Protects against attackers injecting malicious commands into workflows by unsanitized inputs, such as issue titles or pull request descriptions.</span>

**Project Expectations**

<div align="center">

| Incubating | Active | Archived |
|:-----------:|:--------:|:----------:|
| E | E | N/A |

</div>


**Implementation:** [Github Docs](https://securitylab.github.com/research/github-actions-untrusted-input/)



**Sources:**
- [OpenSSF Scorecard](https://github.com/ossf/scorecard/blob/main/docs/checks.md)

**MITRE:**
- [CWE-454](https://cwe.mitre.org/data/definitions/454.html)
- [CAPEC-242](https://capec.mitre.org/data/definitions/242.html)

**OpenPathFinder:** https://openpathfinder.com/docs/checks/preventScriptInjection/

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
    <a href="../ghWorkflowSec">ghWorkflowSec</a>
  </td>
  <td>
    <a href="../cicdControls">cicdControls</a><br> >
    <a href="../ghWorkflowSec">ghWorkflowSec</a>
  </td>
</tr>
</table>

---

*Part of: [OpenJS Security Compliance Guide](../README.md)* 