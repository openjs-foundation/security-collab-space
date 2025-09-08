# OpenJS Foundation Projects and the OpenSSF Best Practices Badge

This document is written for two primary audiences: OpenJS Foundation staff/volunteers/stakeholders, and end users of Foundation software projects.

## Status Overview

Of the 7 projects deemed “critical”, 6 of them have set up a "badge project" to start tracking their compliance with the best practices. 3 of those 6 are at 100% of the “Passing” tier, and the remaining 3 are 82% or higher.

Of the remaining 26 non-archived projects, 5 of them have set up a badge project, and 2 of those are at 100% “Passing”.

Detailed results are available on this [temporary tracking dashboard][dashboard].

## Breakdown of work done

Most of the work done was by the project maintainers themselves, although an OpenJS contractor coordinated and drove much of it. By following the JS-ecosystem-focused [Best Practices Badge Guide](https://github.com/openjs-foundation/security-collab-space/blob/main/best-practices-badge.md), project maintainers should be able to efficiently document their existing practices, see what needs improvement, and implement those improvements.

## Known Gaps

 “Silver” status requires having two or more maintainers, and “Gold” status requires that those two not be associated (ie, employed at the same company). Thus, single-maintainer projects may find themselves unable to qualify for “Silver”, and single-company-driven projects may find themselves unable to qualify for “Gold”. `nvm`, for example, has only two conceptual items to satisfy before meeting 100% Silver, one of which would be obtaining a second maintainer. The percentage fields on the [dashboard][dashboard] have comments describing the gaps for the projects that are close to 100%.

## Analysis of Project State

Overall, things seem pretty good so far! The largest oversight is that 16 projects, one of them “critical”, are missing a security policy. Efforts should be prioritized to create an example security policy for projects to copy, and to nudge projects to do so.

Otherwise, the gaps tend to be things that for JS projects don't directly relate to security, but decrease the overall likelihood of security-related issues, like code coverage, static and dynamic analysis tools, etc. With further effort to document all Foundation projects' current status, the best places to focus will become clear.

## Next Steps

Overall, next is to get all foundation projects up to 100% Passing, and fully populate the [dashboard][dashboard]. That progress can be tracked in [this GitHub issue](https://github.com/openjs-foundation/security-collab-space/issues/95).

[dashboard]: https://docs.google.com/spreadsheets/d/1wUsWSRu4x_Up4PjVNhEu_z8eOag8V7bcJGaJJl5RlC8/edit#gid=0
