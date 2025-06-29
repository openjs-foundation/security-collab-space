# OpenJS Security Compliance Guide - Hierarchy1 (Domain → Context → Guideline)

- Code Quality
  - projectDocumentation
    - [docSoftwareArchitecture](syncedToRepo/guidelines/projectDocumentation-docSoftwareArchitecture.md) - Document Software Architecture
  - securityTraining
    - [owaspTop10Training](syncedToRepo/guidelines/securityTraining-owaspTop10Training.md) - Training on OWASP Top 10 or Equivalent
    - [softwareDesignTraining](syncedToRepo/guidelines/securityTraining-softwareDesignTraining.md) - Training on Secure Software Design
  - vulnPrevention
    - [regressionTestsForVulns](syncedToRepo/guidelines/vulnPrevention-regressionTestsForVulns.md) - Create Regression Tests for Bugs and Security Vulnerabilities
- Code Review
  - multiPartyReviews
    - [ghCodeOwnerReviewForLargeTeams](syncedToRepo/guidelines/multiPartyReviews-ghCodeOwnerReviewForLargeTeams.md) - Require Code Owners Review for Large Projects and Teams
    - [ghRequirePrApprovals](syncedToRepo/guidelines/multiPartyReviews-ghRequirePrApprovals.md) - Require Approved PRs for Mainline Commits (Two+ Maintainers)
    - [ghTwoPartyReview](syncedToRepo/guidelines/multiPartyReviews-ghTwoPartyReview.md) - Require Two-Party Review (Two+ Maintainers)
- Coordinated Vulnerability Disclosure
  - governance
    - [docIncidentResponsePlan](syncedToRepo/guidelines/governance-docIncidentResponsePlan.md) - Define Clear Communication and Incident Response Plans
    - [securityPolicyMeetsStandards](syncedToRepo/guidelines/governance-securityPolicyMeetsStandards.md) - Ensure Security.md Meets OpenJS CVD Guidelines
  - releaseDocumentation
    - [assignCVEForKnownVulns](syncedToRepo/guidelines/releaseDocumentation-assignCVEForKnownVulns.md) - Assign CVEs to All Known Security Vulnerabilities
    - [includeCVEInReleaseNotes](syncedToRepo/guidelines/releaseDocumentation-includeCVEInReleaseNotes.md) - Include CVE IDs for security fixes in changelogs and Release Notes
  - useCvdTools
    - [noBountyBudget](syncedToRepo/guidelines/useCvdTools-noBountyBudget.md) - Don't have a bounty budget? Use GitHub Private Vulnerability Reporting
    - [withBountyBudget](syncedToRepo/guidelines/useCvdTools-withBountyBudget.md) - Have a bounty budget? The Foundation can help with partnering.
- Dependencies
  - ciCdScanners
    - [depMgmtOodNoVulns](syncedToRepo/guidelines/ciCdScanners-depMgmtOodNoVulns.md) - Automate Monitoring of Outdated Dependencies
    - [depMgmtWithVulns](syncedToRepo/guidelines/ciCdScanners-depMgmtWithVulns.md) - Automate Dependency Vulnerability Identification
  - freestandingApplications
    - [appsOnlyIncludePackageLock](syncedToRepo/guidelines/freestandingApplications-appsOnlyIncludePackageLock.md) - Freestanding Apps include package-lock.json in releases
    - [appsOnlyMmachineReadableDependencies](syncedToRepo/guidelines/freestandingApplications-appsOnlyMmachineReadableDependencies.md) - Provide Machine-Readable Dependency Lists
  - ghWorkflowSec
    - [ghPinActionsWithSecrets](syncedToRepo/guidelines/ghWorkflowSec-ghPinActionsWithSecrets.md) - Pin Actions with Secrets to Full-Length Commit SHAs
    - [ghVerifiedActionsOnly](syncedToRepo/guidelines/ghWorkflowSec-ghVerifiedActionsOnly.md) - Limit GitHub Actions to Verified or Trusted Actions
  - governance
    - [annualDependencyRefresh](syncedToRepo/guidelines/governance-annualDependencyRefresh.md) - Refresh Dependencies with Annual Releases
  - projectDocumentation
    - [docModifiedProjectDeps](syncedToRepo/guidelines/projectDocumentation-docModifiedProjectDeps.md) - Uniquely Identify Modified Dependencies
