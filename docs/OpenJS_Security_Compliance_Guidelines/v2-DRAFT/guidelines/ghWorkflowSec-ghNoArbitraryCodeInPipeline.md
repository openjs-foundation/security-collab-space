<span style="font-size:0.8em;"><code>ghNoArbitraryCodeInPipeline</code></span>  
# Restrict Build Pipeline Code Execution to Build Scripts


<span style="font-size:1.15em;"><b>Build Pipeline Cannot Execute Arbitrary Code from Outside of a Build Script</b></span>

<span style="font-size:1.1em;"><b>Why This Matters:</b> Preventing the execution of arbitrary code in build pipelines mitigates risks from compromised pull requests or dependencies.</span>

**Project Expectations**

<div align="center">

| Incubating | Active | Archived |
|:-----------:|:--------:|:----------:|
| E | E | N/A |

</div>




**Sources:**
- [OpenSSF Scorecard](https://github.com/ossf/scorecard/blob/main/docs/checks.md)

**MITRE:**
- [CWE-94](https://cwe.mitre.org/data/definitions/94.html)
- [CAPEC-19](https://capec.mitre.org/data/definitions/19.html)

**OpenPathFinder:** https://openpathfinder.com/docs/checks/noArbitraryCodeInPipeline/

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