# npm Security Guidelines

This document contains all security guidelines specific to npm.

## accessGovernance

### Expected

| Guideline | Title | Incubating | Active | Archived |
|-----------|-------|------------|--------|----------|
| [useNpmOrgsTeams](guidelines/useRBACfeatures-useNpmOrgsTeams.md) | Manage npm Permissions using Organizations and Teams | E | E | E |

### Recommended

| Guideline | Title | Incubating | Active | Archived |
|-----------|-------|------------|--------|----------|
| [npmNumMembers](guidelines/limitOwnersAndAdmins-npmNumMembers.md) | Limit npm Teams to bare minimum required to publish | R | R | R |
| [npmNumOrgAdmins](guidelines/limitOwnersAndAdmins-npmNumOrgAdmins.md) | Limit npm Admins to Fewer Than Three | R | R | R |
| [npmNumOrgOwners](guidelines/limitOwnersAndAdmins-npmNumOrgOwners.md) | Limit npm Org Owners to Fewer Than Three | R | R | R | 

## cicdControls

### Expected

| Guideline | Title | Incubating | Active | Archived |
|-----------|-------|------------|--------|----------|
| [npmOnlyUseGranularAccessTokens](guidelines/properCredUse-npmOnlyUseGranularAccessTokens.md) | Use Granular Access Tokens | E | E | E |
| [npmPackagePublishingAccess](guidelines/properCredUse-npmPackagePublishingAccess.md) | Restrict Package Publishing Access | E | E | E |
| [npmUserWritesReqMFA](guidelines/configureMFA-npmUserWritesReqMFA.md) | Require MFA for User Account Writes | E | E | E |

### Recommended

| Guideline | Title | Incubating | Active | Archived |
|-----------|-------|------------|--------|----------|
| [npmPublishingWithMFA](guidelines/properCredUse-npmPublishingWithMFA.md) | Publish to npm Using MFA-Enabled Accounts | R | R | R | 

## enforceMFAonOrgs

### Expected

| Guideline | Title | Incubating | Active | Archived |
|-----------|-------|------------|--------|----------|
| [npmOrgEnforceMFA](guidelines/enforceMFAonOrgs-npmOrgEnforceMFA.md) | Enforce MFA in npm Organization(s) | E | E | E |

 

## publishingPermissions

### Expected

| Guideline | Title | Incubating | Active | Archived |
|-----------|-------|------------|--------|----------|
| [npmDocPublishAccess](guidelines/defineRolesAndPerms-npmDocPublishAccess.md) | Define Teams/Individuals with Write Access to npm Orgs, Teams, Packages | E | E | E |

 

## useHwOrPassKey

### Recommended

| Guideline | Title | Incubating | Active | Archived |
|-----------|-------|------------|--------|----------|
| [npmMFAUseHwKey](guidelines/useHwOrPassKey-npmMFAUseHwKey.md) | Use WebAuthN via a passkey (AAL2) or hardware key (AAL3) that activates using a password or biometrics | R | R | R | 

## usePhishingResistentMFA

### Expected

| Guideline | Title | Incubating | Active | Archived |
|-----------|-------|------------|--------|----------|
| [npmMFAphishingResistant](guidelines/usePhishingResistentMFA-npmMFAphishingResistant.md) | Do not use MFA methods vulnerable to phishing attacks | E | E | E |

  