- Service Authentication
  - properCredUse
    - [credsNotInProjectRepoFiles](syncedToRepo/guidelines/properCredUse-credsNotInProjectRepoFiles.md) - Credentials are not stoerd in repositories
    - [ghInjectSecretsAtRuntime](syncedToRepo/guidelines/properCredUse-ghInjectSecretsAtRuntime.md) - Ensure that the secrets are injected at runtime
    - [ghWebhooksUseSecrets](syncedToRepo/guidelines/properCredUse-ghWebhooksUseSecrets.md) - Secure GitHub Webhooks with Secrets
    - [npmOnlyUseGranularAccessTokens](syncedToRepo/guidelines/properCredUse-npmOnlyUseGranularAccessTokens.md) - Use Granular Access Tokens
    - [npmPackagePublishingAccess](syncedToRepo/guidelines/properCredUse-npmPackagePublishingAccess.md) - Restrict Package Publishing Access
- Service Authorization
  - properCredUse
    - [ghDefaultTokenPermsReadOnly](syncedToRepo/guidelines/properCredUse-ghDefaultTokenPermsReadOnly.md) - Set Default GitHub Workflow Token Permissions to Read Only
    - [ghOnlyJobsHaveWritePerms](syncedToRepo/guidelines/properCredUse-ghOnlyJobsHaveWritePerms.md) - Limit Workflow Write Permissions to Job-Level
    - [ghRestrictSecretsToRepos](syncedToRepo/guidelines/properCredUse-ghRestrictSecretsToRepos.md) - Restrict GitHub Org Secrets to Specific Repositories
- Source Control
  - branchProtection
    - [ghCommitChecksMustPass](syncedToRepo/guidelines/branchProtection-ghCommitChecksMustPass.md) - All Commit/PR Checks (including any Warnings) must Pass before merging
    - [ghCommitSignoffForWeb](syncedToRepo/guidelines/branchProtection-ghCommitSignoffForWeb.md) - Enforce Commit Signoff for Web-Based Commits
    - [ghDefaultBranchNoForcePush](syncedToRepo/guidelines/branchProtection-ghDefaultBranchNoForcePush.md) - Disable Force Push on Default Branch
    - [ghDefaultBranchPreventDeletion](syncedToRepo/guidelines/branchProtection-ghDefaultBranchPreventDeletion.md) - Prevent Deletion of Default Branch
    - [ghMergingRequiresPr](syncedToRepo/guidelines/branchProtection-ghMergingRequiresPr.md) - Require Pull Requests Before Merging
    - [ghRequireSignedCommits](syncedToRepo/guidelines/branchProtection-ghRequireSignedCommits.md) - Require Signed Commits
    - [ghUpToDateDefaultBranchBeforeMerge](syncedToRepo/guidelines/branchProtection-ghUpToDateDefaultBranchBeforeMerge.md) - Require Default Branch Updates Before Merging
  - ciCdScanners
    - [checkCommits4Creds](syncedToRepo/guidelines/ciCdScanners-checkCommits4Creds.md) - Check All Commits for Credentials
    - [staticAppSecTesting](syncedToRepo/guidelines/ciCdScanners-staticAppSecTesting.md) - Use Static Application Security Testing for All Commits
    - [staticCodeAnalysis](syncedToRepo/guidelines/ciCdScanners-staticCodeAnalysis.md) - Use Automated Static Code Analysis Tools
  - ghWorkflowSec
    - [ghForkWorkflowApproval](syncedToRepo/guidelines/ghWorkflowSec-ghForkWorkflowApproval.md) - Require Approval for Forked Workflow Changes
    - [ghNoArbitraryCodeInPipeline](syncedToRepo/guidelines/ghWorkflowSec-ghNoArbitraryCodeInPipeline.md) - Restrict Build Pipeline Code Execution to Build Scripts
    - [ghNoSelfHostedRunners](syncedToRepo/guidelines/ghWorkflowSec-ghNoSelfHostedRunners.md) - Disable Self-Hosted Runners in GitHub Org
    - [ghPreventScriptInjection](syncedToRepo/guidelines/ghWorkflowSec-ghPreventScriptInjection.md) - Avoid Script Injection from Untrusted Variables
  - projectDocumentation
    - [cicdPrePublishAutomation](syncedToRepo/guidelines/projectDocumentation-cicdPrePublishAutomation.md) - Automate Pre-Publish CI/CD Steps in Code-Based Pipelines
  - properCredUse
    - [ghBlockCommitsWithCreds](syncedToRepo/guidelines/properCredUse-ghBlockCommitsWithCreds.md) - Block New Commits with Credentials
  - releaseDocumentation
    - [releasesUseGitTags](syncedToRepo/guidelines/releaseDocumentation-releasesUseGitTags.md) - Use Annotated Git Release Tags
