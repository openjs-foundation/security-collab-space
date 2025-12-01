# Secure Releases Guide 2.0

## Introduction

This guide was developed by OpenJS Foundation Security Collab Space to provide security best practice insights and recommendations for JavaScript project maintainers using the npm package manager. Also included are brief overviews and examples of the threats npm’s various security features are designed to defend against.

> [!IMPORTANT]
> This guide directly inspired by, borrows from, and is intended to ultimately feed updates into the [npm Best Practices Guide v1.1](https://github.com/ossf/package-manager-best-practices/blob/main/published/npm.md) (last updated September 2022) by OSSF's [Best Practices for Open Source Developers](https://github.com/ossf/wg-best-practices-os-developers) Working Group.

This document is being developed incrementally, section by section. The first three sections of this updated guide are:

* **User Account & MFA Best Practices**
* **Access Token Best Practices**
* **Permissions Management Best Practices**

## How to use this guide

Throughout this guide are direct references to the official npm documentation to achieve these recommendations and relevant OpenJS Security Compliance Guidelines for OpenJS hosted projects. This guide is intended to complement the official npm documentation, not to be an alternative.

As guidance can differ between different kinds of JavaScript projects, this guide organizes projects into three types:

* **Libraries:** These are projects published on the npm registry and consumed by other projects in the form of API calls. (Their manifest file typically contains a main, exports, browser, module, and/or types entry).
* **Standalone CLIs:** These are projects published on the npm registry and consumed by end-users in the form of locally installed programs that are always run stand-alone via npx or via a global install. An example would be clipboard-cli. (Their manifest file contains a bin entry).
* **Applications:** These are projects that teams collaborate on in development and deployment, such as websites and/or web applications. An example would be a React web app for a company's user-facing SaaS. (Their manifest file typically contains "private": true).

## Relevant Threats

Since npm [introduced support for 2FA in 2022](https://github.blog/news-insights/product-news/introducing-even-more-security-enhancements-to-npm/), package hijacking via account compromise continues to be a common threat to npm package maintainers. The root causes of these attacks include:

* ### Not monitoring for and rotating compromised passwords

[Credential stuffing attacks](https://en.wikipedia.org/wiki/Credential_stuffing) occur due to password re-use across multiple services. When one service is compromised, the email addresses and passwords can be used against other services that may have the same email address and password. This attack is particularly dangerous when not using MFA. Services like [haveibeenowned.com](https://haveibeenpwned.com/) help you identify passwords that may be vulnerable to credential stuffing.

* ### Not using Multi-Factor Authentication (MFA)

Failure to enforce MFA on maintainers the lack of MFA support for most npm Access Tokens, including modern Granular Access Tokens (GATs), enables compromise such as the [gluestack-ui package hijacking](https://thehackernews.com/2025/06/new-supply-chain-malware-operation-hits.html). Not using MFA enables successful credential stuffing attacks that re-use passwords across multiple services.

* ### Not using *phishing-resistant* MFA

Two major types of modern phishing attacks attack the human’s understanding and use of the MFA process. The best way to defend against these MFA attacks is to use FIDO2 [WebAuthN](https://webauthn.guide/)-based authentication such as Passkeys, which is a modern, “password-less” authentication method tied to a device or hosted keychain.

* An increasingly common type is an Attacker-in-the-Middle attack where an attacker convinces a user to provide the attacker a one-time-password (OTP) thinking they are on an authentic website when it is actually a site hosted by an attacker. The attacker then uses the OTP on the legitimate site, which happened in the [web3.js package hijacking](https://www.anza.xyz/blog/web3-js-exploit-root-cause-analysis).
* Another type are fatigue attacks that get users to visit fake password reset websites and approve push-based MFA prompts that they didn’t send. This happened during a [large attack on Apple accounts](https://krebsonsecurity.com/2024/03/recent-mfa-bombing-attacks-targeting-apple-users/).

* ### Expired maintainer custom email domains

When maintainers use a custom email domain and allow it to expire, any accounts associated with that email domain can be taken over by an attacker who purchases the domain and sets up an email address that matches the maintainer’s. Researchers [continue](https://thehackernews.com/2023/02/researchers-hijack-popular-npm-package.html) to [demonstrate](https://jfrog.com/blog/npm-package-hijacking-through-domain-takeover-how-bad-is-this-new-attack) the potential for this attack.

* ### Maintainer device compromise

Maintainer laptops, phones, and tablets that are compromised by another means can expose credentials through keyboard logging, reading unprotected files that contain credentials (eg: GitHub ssh keys, .npmrc files). Storing Passkeys in the Apple Secure Enclave, Windows Hello TPM, and various Android system on a chip equivalents is the best protection against this attack.

# Best Practices

## User Account & MFA Best Practices

**Recommendations Summary**

* User Accounts: Enable and configure MFA using Passkeys
* User Accounts: Only store MFA recovery codes on paper or using an airgap
* User Accounts: Track maintainer custom email domain expiration dates
* Organizations: Require members use MFA
* Packages: Require MFA & enable/disable Access Tokens for publishing

**Relevant npm Features**

* User Accounts
* Access Tokens
* Organizations
* Packages

---
### User Accounts: Enable and configure MFA using Passkeys

* Select *Enable 2FA* in your user account’s profile
* *Choose Security key* as your 2FA method
* Set *Require 2FA* to *Authorization and writes*

*Why only use Passkeys that require a physical presence as your 2FA Method?*

SMS and app-based MFA methods are vulnerable to theft by malicious actors if the maintainer’s device(s) or mobile phone account are compromised. Passkeys that perform a biometric check or require a physical presence like Yubikeys, Apple TouchID/FaceID, and Windows Hello provide the best current defense for this. Storing Passkeys in a cloud-based service rather than a physical token or a single device’s secure enclave is only recommended with the use of a biometric check.

Why *Require 2FA* to *Authorization and writes?*

This setting forces an MFA check when a user account attempts to perform a sensitive action, which protects against Session Hijacking attacks.

**References**

* [npm Docs: Threats and Mitigations: Compromised Passwords](https://docs.npmjs.com/threats-and-mitigations#by-compromising-passwords)
* [npm Docs: Configuring Two-Factor Authentication](https://docs.npmjs.com/configuring-two-factor-authentication)
* [npm Docs: Access npm using 2FA](https://docs.npmjs.com/accessing-npm-using-2fa)
* [npm Docs: About 2FA Authorization and Writes](https://docs.npmjs.com/about-two-factor-authentication#authorization-and-writes)
* [OpenSSF Great MFA Project](https://github.com/ossf/great-mfa-project/tree/main?tab=readme-ov-file)
* [The WebAuthN Guide](https://webauthn.guide/)

---
### User Accounts: Only store MFA recovery codes on paper or using an airgap

MFA recovery codes can be used to circumvent established MFA methods and thus should never be stored on an Internet-accessible device or service in the event a maintainer’s device is compromised. Printing out recovery codes remains the best method for protecting recovery codes. A digital airgap alternative is to use a thumb drive that is only ever used for that purpose.

> [!TIP]
> To not lose track of your MFA recovery codes, consider storing them with your other vital records (eg: birth certificates, deeds).

*Why not use npm’s GitHub or Twitter account recovery options?*

If a maintainer’s device(s) or email account(s) are compromised, these recovery options could allow an attacker to reset MFA on the maintainer’s npm account.

---
### User Accounts: Track maintainer custom email domain expiration dates

* Capture custom email domain expiration dates in a way that best suits the project’s governance.
* Begin active tracking of domain expiration dates no less than four weeks from expiration.

*Why track custom email domain expirations?*

Maintainers whose accounts are associated with a custom email domain introduce the risk of their npm account being taken over by a malicious actor if their custom email domain registration expires.

After the domain registration expires, a malicious actor can purchase the domain and then create an account with the same email address as the maintainer. The attacker can then use built-in account recovery processes on accounts across various services that are associated with that email address.

**References:**

* [npm Docs: Recovering your 2FA-enabled Account](https://docs.npmjs.com/recovering-your-2fa-enabled-account)
* [npm Docs: Threats and Mitigations: Custom Email Domain Expiration](https://docs.npmjs.com/threats-and-mitigations#by-registering-an-expired-email-domain)

---
### Organizations: Require members use MFA

By using npm Organizations, package owners can require other maintainers to enable MFA on their own user accounts.

> [!TIP]
> We recommend using npm Organizations to manage maintainer permissions in npm. Organizations are discussed further under Permissions Best Practices.

* For each npm Organization, select *Enable 2FA Enforcement*

**Reference:** [npm Docs: Requiring two-factor authentication in your organization](https://docs.npmjs.com/requiring-two-factor-authentication-in-your-organization)

---
### Packages: Require MFA & enable/disable Access Tokens for publishing

Regardless of whether a project uses an npm Organization or not, *Publishing Access* must be configured for each package in the project. If a project isn’t using an Organization, this setting is used to enforce MFA on other users when they attempt to Publish the package. If a project is not using automation, *Publishing Access* is also used to disable support for Access Tokens when publishing the package.

* If **not** using Access Tokens…
  * Set *Publishing Access* for each package to *Require 2FA and Disable Tokens*
* If using Access Tokens…
  * *Set Publishing Access for each package to Require two-factor authentication OR Single factor automation tokens OR Single factor granular access tokens*

**Reference:** [npm Docs: Requiring 2FA for package publishing and settings modification](https://docs.npmjs.com/requiring-2fa-for-package-publishing-and-settings-modification)

## Access Token Best Practices

**Recommendations Summary**

* Access Tokens: When to use Granular Access Tokens and Legacy Publish Tokens
* Access Tokens: Using and cleaning up after npm login
* Access Tokens: Avoid creating users or access tokens using npm token or npm adduser
* Access Tokens: Create separate Granular Access Tokens for each package
* Access Tokens: Set Granular Access Tokens to expire after no more than two years
* Access Tokens: Set IP Restrictions (when feasible)
* Access Tokens: Securely transfer, store, and use Access Tokens
* Access Tokens: Emergency access removal and Token revocation

**Relevant npm Features**

* Access Tokens
* npm login
* npm logout
* npm token
* npm config

---
###  Access Tokens: When to use Granular Access Tokens and Legacy Publish Tokens

npm Access Tokens are extensions of an individual user account and run as that account. npm supports two types of access tokens: Legacy Access Tokens (which include Read-Only, Automation, and Publish tokens) and newer Granular Access Tokens (GATs).

npm recommends:

* For automation: migrate from using Legacy Automation Tokens to using GATs
* For local CPI: continue using Legacy Publish Tokens (which are generated by npm login).

*Why not use Legacy Automation Tokens?*

Legacy Automation and Publish Tokens run with *all* of the permissions of the user’s account making them inherently over-permissioned for the task and violating the principle of least privilege. GATs, on the other hand, can be limited to specific packages and scopes, configured to expire, and restricted by IP ranges.

*Why still use Legacy Publish Tokens for local CLI?*

Despite being over-permissioned, Legacy Publish Tokens are recommended for local CLI because they support npm’s web-based 2FA check, while GATs do not. This 2FA check (when enabled) reduces the value of Publish Tokens stored in the ~/.npmrc file on the local disk if the host is compromised.

Because npm does not support 2FA checks for GATs, these must always be securely stored in a tool that requires passing a MFA check before granting the user access to the GAT.

**References**

* [npm Docs: Securing Your Token](https://docs.npmjs.com/using-private-packages-in-a-ci-cd-workflow#securing-your-token)

---
### Access Tokens: Using and cleaning up after npm login

Although npm recommends only using Granular Access Tokens (GATs), each time  npm login is used, the npm CLI automatically creates a new Legacy Publish Token and stores it in your local, per-user ~/.npmrc file.

> [!WARNING]
> Whenever npm login is run, it writes the newly created Legacy Publish Token to the per-user ~/.npmrc. It will always overwrite any other access token that was already present in the file for that registry.

These newly created Legacy Publish tokens created by npm login are NOT revoked when running npm logout. These tokens must be manually revoked and cleaned up.

* Revoke in npm using the [npmjs.com](http://npmjs.com) GUI or npm token list and npm token delete
* Clean up your local ~/.npmrc file

See [Securely store and use access tokens](#access-tokens:-securely-transfer,-store,-and-use-access-tokens) (below) for how to safely and securely use GATs with the npm CLI.

**References**

* [npm Docs: About Access Tokens](https://docs.npmjs.com/about-access-tokens)
* [npm Docs: npm login](https://docs.npmjs.com/cli/v9/commands/npm-login)
* [npm Docs: npm logout](https://docs.npmjs.com/cli/v9/commands/npm-logout)

---
### Access Tokens: Avoid creating users or access tokens using npm token or npm adduser

The npm CLI does not support creating Granular Access Tokens (GATs). GATs can only be created using the npmjs.com GUI. The following commands create Legacy Tokens that are added to the user’s local ~/.npmrc file:

* npm token create
* npm adduser

**References**

* [npm Docs: About Access Tokens](https://docs.npmjs.com/about-access-tokens)
* [npm Docs: Creating Granular Access Tokens on the website](https://docs.npmjs.com/creating-and-viewing-access-tokens#creating-granular-access-tokens-on-the-website)

---
### Access Tokens: Have separate Granular Access Tokens for each package/scope

npm recommends the use of Granular Access Tokens (GATs) because, unlike Legacy Tokens, they can be limited to a specific scope or package. Creating separate access tokens for each scope, package, and organization reduces the potential damage of a compromised token.

* *When creating a GAT that needs write/publish permissions to a package*, restrict it to a specific scope or package during its creation in the [npmjs.com](http://npmjs.com) GUI.
* *When creating a GAT to manage an npm Organization*, restrict it to a specific Organization. This does not grant the token write or publish rights to the scopes or packages in the Organization. Tokens with write permissions to an Organization should not be given permissions to packages.

Be sure to give each GAT a highly descriptive name, including the user’s name and the GAT’s package/scope, permission level, and purpose to ease future management and auditing.

**References**

* [npm Docs: About Access Tokens](https://docs.npmjs.com/about-access-tokens)
* [npm Docs: Creating Granular Access Tokens on the website](https://docs.npmjs.com/creating-and-viewing-access-tokens#creating-granular-access-tokens-on-the-website)

---
### Access Tokens: Set Granular Access Tokens to expire after no more than two years

npm recommends the use of Granular Access Tokens (GATs) because, unlike Legacy Tokens, they can be set to expire. Configuring access tokens is a best practice to ensure credentials are routinely rotated to limit the long-term risks of token compromise not being detected.

* Industry standard best practices are to rotate access tokens and certificates annually.
* Given the potential effort of rotating a large number of tokens, open source projects should automatically expire and create new access tokens at least every two years.

**References**

* [npm Docs: About Access Tokens](https://docs.npmjs.com/about-access-tokens)
* [npm Docs: Creating Granular Access Tokens on the website](https://docs.npmjs.com/creating-and-viewing-access-tokens#creating-granular-access-tokens-on-the-website)

---
### Access Tokens: Set IP Restrictions (when feasible)

npm recommends the use of Granular Access Tokens (GATs) because, unlike Legacy Tokens, they can be restricted to specific source IP addresses and ranges. Configuring this limits the IP addresses that npm will allow a token to be used from.

*GAT IP restrictions when using GitHub Actions*

It is not feasible to configure an IP restriction for a GAT used on a free, standard GitHub Action runner available to public repositories. The [potential IP address ranges](https://api.github.com/meta) of standard runners are too large and change too frequently to manage as a static allowlist for a GAT.

Larger GitHub runners can be configured with a static IP address that can be used in a GAT IP allowlist. However, larger runners are only available to GitHub Organizations with paid GitHub Team or Enterprise Cloud licenses.

*GAT IP restrictions for always-on infrastructure and local use*

If the GAT is intended to be used on always-on infrastructure, it is recommended to configure a static IP in that environment so that the GAT(s) used there can be configured with an IP restriction. Depending on the individual user’s method of accessing the Internet, they may also be using one or more IP addresses that can be configured.

**References**

* [GitHub Docs: GitHub’s IP addresses](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/about-githubs-ip-addresses)
* [GitHub Docs: About GitHub-hosted runners](https://docs.github.com/en/actions/using-github-hosted-runners/using-github-hosted-runners/about-github-hosted-runners)
* [GitHub Docs: About larger GitHub runners](https://docs.github.com/en/actions/using-github-hosted-runners/using-larger-runners/about-larger-runners)
* [npm Docs: Creating Granular Access Tokens on the website](https://docs.npmjs.com/creating-and-viewing-access-tokens#creating-granular-access-tokens-on-the-website)

---
### Access Tokens: Securely transfer, store, and use Access Tokens

Granular Access Tokens (GATs) are a credential representing the user who generated the token, but do not support an MFA check within npm. Just like a password, GATs should never be stored in source code or configuration files. Access to GATs should be restricted to only those who absolutely need it.

*Safe Transfer of Access Tokens*

**DO NOT**

* Transfer access tokens using end-to-end encrypted (non-E2EE)
* Copy access tokens or recovery codes into your clipboard (especially on Linux and Windows)
* Print out access tokens or recovery codes using a printer that does not belong to you (such as a work printer)

**DO**

* Transfer access tokens using end-to-end encrypted channels
* Encrypt the file using GPG and then transferring using a non-E2EE method.

*Safe Storage and Use of Access Tokens*

The npm CLI uses the .npmrc file for configuration. Included in this file is the _AuthToken variable, which npm uses to authenticate to the public registry or a private registry. npm’s decision to store access tokens in a plain text file is inherently unsafe and additional measures must be taken to properly use and store it.

```
; Public npm registry example  
//registry.npmjs.org/:_authToken={NPM_ACCESS_TOKEN}  
; Private registry example  
//private_registry_domain.tld/:_authToken={PRIVATE_REGISTRY_ACCESS_TOKEN}
```

There are four different types of .npmrc files. Two types are discussed below: 1) Per-project .npmrc config files with GitHub Actions and 2) Per-user .npmrc files on an individual workstation.

1) **Using per-project .npmrc config files with GitHub Actions**

To safely store and use a GAT with GitHub Actions:

* Store it as a GitHub Actions Secret in the repository that will use it.
* Have GitHub Actions share the secret as an environment variable (eg: {NPM_ACCESS_TOKEN})
* Use the {NPM_ACCESS_TOKEN} variable in the project’s .npmrc file to populate _AuthToken.
* If the GAT is stored in the GitHub Organization, restrict access to only the repositories that need it.

Remember that all members granted Write access to a repository with a GitHub Action Secret (stored either in the repository or in the GitHub Organization) will be able to access the GAT. For this reason, write permissions to a repository should be tightly controlled.

2) **Using per-user ~/.npmrc config files on an individual workstation**

This scenario has many potential approaches. First, use the correct access token for the job:

* GATs should only be stored in tools that require a MFA check before granting access to the token
* Legacy Publish Tokens (with 2FA enabled) should be used if the token must be stored in.npmrc

*How to protect a .npmrc file containing 2FA-compatible Legacy Publish Tokens*

* Add .npmrc to .gitignore to avoid committing credentials to source repositories

`echo ".npmrc" >> .gitignore`

* Block all access to.npmrc except for your local user

With default file system permissions, other users on a shared system may be able to read the token in the .npmrc file. Backup processes might also copy files with default permissions.

| Operating System | POSIX-Compliant (eg: Linux, macOS) | Windows and WSL on Windows File System |
| :---- | :---- | :---- |
| **Set File Permissions** | `Gibson> chmod 600 ~/.npmrc` | `cmd> icacls %USERPROFILE%.npmrc /inheritance:r /grant:r %USERNAME%:F` |
| **Verify File Permissions** | `Gibson> ls -la ~/.npmrc`<br>`-rw------- 1 user group size  01 Jan 70 00:01 .npmrc` | `cmd> icacls %USERPROFILE%.npmrc`<br>`​​C:\Users\userProfile\.npmrc userProfile:(F)` |
| **Explanation** | The 600 represents octal permissions:<br>`6 (owner)`: Read (4) + Write (2) = 6<br>`0 (group)`: No permissions<br>`0(others)`: No permissions | `/inheritance:r` - Removes inherited permissions<br>`/grant:r` - Grants permissions (replacing existing ones)<br>`%USERNAME%:F` - Gives Full control to current user |

If using a GAT, ensure it’s stored in a secure vault, such as built-in commercial operating system keychains (eg: iCloud Keychain, Windows Hello), Linux window manager keychains (eg: Gnome Keyring, KWallet), or a third party password manager (eg: 1Password, Bitwarden).

There are several potential ways to access the GAT on the command line, however they are not straight forward. Two potential options are to do this are by:

* Creating a command line alias
* Creating a wrapper script

**References**

* [npm Docs: Configuring npm using .npmrc](https://docs.npmjs.com/cli/v11/configuring-npm/npmrc)
* [GitHub Docs: About Secrets](https://docs.github.com/en/actions/security-for-github-actions/security-guides/about-secrets)
* [GitHub Docs: Using Secrets in GitHub Actions](https://docs.github.com/en/actions/security-for-github-actions/security-guides/using-secrets-in-github-actions)
* [GitHub Docs: Repository Roles for an Organization](https://docs.github.com/en/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/repository-roles-for-an-organization)

---
### Access Tokens: Emergency access removal and Token revocation

There are two options if a scenario presents itself where it is necessary to immediately deny an npm access token’s access to a resource: 

* If the owner of the user account that generated the access token is available and their user account is not compromised, they may revoke the access token on npmjs.com. Only the user who generated the access token is able to revoke the token.
* The only way to deny another user's access token to resources if the owner is not available to revoke their token is for the npm Organization’s Owners/Admins or Package owner to remove the person’s user account from the Organization, Team, or Package in question. The token is still valid and functional, it just no longer has access to the at-risk resources.

**References**

* [npm Docs: Revoking access tokens](https://docs.npmjs.com/revoking-access-tokens)
* [npm Docs: Removing members from your npm organization](https://docs.npmjs.com/removing-members-from-your-organization)

## Permissions Management Best Practices

**Summary**

* Organizations/Packages: Use npm Organizations to manage access to packages
* Organizations: Set the developers Team permissions for all packages to READ
* Organizations: Use separate Teams to manage permissions for different package teams
* Organizations/Packages: Limit the number of members with Publish rights

**Relevant npm Features**

* Organizations
* Packages

---
### Organizations/Packages: Use npm Organizations to manage access to packages

Users can be granted permissions to npm packages in two ways:

1) Use Teams in npm Organizations to selectively grant read/write permissions for different packages and different users with role based access controls  
2) Directly grant users access to packages owned by a user account rather than organization

Using npm Organizations is strongly recommended to leverage npm’s more robust Organization and Teams functionality across packages rather than managing individual access to each package.

npm Organizations have three different roles: Owners, Admins, and Members. The Admin and Member roles provide additional access controls that are not available when directly granting users access to packages.

**References**

* [npm Docs: Organization roles and permissions](https://docs.npmjs.com/organization-roles-and-permissions)
* [npm Docs: Creating an Organization](https://docs.npmjs.com/creating-an-organization)
* [npm Docs: Package Scope Access Level and Visibility](https://docs.npmjs.com/package-scope-access-level-and-visibility)

---
### Organizations: Set the developers team permissions for all packages to read

By default, all npm organizations contain a developers team that has special properties: This team:

* Cannot be deleted.
* Contains all members of the organization, who are added automatically and cannot be removed.
* Is automatically granted read/write permissions for new packages added to the organization.
* Cannot be removed from organization packages.

To ensure the developers team has no package access, follow these steps:

1. For each package in the organization, create a dedicated team for that package.
2. Add the package to its dedicated team, granting those team members full access.
3. Remove the package from the developers team.
4. Repeat for all packages until the developers team has zero packages assigned to it.

This approach ensures that only explicitly designated team members have access to each package, rather than all organization members by default.

**References**

* [npm Docs: Creating teams](https://docs.npmjs.com/creating-teams)
* [npm Docs: Managing Team access to Organization Packages](https://docs.npmjs.com/managing-team-access-to-organization-packages)

---

**References**

* [npm Docs: About the Developers Team](https://docs.npmjs.com/about-developers-team)
* [npm Docs: Managing Team access to Organization Packages](https://docs.npmjs.com/managing-team-access-to-organization-packages)

---
### Organizations: Use separate Teams to manage permissions for different packages

With the developers team’s permissions set to read for all packages, create a separate team to manage write permissions to packages.

If there are multiple packages in the organization, particularly if they have different individuals responsible for each package, manage write permissions by using separate teams for each package.

**References**

* [npm Docs: Creating teams](https://docs.npmjs.com/creating-teams)
* [npm Docs: Adding Organization members to teams](https://docs.npmjs.com/adding-organization-members-to-teams) / [npm Docs: Removing Organization members from Teams](https://docs.npmjs.com/removing-organization-members-from-teams)
* [npm Docs: Managing team access to Organization packages](https://docs.npmjs.com/managing-team-access-to-organization-packages)

---
### Organizations: Limit the number of users in npm organizations/packages

Because of the developers team’s default configuration, by default all organization members have permission to edit and publish organization packages. For this reason it’s recommended to keep the number of users in the npm organization and in Owner and Admin roles to the very minimum.

**References**

* [npm Docs: Organization roles and permissions](https://docs.npmjs.com/organization-roles-and-permissions)
