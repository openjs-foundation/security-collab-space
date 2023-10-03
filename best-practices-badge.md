# OpenSSF CII Best Practices Badge Guide

## Summary

Ensuring the security, sustainability, and maintainability of software projects is critically important. Following industry-standard best practices is a great start to doing that, and the [OpenSSF CII Best Practices badge system][bp] is a reliable way to concretely audit and measure how well the project is doing.

Here‘s how you can most efficiently secure your project and earn the OpenSSF CII Best Practices badge for your JS project - at a “Passing” level, at a minimum, and “Silver”, ideally. “Gold” is nice, but not practically achievable for most open source projects unless they are lucky or large enough to have multiple maintainers, or a corporation has intensely invested in them. To read more about the tiers, their rationale, and their goals, see [Criteria Discussion][bp-criteria].

## Who is this guide for?

This guide is for Open Source software project maintainers in the JS ecosystem - primarily projects that are published to [npm](https://npmjs.com). The goal is to, as efficiently as possible, help you move through the steps, both to accurately document what your project is currently doing, and, to surface opportunities for enhancing your project‘s security.

## Logging in

Visit [the login page][bp-login] and log in with your GitHub account.

## Terminology?

 - _the project_: The conceptual project - this does not mean a specific piece of software or repository, but includes all related material such as a repo, a website, maintainers, etc.
 - _Software produced by the project_: this does NOT mean “your software project outputs more runnable code”, it means “the software your conceptual project produces”.

## Locate/Create your project

Click [Projects][bp-projects] and see if your project already exists - if so, consider whether you can contact its owner and have them add your User ID (visit “Profile” in the “Account” dropdown on the upper right). If not, click [Add New][bp-new] and add your project.

## Edit your project

Click “Edit” if needed.

## Go for “Passing”

<details open>
<summary><h3 style="display:inline">Basics</h3></summary>

#### “Identification”

Hopefully the only one here that might not be easy to answer is the [“CPE”][cpe] one - if you know your project has one, fill it out, but if not, ignore it.

#### Basic project website content

A `CONTRIBUTING.md`, along with your website and/or project readme describing your project and what it does, should allow all of these to be “Met”.

#### FLOSS license

MIT is the most common license in the JS ecosystem, so hopefully that‘s what your project is using (because it‘s ideal, in any ecosystem, to use the most idiomatic license for that ecosystem), but if not, the OpenJS Foundation strongly recommends it‘s something [OSI-approved][osi] (this is required for Foundation projects). If so, this section is an easy “Met”.

#### Documentation

Again, if your website and/or project readme describes how to use the project, this section‘s easy. If not, it might be wise to do so.

#### Other

Everything should support HTTPS at this point, and your GitHub repo has the Issues feature, and for better or worse, English is the lingua franca of open source, so this guide assumes the maintainers can converse in English as needed. For “must be maintained”, please click “show details” _just in case_ you‘re missing some of the context, but hopefully y‘all are also doing all of this stuff too.

##### Other users

> What other users have additional rights to edit this badge entry?

Get your co-maintainers to register for an account on the badge website, and give you their user ID (in the URL when they go to Account -> Profile), and put it in here with a `+`.
</details>

<details open>
<summary><h3 style="display:inline">Change Control</h3></summary>

#### Public version-controlled source repository
If your repo is on GitHub, and if you merge changes to the default branch before releasing them (even if you have auto-publishing set up *after* that), then you can click “Met” for all of these (`repo_public`, `repo_track`, `repo_interim`, `repo_distributed`).

#### Unique version numbering
If you use [Semver][node-semver] and tag all of your releases in either the `v1.2.3` (preferred) or `1.2.3` format, or if in a monorepo, a consistent naming convention that makes identifying the version number easy for a human or a computer, then all of these are “Met” (`version_unique`, `version_semver`, `version_tags`).

#### Release notes
`release_notes`: Do you have a `CHANGELOG.md` file, or, do you use GitHub Releases as a changelog? If so, mark it as “Met” and add a link either to your `CHANGELOG.md`, or to `$REPO_URL/releases`.

`release_notes_vulns`: if you‘ve not yet had any CVEs, mark it as “N/A”. If you have, and they‘re identified in the release notes/changelog, mark it as “Met”.
</details>

<details open>
<summary><h3 style="display:inline">Reporting</h3></summary>

#### Bug-reporting process

GitHub Issues make `report_process`, `report_tracker`, and `report_archive` be “Met”; `report_responses` and `enhancement_responses` are “Met” if you‘ve had any response at all to at least _half_ of the issues that have come in within the last 2 to 12 months (hopefully you‘ve hit 100%, since “respond” doesn‘t mean “fix”, and just “triage” or “acknowledge” would suffice). To be explicit, “response” means any human response - adding a label or acknowleding the issue‘s receipt counts - but automated labelling and/or comments do not count, although the human responders they summon may.

#### Vulnerability report process

Make sure `$REPO_URL/security/policy` loads something relevant - see [nvm’s security policy][nvm-sec-pol] for an example. This can come from a `SECURITY.md` or `.github/SECURITY.md` in your repo, or, in the user or org‘s `.github` repo, either of the same two files.

If you have a policy that allows for private reports (like email), AND have enabled GitHub‘s [“Private Vulnerability Reporting” feature][pvr], then `vulnerability_report_process` and `vulnerability_report_private` are “Met”.

For `vulnerability_report_response`, if you‘ve received no reports, or none within the last 6 months, you can mark either “Met” or “N/A”; if you‘ve received any within the last 6 months, all of them must have been responded to (not necessarily fixed) within 2 weeks to select “Met”.
</details>

<details open>
<summary><h3 style="display:inline">Quality</h3></summary>

#### Working build system

Do you publish transpiled code, presumably with babel or typescript, or perhaps a bundler? Does your package have a `postinstall` or `prepare` script that causes consumers to run a build on install? If not, click “N/A” on `build`, `build_common_tools`, and `build_floss_tools`; if only the former, click “Met” on `build` assuming that a standard `npm install` and something akin to the conventional `npm run build` can run this build step. If the latter, things are more complex and nuanced - please ask in the [OpenJS Slack][slack].

If you‘re using a tool that‘s not heavily used in your relevant ecosystem, click “**Unmet**” on `build_common_tools`. If you‘re not sure, ask in the [OpenJS Slack][slack]]!