- User Account Permissions
  - branchProtection
    - [adminOnlyRepoCreation](syncedToRepo/guidelines/branchProtection-adminOnlyRepoCreation.md) - Allow Only Admins to Create Public Repositories
    - [ghPreventAdminBypass](syncedToRepo/guidelines/branchProtection-ghPreventAdminBypass.md) - Prevent Admins from Bypassing Branch Protection
  - defineRolesAndPerms
    - [ghDocRepoWriteAcces](syncedToRepo/guidelines/defineRolesAndPerms-ghDocRepoWriteAcces.md) - Define Teams/Individuals with Write Access to GitHub Repositories
    - [npmDocPublishAccess](syncedToRepo/guidelines/defineRolesAndPerms-npmDocPublishAccess.md) - Define Teams/Individuals with Write Access to npm Orgs, Teams, Packages
  - governance
    - [ghOwnerContinuityPolicy](syncedToRepo/guidelines/governance-ghOwnerContinuityPolicy.md) - Configure Two or more Owners for Access Continuity
  - limitOwnersAndAdmins
    - [ghOrgOwners](syncedToRepo/guidelines/limitOwnersAndAdmins-ghOrgOwners.md) - Limit GitHub Org Owners to Fewer Than Three
    - [ghRepoAdmins](syncedToRepo/guidelines/limitOwnersAndAdmins-ghRepoAdmins.md) - Limit GitHub Repo Admins to Fewer Than Three
    - [npmNumMembers](syncedToRepo/guidelines/limitOwnersAndAdmins-npmNumMembers.md) - Limit npm Teams to bare minimum required to publish
    - [npmNumOrgAdmins](syncedToRepo/guidelines/limitOwnersAndAdmins-npmNumOrgAdmins.md) - Limit npm Admins to Fewer Than Three
    - [npmNumOrgOwners](syncedToRepo/guidelines/limitOwnersAndAdmins-npmNumOrgOwners.md) - Limit npm Org Owners to Fewer Than Three
  - permsRequireActivity
    - [activeGhAdmins](syncedToRepo/guidelines/permsRequireActivity-activeGhAdmins.md) - Require Activity in Past 12 Months for GitHub Org Admins
    - [activeGhWriteAccess](syncedToRepo/guidelines/permsRequireActivity-activeGhWriteAccess.md) - Require Activity in Past 12 Months for GitHub Members with Write Access
  - properCredUse
    - [npmPublishingWithMFA](syncedToRepo/guidelines/properCredUse-npmPublishingWithMFA.md) - Publish to npm Using MFA-Enabled Accounts
  - useRBACfeatures
    - [ghOrgRestrictDefaultMemberPerms](syncedToRepo/guidelines/useRBACfeatures-ghOrgRestrictDefaultMemberPerms.md) - Restrict Default GitHub Org Member Permissions
    - [useGhOrgs](syncedToRepo/guidelines/useRBACfeatures-useGhOrgs.md) - Manage GitHub Permissions using Organizations
    - [useNpmOrgsTeams](syncedToRepo/guidelines/useRBACfeatures-useNpmOrgsTeams.md) - Manage npm Permissions using Organizations and Teams
