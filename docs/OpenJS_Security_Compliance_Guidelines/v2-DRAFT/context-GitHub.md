# GitHub Security Guidelines

This document contains all security guidelines specific to GitHub.

## 
dependencyManagement

### Recommended

| Guideline | Title | Incubating | Active | Archived |
|-----------|-------|------------|--------|----------|
| [annualDependencyRefresh](guidelines/governance-annualDependencyRefresh.md) | Refresh Dependencies with Annual Releases | R | R | N/A |
| [appsOnlyIncludePackageLock](guidelines/freestandingApplications-appsOnlyIncludePackageLock.md) | Freestanding Apps include package-lock.json in releases | R | R | R | 

## accessGovernance

### Expected

| Guideline | Title | Incubating | Active | Archived |
|-----------|-------|------------|--------|----------|
| [ghDocRepoWriteAcces](guidelines/defineRolesAndPerms-ghDocRepoWriteAcces.md) | Define Teams/Individuals with Write Access to GitHub Repositories | E | E | E |
| [ghOrgRestrictDefaultMemberPerms](guidelines/useRBACfeatures-ghOrgRestrictDefaultMemberPerms.md) | Restrict Default GitHub Org Member Permissions | E | E | E |
| [ghOwnerContinuityPolicy](guidelines/governance-ghOwnerContinuityPolicy.md) | Configure Two or more Owners for Access Continuity | E | E | E |
| [useGhOrgs](guidelines/useRBACfeatures-useGhOrgs.md) | Manage GitHub Permissions using Organizations | N/A | N/A | N/A |

### Recommended

| Guideline | Title | Incubating | Active | Archived |
|-----------|-------|------------|--------|----------|
| [activeGhAdmins](guidelines/permsRequireActivity-activeGhAdmins.md) | Require Activity in Past 12 Months for GitHub Org Admins | R | R | N/A |
| [activeGhWriteAccess](guidelines/permsRequireActivity-activeGhWriteAccess.md) | Require Activity in Past 12 Months for GitHub Members with Write Access | R | R | N/A |
| [ghOrgOwners](guidelines/limitOwnersAndAdmins-ghOrgOwners.md) | Limit GitHub Org Owners to Fewer Than Three | R | R | R |
| [ghRepoAdmins](guidelines/limitOwnersAndAdmins-ghRepoAdmins.md) | Limit GitHub Repo Admins to Fewer Than Three | R | R | R | 

## cicdChecks

### Expected

| Guideline | Title | Incubating | Active | Archived |
|-----------|-------|------------|--------|----------|
| [checkCommits4Creds](guidelines/ciCdScanners-checkCommits4Creds.md) | Check All Commits for Credentials | E | E | N/A |
| [credsNotInProjectRepoFiles](guidelines/properCredUse-credsNotInProjectRepoFiles.md) | Credentials are not stoerd in repositories | E | E | E |
| [staticAppSecTesting](guidelines/ciCdScanners-staticAppSecTesting.md) | Use Static Application Security Testing for All Commits | E | E | N/A |

### Recommended

| Guideline | Title | Incubating | Active | Archived |
|-----------|-------|------------|--------|----------|
| [staticCodeAnalysis](guidelines/ciCdScanners-staticCodeAnalysis.md) | Use Automated Static Code Analysis Tools | R | R | N/A | 

## cicdControls

### Expected

