<span style="font-size:0.8em;"><code>ghOnlyJobsHaveWritePerms</code></span>  
# Limit Workflow Write Permissions to Job-Level


<span style="font-size:1.15em;"><b>Only Allow Workflows Write Permissions at the Job-Level</b></span>

<span style="font-size:1.1em;"><b>Why This Matters:</b> Limiting write permissions to specific jobs minimizes the impact of a compromised step and follows the principle of least privilege.</span>

**Project Expectations**

<div align="center">

| Incubating | Active | Archived |
|:-----------:|:--------:|:----------:|
| R | R | N/A |

</div>


**Implementation:** [Github Docs](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions)



**Sources:**
- [OpenSSF Scorecard](https://github.com/ossf/scorecard/blob/main/docs/checks.md)
- [OpenSSF SCM Best Practices](https://github.com/ossf/scorecard/blob/main/docs/checks.md)

**MITRE:**
- [CWE-250](https://cwe.mitre.org/data/definitions/250.html)
- [CAPEC-69](https://capec.mitre.org/data/definitions/69.html)

**OpenPathFinder:** https://openpathfinder.com/docs/checks/limitWorkflowWritePermissions/

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