- User Authentication
  - configureMFA
    - [npmUserWritesReqMFA](syncedToRepo/guidelines/configureMFA-npmUserWritesReqMFA.md) - Require MFA for User Account Writes
  - enforceMFAonOrgs
    - [ghOrgEnforceMFA](syncedToRepo/guidelines/enforceMFAonOrgs-ghOrgEnforceMFA.md) - Enforce MFA in GitHub Organization(s)
    - [npmOrgEnforceMFA](syncedToRepo/guidelines/enforceMFAonOrgs-npmOrgEnforceMFA.md) - Enforce MFA in npm Organization(s)
  - properCredUse
    - [ghRepoKeysHavePassphrase](syncedToRepo/guidelines/properCredUse-ghRepoKeysHavePassphrase.md) - Use SSH Keys with Passphrases for Repository Access
  - useHwOrPassKey
    - [ghMFAUseHwKeyInteractive](syncedToRepo/guidelines/useHwOrPassKey-ghMFAUseHwKeyInteractive.md) - Use AAL2/3 Passkeys for GitHub Access
    - [ghMFAUseHwKeyNonInteractive](syncedToRepo/guidelines/useHwOrPassKey-ghMFAUseHwKeyNonInteractive.md) - Use AAL2/3 Passkeys for Non-Interactive GitHub Access
    - [npmMFAUseHwKey](syncedToRepo/guidelines/useHwOrPassKey-npmMFAUseHwKey.md) - Use WebAuthN via a passkey (AAL2) or hardware key (AAL3) that activates using a password or biometrics
  - usePhishingResistentMFA
    - [ghMFAphishingResistant](syncedToRepo/guidelines/usePhishingResistentMFA-ghMFAphishingResistant.md) - Do not use MFA methods vulnerable to phishing attacks
    - [npmMFAphishingResistant](syncedToRepo/guidelines/usePhishingResistentMFA-npmMFAphishingResistant.md) - Do not use MFA methods vulnerable to phishing attacks
- Vulnerability Management
  - projectDocumentation
    - [upgradePathsForOlderReleases](syncedToRepo/guidelines/projectDocumentation-upgradePathsForOlderReleases.md) - Support Older Versions or Provide Upgrade Paths
  - vulnRemediationTimelines
    - [criticalVulns30Days](syncedToRepo/guidelines/vulnRemediationTimelines-criticalVulns30Days.md) - Patch Actively Exploited Critical Vulnerabilities within 30 Days
    - [exploitableHighCritVulns14Days](syncedToRepo/guidelines/vulnRemediationTimelines-exploitableHighCritVulns14Days.md) - Patch Critical/High Vulnerabilities in 14 Days
    - [exploitableNonCritVulns60Days](syncedToRepo/guidelines/vulnRemediationTimelines-exploitableNonCritVulns60Days.md) - Patch Non-Critical Vulnerabilities in 60 Days
    - [nonCriticalVulns90Days](syncedToRepo/guidelines/vulnRemediationTimelines-nonCriticalVulns90Days.md) - Patch Non-Critical Vulnerabilities within 90 Days
    - [respond14Days](syncedToRepo/guidelines/vulnRemediationTimelines-respond14Days.md) - Respond to External Vulnerability Reports in Under 14 Days