Assuming every build tool you‘re using is Open Source (has an OSI-approved license), click “Met” on `build_floss_tools`; if you‘re not using any, “N/A”; if you‘re using something that‘s not Open Source, click “**Unmet**”.

#### Automated test suite

Having repeatable CI - tests, linters, etc - that runs on “not a developer‘s machine” is very important to ensure a consistent baseline of functionality, and to ensure that regressions are avoided, important use cases are protected, and the API contract you commit to is fulfilled. Your CI checks should run on every PR and every push to the default branch<!-- (TODO: more on this here; eventually link to a different Scorecard doc) -->. If so, and if `npm test` invokes everything locally (preferably, no matter how you split up your CI, `npm test` should run as close to “every” test scenario that‘s practical), then that covers `test`, `test_invocation`, and `test_continuous_integration` as “Met”.

Code coverage is equally important, and helps ensure that every line, function, branch, and statement of your code is at least *exercised* in tests. The common tools for this standard practice in the JS ecosystem are nyc/istanbul, jest, or c8 (v8‘s built-in coverage tool), often combined with services like codecov or coveralls. If you‘re doing this, then `test_most` is also “Met”.

#### New functionality testing

If you have a required increase (or, prohibited decrease) on coverage with “protected branches”, and _especially_ if `CONTRIBUTING.md` says anything about “add tests that cover your changes”, then all three of these are “Met” (`test_policy`, `tests_are_added`, `tests_documented_added`).

#### Warning Flags

Either you‘re authoring in ESM (whether you transpile or not), or, you‘re authoring in CJS and using `'use strict';` directives at the top of every file - if so, all 3 of these are “Met” (`warnings`, `warnings_fixed`, `warnings_strict`).

Additionally, if you‘re using TypeScript, for these to be met you‘ll want to enable `strict` in `tsconfig.json`.
</details>

<details open>
<summary><h3 style="display:inline">Security</h3></summary>

#### Secure development knowledge

These two are a bit hand-wavy - basically, at least one of the maintainers “knows” how to design secure software, which includes knowing common security problems in JS.

Please be familiar with:
  - [npm Best Practices Guide][openssf-npm-bp]
  - [Node.js Security Best Practices][node-sec-guide]
  - [The Node.js threat model][node-threat-model]
  - [LF Designing Secure Software course][lf-course-designing-secure-software]

If at least one of y‘all believes you qualify, mark `know_secure_design` and `know_common_errors` as “Met” - if there are any doubts after reviewing the material above and completing the course, feel free to ask questions in the [OpenJS Slack][slack].

#### Use basic good cryptographic practices
Most projects simply don‘t _do_ any encryption or decryption, or, require a plugin to do it. If this is you, click the “Press here…” button and it‘ll mark everything in this section as “N/A”.

