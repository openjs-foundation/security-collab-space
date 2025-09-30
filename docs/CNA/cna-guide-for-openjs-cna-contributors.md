# OpenJS CNA Guide For CNA Contributors

## Reserved CVE ID Handling

### Reserving CVE IDs

- The CNA should have no less than 2 and no more than 5 reserved, unused CVEs at any one time
- An issue must be created and approved in [security-advisories](https://github.com/openjs-foundation/security-advisories) before additional CVE IDs may be reserved

### Managing Reserved CVE IDs
- All reserved CVE IDs are stored in [security-advisories](https://github.com/openjs-foundation/security-advisories)/reserved-cve.md until they are assigned to a CVE Request

### Assigning a CVE ID to a CVE Request
- Comment in the CVE Request issue stating which reserved CVE IDs will be requested to be used
- A pull request with a link to the relevant CVE Request issue must be approved to remove one or more CVE IDs from reserved-cve.md

## Handling CVE Requests

### Capture CVE Requests from email
- Let other coordinators know you're creating the issue in the #cna slack
- Create an issue in the issue in the security-advisories repo
- Use [THIS TBD TEMPLATE] to ensure everything needed to publish the CVE has been captured
- Requests for multiple CVEs that will be published at the same time should go in the same issue

### Assigning a CVE Request
- A CVE Request should be handled by the same coordinator from start to finish

### Verify the authenticity of CVE requests from project maintainers
TBD

### Collaborate with project maintainers
- Avoid using email beside initial contact
- Use the project maintainer's preferred tools to collaborate on content of security advisories
- The CVE Request issue should only be used for coordinating within the CNA

### Generate CVE JSON
- Do not use the free online [Vulnogram](https://vulnogram.github.io/) site for real pre-release vulnerabilities!
- Use a locally hosted version of:
  - [Vulnogram](https://vulnogram.github.io/)
  - [cveClient](https://github.com/CERTCC/cveClient?)

### Pre-Publication Review of CVE ID JSON
- Create a pull request with link to the relevant CVE Request issue for each CVE ID JSON file
- Have two people review and these

### Pre-Publication Review of OpenJS CNA Security Advisories Webpage
- Create a pull request for the relevant changes to the webpage
- Do not merge the pull request until after CVE publication

### Publishing CVEs
- CVE JSON PRs and CNA Security Advisories Webpage PR must be approved before publishing CVEs
- As plans can change, immediately before submitting a CVE get final confirmation from the project maintainer
- Consider publishing each CVE ID JSON to the test instance to validate correct display before publishing to production
- Close the CVE Request issue once the CVE is published and the project maintainer confirms no further support is needed