| Guideline | Title | Incubating | Active | Archived |
|-----------|-------|------------|--------|----------|
| [adminOnlyRepoCreation](guidelines/branchProtection-adminOnlyRepoCreation.md) | Allow Only Admins to Create Public Repositories | E | E | E |
| [ghCommitChecksMustPass](guidelines/branchProtection-ghCommitChecksMustPass.md) | All Commit/PR Checks (including any Warnings) must Pass before merging | E | E | N/A |
| [ghDefaultBranchPreventDeletion](guidelines/branchProtection-ghDefaultBranchPreventDeletion.md) | Prevent Deletion of Default Branch | E | E | E |
| [ghInjectSecretsAtRuntime](guidelines/properCredUse-ghInjectSecretsAtRuntime.md) | Ensure that the secrets are injected at runtime | E | E | E |
| [ghNoArbitraryCodeInPipeline](guidelines/ghWorkflowSec-ghNoArbitraryCodeInPipeline.md) | Restrict Build Pipeline Code Execution to Build Scripts | E | E | N/A |
| [ghNoSelfHostedRunners](guidelines/ghWorkflowSec-ghNoSelfHostedRunners.md) | Disable Self-Hosted Runners in GitHub Org | E | E | E |
| [ghPinActionsWithSecrets](guidelines/ghWorkflowSec-ghPinActionsWithSecrets.md) | Pin Actions with Secrets to Full-Length Commit SHAs | D | E | E |
| [ghPreventAdminBypass](guidelines/branchProtection-ghPreventAdminBypass.md) | Prevent Admins from Bypassing Branch Protection | E | E | E |
| [ghPreventScriptInjection](guidelines/ghWorkflowSec-ghPreventScriptInjection.md) | Avoid Script Injection from Untrusted Variables | E | E | N/A |
| [ghUpToDateDefaultBranchBeforeMerge](guidelines/branchProtection-ghUpToDateDefaultBranchBeforeMerge.md) | Require Default Branch Updates Before Merging | E | E | E |
| [ghVerifiedActionsOnly](guidelines/ghWorkflowSec-ghVerifiedActionsOnly.md) | Limit GitHub Actions to Verified or Trusted Actions | E | E | N/A |

### Recommended

| Guideline | Title | Incubating | Active | Archived |
|-----------|-------|------------|--------|----------|
| [ghBlockCommitsWithCreds](guidelines/properCredUse-ghBlockCommitsWithCreds.md) | Block New Commits with Credentials | R | R | N/A |
| [ghCommitSignoffForWeb](guidelines/branchProtection-ghCommitSignoffForWeb.md) | Enforce Commit Signoff for Web-Based Commits | R | R | R |
| [ghDefaultBranchNoForcePush](guidelines/branchProtection-ghDefaultBranchNoForcePush.md) | Disable Force Push on Default Branch | R | R | N/A |
| [ghMergingRequiresPr](guidelines/branchProtection-ghMergingRequiresPr.md) | Require Pull Requests Before Merging | R | R | N/A |
| [ghRequireSignedCommits](guidelines/branchProtection-ghRequireSignedCommits.md) | Require Signed Commits | R | R | N/A | 

## cicdPermissions

### Expected

| Guideline | Title | Incubating | Active | Archived |
|-----------|-------|------------|--------|----------|
| [ghDefaultTokenPermsReadOnly](guidelines/properCredUse-ghDefaultTokenPermsReadOnly.md) | Set Default GitHub Workflow Token Permissions to Read Only | E | E | N/A |
| [ghRestrictSecretsToRepos](guidelines/properCredUse-ghRestrictSecretsToRepos.md) | Restrict GitHub Org Secrets to Specific Repositories | E | E | N/A |

### Recommended

| Guideline | Title | Incubating | Active | Archived |
|-----------|-------|------------|--------|----------|
| [ghForkWorkflowApproval](guidelines/ghWorkflowSec-ghForkWorkflowApproval.md) | Require Approval for Forked Workflow Changes | R | R | R |
| [ghOnlyJobsHaveWritePerms](guidelines/properCredUse-ghOnlyJobsHaveWritePerms.md) | Limit Workflow Write Permissions to Job-Level | R | R | N/A | 

## coordinatedDisclosure

### Expected

| Guideline | Title | Incubating | Active | Archived |
|-----------|-------|------------|--------|----------|
| [noBountyBudget](guidelines/useCvdTools-noBountyBudget.md) | Don't have a bounty budget? Use GitHub Private Vulnerability Reporting | E | E | E |

### Recommended