If your project *does* include encryption/decryption, please review these carefully - this document assumes that if applicable, you already have the knowledge required to understand what‘s being asked. If you have any doubts or concerns, please ask in the [OpenJS Slack][slack].

#### Secured delivery against man-in-the-middle (MITM) attacks

For a deployed application, the delivery of that application is secured in different ways based on your hosting environment. Your service provider and/or infrastructure team are likely handling this; if not, please ask in the [OpenJS Slack][slack].

For a library or a node-based executable, the primary, only expected, and most secure method of delivery is to publish to the public npm registry. (for private code, you‘d likely publish to a private npm registry, but since this guide is for public code, that won‘t be explored here) Assuming that you‘re doing so, both `delivery_mitm` and `delivery_unsigned` are an immediate “Met”.

#### Publicly known vulnerabilities fixed

CVEs can be filed, or vulnerabilities reported, against your project, and/or against your direct or transitive dependencies. As long as you are using semver ranges (`^` for anything following semver, which is most; or `~` for things like TypeScript or React that follow a modified Semver approach), then you likely do not need to take any action in your project. Certainly you may update the minimum required version, but you do not need to, even if users ask you to.

However, if you are pinning any of your dependencies (with `=`, or with a bare full version number), or, if you are bundling any dependencies (this includes `bundleDependencies` as well as if your package includes build output that was generated from a vulnerable dependency), then your package is implicated by the CVE just as much as the dependency‘s. Your solution may be to upgrade, or to downgrade, or to remove that dependency altogether, but since this can be complex and nuanced, please ask in the [OpenJS Slack][slack].

If your package has any CVEs, you fix them within 60 days -> both `vulnerabilities_fixed_60_days` and `vulnerabilities_critical_fixed` are “Met”. If you have none, both are “N/A”. If you aren‘t fixing them promptly, “**Unmet**”.

#### Other security issues

At this point, both npm and GitHub are pretty good about automatically catching leaked secrets; [make sure you‘re not leaking sensitive information][node-leak-guide] and have [enabled secret scanning for push protection][github-secret-scanning], and then mark `no_leaked_credentials` as “Met”.
</details>

<details open>
<summary><h3 style="display:inline">Analysis</h3></summary>

#### Static code analysis

Using a linter - a tool that helps enforce that your code follows best practices, avoids bugs, is consistent, and many more benefits - is at this point a de facto industry requirement. For the JS ecosystem, that linter is eslint. Note that this applies whether you‘re using a separate formatter or not (eslint is also a formatter, and you can use other formatters with it, like prettier), since formatters don‘t cover most of the classes of things that a linter can.

If you are doing this, and enforcing it passes in CI (on GitHub, as a required status check), that covers all 4 of these as “Met” (`static_analysis`, `static_analysis_common_vulnerabilities`, `static_analysis_fixed`, `static_analysis_often`). (It is strongly recommended that you set as many rules as possible to “error”, and that you use a common community shared config such as the [airbnb][airbnb-config] config, with small tweaks on top of that, versus making your own config from scratch)

You may also wish to enable GitHub‘s CodeQL, which helps cover this requirement.

#### Dynamic code analysis
CodeQL marks `dynamic_analysis` and `dynamic_analysis_enable_assertions` as “Met”; JS is memory-safe, which covers `dynamic_analysis_unsafe`; making CodeQL a required check covers `dynamic_analysis_fixed`.
</details>
<br />

That should cover the “passing” tier, and you should be at 100%.

## Add the badge

Make a PR. or push a commit, that adds the following markdown to the top of your readme:
```md
[![CII Best Practices](https://www.bestpractices.dev/projects/$ID/badge)](https://www.bestpractices.dev/projects/$ID)
```

where `$ID` is the ID of your project - you can find it in the URL on the best practices site.

## Go for “Silver”!

Click the “silver” pill near the top of the page - it‘s the word “silver” in the sentence `“These are the Passing level criteria. You can also view the silver and gold level criteria”`.

Click “Hide met & N/A”, above, to hide all the “passing” items you‘ve already completed.

<details open>
<summary><h3 style="display:inline">Basics</h3></summary>

#### Identification
Fill out a brief description of your project, if you haven‘t already.

#### Project oversight
If you already have a [DCO or CLA][dco-vs-cla] process, then click “Met” on `dco`.

For `governance` and `roles_responsibilities`, to click “Met”, create a `GOVERNANCE.md` file at the root of your repo that describes how the project is run: who makes decisions, how disputes are resolved, how someone can become a contributor and/or a maintainer (or other roles you define there), etc. Some useful resources:
 - <https://opensource.guide/leadership-and-governance/>
 - <https://github.com/github/mvg>

