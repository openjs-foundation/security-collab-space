<span style="font-size:0.8em;"><code>ghForkWorkflowApproval</code></span>  
# Require Approval for Forked Workflow Changes


<span style="font-size:1.15em;"><b>Limit changes from forks to workflows by requiring approval for all non collaborators</b></span>

<span style="font-size:1.1em;"><b>Why This Matters:</b> Helps prevent attackers from exploiting GitHub Actions’ elevated permissions via malicious pull requests.</span>

**Project Expectations**

<div align="center">

| Incubating | Active | Archived |
|:-----------:|:--------:|:----------:|
| R | R | R |

</div>




**Sources:**
- [Github Docs](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository)

**MITRE:**
[CAPEC-180](https://capec.mitre.org/data/definitions/180.html)

**OpenPathFinder:** https://openpathfinder.com/docs/checks/forkWorkflowApproval/

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
    <a href="../cicdPermissions">cicdPermissions</a><br> >
    <a href="../ghWorkflowSec">ghWorkflowSec</a>
  </td>
</tr>
</table>

---

*Part of: [OpenJS Security Compliance Guide](../README.md)* 