| Guideline | Title | Incubating | Active | Archived |
|-----------|-------|------------|--------|----------|
| [withBountyBudget](guidelines/useCvdTools-withBountyBudget.md) | Have a bounty budget? The Foundation can help with partnering. | R | R | N/A | 

## credentialMgmt

### Expected

| Guideline | Title | Incubating | Active | Archived |
|-----------|-------|------------|--------|----------|
| [ghRepoKeysHavePassphrase](guidelines/properCredUse-ghRepoKeysHavePassphrase.md) | Use SSH Keys with Passphrases for Repository Access | E | E | E |
| [ghWebhooksUseSecrets](guidelines/properCredUse-ghWebhooksUseSecrets.md) | Secure GitHub Webhooks with Secrets | E | E | E |

 

## dependencyManagement

### Expected

| Guideline | Title | Incubating | Active | Archived |
|-----------|-------|------------|--------|----------|
| [appsOnlyMmachineReadableDependencies](guidelines/freestandingApplications-appsOnlyMmachineReadableDependencies.md) | Provide Machine-Readable Dependency Lists | E | E | E |
| [depMgmtOodNoVulns](guidelines/ciCdScanners-depMgmtOodNoVulns.md) | Automate Monitoring of Outdated Dependencies | E | E | N/A |
| [depMgmtWithVulns](guidelines/ciCdScanners-depMgmtWithVulns.md) | Automate Dependency Vulnerability Identification | E | E | N/A |

 

## enforceMFAonOrgs

### Expected

| Guideline | Title | Incubating | Active | Archived |
|-----------|-------|------------|--------|----------|
| [ghOrgEnforceMFA](guidelines/enforceMFAonOrgs-ghOrgEnforceMFA.md) | Enforce MFA in GitHub Organization(s) | E | E | E |

 

## governance

### Expected

| Guideline | Title | Incubating | Active | Archived |
|-----------|-------|------------|--------|----------|
| [cicdPrePublishAutomation](guidelines/projectDocumentation-cicdPrePublishAutomation.md) | Automate Pre-Publish CI/CD Steps in Code-Based Pipelines | D | E | N/A |
| [releasesUseGitTags](guidelines/releaseDocumentation-releasesUseGitTags.md) | Use Annotated Git Release Tags | E | E | N/A |

 

## multiPartyReviews

### Recommended

| Guideline | Title | Incubating | Active | Archived |
|-----------|-------|------------|--------|----------|
| [ghCodeOwnerReviewForLargeTeams](guidelines/multiPartyReviews-ghCodeOwnerReviewForLargeTeams.md) | Require Code Owners Review for Large Projects and Teams | R | R | N/A |
| [ghRequirePrApprovals](guidelines/multiPartyReviews-ghRequirePrApprovals.md) | Require Approved PRs for Mainline Commits (Two+ Maintainers) | R | R | N/A |
| [ghTwoPartyReview](guidelines/multiPartyReviews-ghTwoPartyReview.md) | Require Two-Party Review (Two+ Maintainers) | R | R | N/A | 

## useHwOrPassKey

### Recommended

| Guideline | Title | Incubating | Active | Archived |
|-----------|-------|------------|--------|----------|
| [ghMFAUseHwKeyInteractive](guidelines/useHwOrPassKey-ghMFAUseHwKeyInteractive.md) | Use AAL2/3 Passkeys for GitHub Access | R | R | R |
| [ghMFAUseHwKeyNonInteractive](guidelines/useHwOrPassKey-ghMFAUseHwKeyNonInteractive.md) | Use AAL2/3 Passkeys for Non-Interactive GitHub Access | R | R | R | 

## usePhishingResistentMFA

### Expected

| Guideline | Title | Incubating | Active | Archived |
|-----------|-------|------------|--------|----------|
| [ghMFAphishingResistant](guidelines/usePhishingResistentMFA-ghMFAphishingResistant.md) | Do not use MFA methods vulnerable to phishing attacks | E | E | E |

  