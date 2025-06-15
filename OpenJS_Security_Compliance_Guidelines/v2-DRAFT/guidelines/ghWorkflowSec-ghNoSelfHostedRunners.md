<span style="font-size:0.8em;"><code>ghNoSelfHostedRunners</code></span>  
# Disable Self-Hosted Runners in GitHub Org


<span style="font-size:1.15em;"><b>Disable use of Self-Hosted Runners in Github Org</b></span>

<span style="font-size:1.1em;"><b>Why This Matters:</b> A random, ephemeral runner reduces the risk of compromise from inadequately managed self-hosted runners.</span>

**Project Expectations**

<div align="center">

| Incubating | Active | Archived |
|:-----------:|:--------:|:----------:|
| E | E | E |

</div>


**Implementation:** [Github Docs](https://docs.github.com/en/organizations/managing-organization-settings/disabling-or-limiting-github-actions-for-your-organization)



**Sources:**
- [Github Action Hardening Docs](https://docs.github.com/en/actions/security-guides/security-hardening-for-github-actions)

**MITRE:**
[CAPEC-439](https://capec.mitre.org/data/definitions/439.html)

**OpenPathFinder:** https://openpathfinder.com/docs/checks/noSelfHostedRunners/

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