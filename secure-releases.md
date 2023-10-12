# Secure Releases and CVE Management for the JS Ecosystem

## Secure Releases

In order for your JS software project to be safe, secure, and reliable, its releases need to follow security best practices. Below are the OpenJS Foundations recommended best practices for secure releases.

### Two-factor and Multifactor Authentication

Two-factor authentication (2FA) and Multifactor Authentication (MFA) means having something more than just your password to confirm you're you. The second factor can be a one-time code using a 2FA/MFA authentication app (like Google Authenticator, Authy, 1Password, etc), a hardware key (such as Yubikey or Titan), or a passkey using touch ID, face ID, or another locally stored secure passkey mechanism on your device. Note: do not *ever* use SMS for 2FA/MFA unless it's the only mechanism offered, since SMS is vulnerable to SIM swap and number forgery attacks.

Although this extra authentication step can be a mild inconvenience, the benefit for security is overwhelmingly worth it. Both GitHub and npm will soon require 2FA/MFA for every user, so you might as well enable it now.

Please use a secure password manager to store, and generate, your secure password; additionally, make sure to preserve your recovery codes in a safe place, preferably not connected to the internet and in a separate physical location.

### Preparing for Publish

It can be easy to forget to run steps before publishing. If you have any build steps (transpiling with Babel or TypeScript, emitting types with TypeScript, etc) and/or validation steps (running tests, etc), make sure they're set up in the `scripts` section of `package.json` such that `npm run prepublish` or `npm run prepublishOnly` would invoke them - that way, running `npm publish` in the future will automatically run these steps.

Publishing to npm can be done in one step (`npm publish`), or two (`npm pack` to generate a tarball, and then later, `npm publish path/to/tarball` to publish). Even if you publish separately with one step, it's a good idea to run `npm pack` in CI to ensure that the steps succeed, and that the tarball is somewhat reproducible. (Example: [this workflow](https://github.com/ljharb/actions/blob/5a85b6e4de8738a6c7a87a45ebc9711f2d9a7226/.github/workflows/pretest.yml#L64-L67), which you can see the latest runs of [here](https://github.com/ljharb/qs/actions/workflows/node-pretest.yml?query=branch%3Amain))

### Publishing
If you have only one person who can publish releases, then this step is optional. If you have two or more, this step is strongly recommended.

Publish a packed tarball from CI, only upon an explicit request. This means, don't make a new release automatically, but make sure that a human has intentionally said "it's time to publish a new version, here's the version number it will use". This explicit request can be a pushed semver-versioned git tag, or an explicit user-run workflow - but does not include merging/committing to the default branch.

Do not publish without using 2FA. Note that an npm automation token is a single factor, and does not qualify as 2FA. Since GitHub does not provide any functionality to allow you to input a 2FA code natively, you'll need to use something like [Wombat Dressing Room](https://opensource.googleblog.com/2020/01/wombat-dressing-room-npm-publication_10.html) which requires you to host a service on GCP ([example](https://github.com/mathiasbynens/String.prototype.endsWith/blob/main/.github/workflows/publish-on-tag.yml#L21-L22)), or [Step Security's Wait For Secrets](https://github.com/step-security/wait-for-secrets) ([example](https://github.com/jsx-eslint/eslint-plugin-react/blob/28f9a6cdf716bc34f824ea3a3988e68f3e54eb0f/.github/workflows/npm-publish.yml)) which requires you to trust Step Security's external service.

## CVE Management

### Security Policy

Your software project will, likely inevitably, have a security vulnerability. When that happens, you want to make sure that whoever discovers it has a way to report it to you privately - this is called "responsible disclosure" or "coordinated disclosure". So, the first important step is to *have a security policy*.

On GitHub, this is always located at `$REPO_URL/security/policy` ([example](https://github.com/nvm-sh/nvm/security/policy)). This page can be populated from a number of file locations: `SECURITY.md` or `.github/SECURITY.md` in the repo itself, or, one of the same files in your user or organization’s `.github` repository. If you're not on GitHub, then look for a similar platform-specific convention, and if you find none, a top-level `SECURITY.md` is safe.

In this policy, you'll want to mention a private reporting channel. This could be an email address, a service like HackerOne, etc.

#### Programmatic Private Vulnerability Reporting

GitHub and Gitlab support a Private Vulnerability Reporting (PVR) feature and API. This allows reporters to use the platform itself, programmatically if needed. It is strongly recommended to enable this feature, if it's not already on by default. Note that it can be enabled at the user/org level for all repos, including enabled as the default for new repos.

### Audit Dependencies

You'll want to ensure all of your dependencies - direct and transitive - are audited on every commit. This can be achieved locally and in CI with `npm audit`, if your project has a lockfile, or https://npmjs.com/aud for packages without a lockfile.

In addition - not instead - you may want to use services like Dependabot, Renovate, [Tidelift](https://tidelift.com), [Socket.dev](https://socket.dev), etc to automatically detect and warn you about issues with your dependency graph.

If your package does not have a build process - meaning, all of the artifacts you publish are committed to version control and hand-written - then you may only need to audit your runtime dependencies (`dependencies`, `peerDependencies`) and not `devDependendies`. However, if you do have a build process, whichever dev deps that generate code need to be audited as well.

### Handling Reports

First, be highly responsive. Respond to a report as soon as possible; ideally, within 24 hours or one business day. Your security policy should explicitly describe your expected response time - especially if it's longer than this.

When responding to a report, you'll want to seriously consider how the behavior may or may not be a vulnerability. Things to weigh include what documentation says, typical community expectations, what the likely attack surface looks like, etc. These considerations can be nuanced, so always err on the side of discussing it with your favorite trusted security exports - feel free to ask us on the [OpenJS Slack](https://slack-invite.openjsf.org/).

When publishing your fixes, be sure to _credit your reporters_. This can include an explicit reference in the issue and at-mentioning their username(s) in the changelog or in GitHub Releases. Be sure to wait until the issue has been publicly disclosed before referencing a CVE number or another vulnerability identifier. If you’re using GitHub’s PVR feature, assigning credit is built into the UI.

## Additional Resources

 - https://github.com/ossf/package-manager-best-practices/blob/main/published/npm.md
 - https://github.com/ossf/wg-best-practices-os-developers/blob/main/docs/Concise-Guide-for-Developing-More-Secure-Software.md#readme