Hopefully you already have a Code of Conduct. If not, create a `CODE_OF_CONDUCT.md`` file, either at the root of your repo, in the `.github/` folder, or, in the user/organization‘s `.github` repo (in one of the same locations). The latter is preferred so it applies by default to new repos. Some resources:
- <https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/adding-a-code-of-conduct-to-your-project>

Once you have a CoC, `code_of_conduct` is “Met”.

These last two basically require having more than one maintainer. You technically _can_ satisfy the `access_continuity` one by having a succession plan so that someone takes over in the event of disruption, but since the `bus_factor` item requires 2 or more maintainers, you‘ll need to recruit folks to mark these as “Met”.

#### Documentation
First, you‘re asked for a documented “roadmap”. This can be a `ROADMAP.md`, an issue describing future plans, a link to GitHub Milestones, etc - some way a user can figure out what‘s likely to be worked on in the next year - and then you can click “Met” on `documentation_roadmap`.

`documentation_architecture`: TODO, please ask in [Slack][slack]. <!-- unclear -->

`documentation_security`: TODO, please ask in [Slack][slack]. <!-- unclear -->

As long as you have any sort of “quick start” guide, you can click “Met” for `documentation_quick_start`. This could be as involved or concise as experience indicates is necessary.

Typically, documentation is kept in the repo, and optionally published to a website. If you have a website, and it‘s updated on every release, or if you don‘t have a website, then click “Met” for `documentation_current`.

Once you‘ve added the “passing” badge to your GitHub readme (preferred) or project website, then `documentation_achievements` is “Met”.

#### Accessibility and internationalization

`accessibility_best_practices`: TODO, please ask in [Slack][slack]. <!-- unclear -->

`internationalization`: TODO, please ask in [Slack][slack]. <!-- unclear -->

#### Other

Most OSS projects don‘t store any user credentials, so `sites_password_security` can be set to “N/A”.
</details>

<details open>
<summary><h3 style="display:inline">Change Control</h3></summary>

#### Previous Versions

For anything published to npm, you get `maintenance_or_update` “Met” for free. For anything else, please ask in the [OpenJS Slack][slack]. Note that using semver-based git-tagged releases with a similarly version-controlled installation/upgrade/downgrade process may qualify, but please ask just in case.
</details>

<details open>
<summary><h3 style="display:inline">Reporting</h3></summary>

#### Bug-reporting process

Assuming Github Issues are enabled, click “Met” and put `$REPO_URL/issues` as the URL.

#### Vulnerability report process

If you‘ve had no vulnerabilities reported in the last year, click “N/A”. If you have, and the reporter hasn‘t asked to stay anonymous, make sure you‘ve given them credit somewhere (the changelog, the opening post of a PR or an issue, a GitHub Release, etc) - and then you can click “Met” for `vulnerability_report_credit`.

If you‘ve got a Security Policy (which the “passing” criteria requires already), and it lists an email address for private reports - OR if you‘re on GitHub and enabled PVR (private vulnerability reporting) - you can click “Met” for `vulnerability_response_process`.
</details>

<details open>
<summary><h3 style="display:inline">Quality</h3></summary>

#### Coding standards

If you‘ve enabled eslint, as is strongly recommended in the “passing” criteria for static code analysis, and if it‘s configured to enforce your preferred code style, then `coding_standards` is “Met”. If you‘ve *also* made passing the linter a required status check to land code in the default branch (or in a release), then `coding_standards_enforced` is also “Met”.

#### Working build system

If you‘re authoring a native JS or WASM project, then all four of these are “N/A” (`build_standard_variables`, `build_preserve_debug`, `build_non_recursive`, `build_repeatable`). If not, please ask in the [OpenJS Slack][slack].

#### Installation system

If you‘re publishing to npm, then all three of these are “Met” (`installation_common`, `installation_standard_variables`, `installation_development_quick`).

#### Externally-maintained components

If all external dependencies are listed in `package.json` - runtime deps in “dependencies” and “peerDependencies” and non-runtime dev deps in “devDependencies” - then `external_dependencies` and `updateable_reused_components` are both “Met”.

If you‘ve enabled [Renovate][renovate] or [Dependabot][dependabot], then `dependency_monitoring` is “Met”.

If all of your direct dependencies are using an Open Source (OSI-approved) license, and you‘ve addressed any deprecations in direct dependencies (or there isn‘t a viable alternative), then `interfaces_current` is “Met”.

#### Automated test suite

If you‘ve followed our recommendations in the “passing” section, and enabled GitHub branch protections or the equivalent such that passing tests are required to merge code into the default branch and/or a release, then `automated_integration_testing` is “Met”.

If at least half of your bugfixes are backed by regression tests, then `regression_tests_added50` is “Met”. If not, go add those tests retroactively, so that you do meet this criteria.

Almost every test framework has a code coverage solution - either built-in, or via [nyc][nyc] - and if you‘re using it, and have at least 80% statement coverage (there‘s 4 metrics: statements, branches, functions, lines, and ideally all four are close to 100%) then you can mark `test_statement_coverage80` as “Met”.

#### New functionality testing
If you‘ve written down somewhere - ideally in `CONTRIBUTING.md` - that regression tests are required for bugfixes, and tests are required for new features, then `test_policy_mandated` and `tests_documented_added` are both “Met”.

#### Warning flags
If your software is just JS, then `warnings_strict` is “N/A”.
</details>

<details open>
<summary><h3 style="display:inline">Security</h3></summary>

#### Secure development knowledge

If your software is implemented using the principles that your maintainers are aware of from a [previous section](#Secure-development-knowledge), then `implement_secure_design` is “Met”.

#### Use basic good cryptographic practices

Most software does not deal with cryptography at all - even the core of a webserver may not, if cryptographic functionality is provided by plugins - and thus these projects can click the “Press here” button to mark everything as “N/A”.

If this stuff does apply to your project, please ask in the [OpenJS Slack][slack].

#### Secure release

If you publish to npm, `signed_releases` is “Met”.

If you create a git tag for each release according to the [“Unique version numbering”](#Unique-version-numbering) guidance, then `version_tags_signed` is “Met”.

#### Other security issues

The arguments of every function called by a consumer, or any data read from a filesystem or received over a network, is untrusted data. To satisfy `input_validation` as “Met”, all untrusted data must be validated in some way - ideally, maximally so, and every invalid input rejected.

`hardening`: TODO, please ask in [Slack][slack]. <!-- unclear -->

`assurance_case`: TODO, please ask in [Slack][slack]. <!-- unclear -->
</details>

<details open>
<summary><h3 style="display:inline">Analysis</h3></summary>

#### Static code analysis

If you run `npm audit` or the equivalent in your CI, then `static_analysis_common_vulnerabilities` is “Met”. For npm projects without a lockfile, you can use <https://npmjs.com/aud>.

If you‘re using CodeQL as recommended previously, `dynamic_analysis_unsafe` is “Met”.
</details>


## Go for “Gold”?

This document does not go into the “Gold” requirements. The requirements are more challenging, and also impossible to meet with a single-maintainer project. Few projects need to seek this tier.

[bp]: https://www.bestpractices.dev
[bp-projects]: https://www.bestpractices.dev/en/projects
[bp-criteria]: https://www.bestpractices.dev/en/criteria_discussion
[bp-login]: https://www.bestpractices.dev/login
[bp-new]: https://www.bestpractices.dev/en/projects/new
[cpe]: https://nvd.nist.gov/products/cpe
[osi]: https://opensource.org/licenses/
[node-semver]: https://www.npmjs.com/package/semver
[nvm-sec-pol]: https://github.com/nvm-sh/nvm/security/policy
[pvr]: https://docs.github.com/en/code-security/security-advisories/repository-security-advisories/configuring-private-vulnerability-reporting-for-a-repository
[slack]: https://slack-invite.openjsf.org/
[nyc]: https://npmjs.com/nyc
[openssf-npm-bp]: https://github.com/ossf/package-manager-best-practices/blob/main/published/npm.md
[node-sec-guide]: https://nodejs.org/en/docs/guides/security
[node-threat-model]: https://github.com/nodejs/node/blob/main/SECURITY.md#the-nodejs-threat-model
[lf-course-designing-secure-software]: https://training.linuxfoundation.org/training/developing-secure-software-lfd121/
[node-leak-guide]: https://nodejs.org/en/docs/guides/security#exposure-of-sensitive-information-to-an-unauthorized-actor-cwe-552
[github-secret-scanning]: https://docs.github.com/en/code-security/secret-scanning/push-protection-for-repositories-and-organizations#enabling-secret-scanning-as-a-push-protection
[airbnb-config]: https://npmjs.com/eslint-config-airbnb-base
[dco-vs-cla]: https://opensource.com/article/18/3/cla-vs-dco-whats-difference
[renovate]: https://www.mend.io/renovate/
[dependabot]: https://docs.github.com/en/code-security/dependabot/dependabot-version-updates/configuring-dependabot-version-updates#enabling-github-dependabot-version-updates
