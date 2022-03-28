# Security Vulnerability Process

I (Christian Kotzbauer) use this security disclosures and response policy to ensure that critical issues are handled responsibly.
Security vulnerabilities should be handled quickly and sometimes privately. The primary goal of this process is to reduce the total time users are vulnerable to publicly and privately known exploits.

### Contact

* Christian Kotzbauer (git@ckotzbauer.de) [GPG Key](https://api.github.com/users/ckotzbauer/gpg_keys)

I will share various tasks as listed below:

- Triage: Assess the impact of the vulnerability (can it be replicated, is the code in one of my repos or upstream?)
- Infra: Create a security advisory and temporary fork to work on the issue
- Disclosure: Handle public messaging around the vulnerability, by documenting the issue (how to upgrade, list affected versions, draft an advisory notice)
- Release: Create new release addressing a security fix and notify the public


## Disclosures

### Private Disclosure Processes

I ask that all suspected vulnerabilities be handled in accordance with [Responsible Disclosure model](https://en.wikipedia.org/wiki/Responsible_disclosure).

### Public Disclosure Processes

If anyone knows of a publicly disclosed security vulnerability please IMMEDIATELY email me about the vulnerability so that I may start the patch, release, and communication process.

If a reporter contacts me to express intent to make an issue public before a fix is available, I will request if the issue can be handled via a private disclosure process. If the reporter denies the request, I will move swiftly with the fix and release process.

## Patch, Release, and Public Communication

For each vulnerability, I will coordinate to create the fix and release, and notify the public.

All of the timelines below are suggestions and assume a Private Disclosure.

- I drive the schedule using their best judgment based on severity, development time, and release work.
- If I'm dealing with a Public Disclosure all timelines become ASAP.
- If the fix relies on another upstream project's disclosure timeline, that will adjust the process as well.
- I will work with the upstream project to fit their timeline and best protect the users.

### Fix Development Process

These steps should be completed within the 1-14 days of Disclosure.

- I will create a new [security advisory](https://docs.github.com/en/code-security/security-advisories/) in affected repository by visiting `https://github.com/ckotzbauer/<project>/security/advisories/new`
- As many details as possible should be entered such as versions affected, CVE (if available yet). As more information is discovered, edit and update the advisory accordingly.
- Use the CVSS calculator to score a severity level.
- Request a CVE
- I will create a private temporary fork
- All communication happens within the security advisory, it is *not* discussed in slack channels or non private issues.
- I will decide on a release day, if the work is completed.

If the CVSS score is under ~4.0
([a low severity score](https://www.first.org/cvss/specification-document#i5)) or the assessed risk is low I can decide to slow the release process down in the face of holidays, developer bandwidth, etc.

The severity of the bug and related handling decisions must be discussed on in the security advisory, never in public repos.

### Fix Disclosure Process

**Fix Release Day** (Completed within 1-21 days of Disclosure)

- I will approve the related pull requests in the private temporary branch of the security advisory
- I will merge the security advisory / temporary fork and its commits into the main branch of the affected repository
- I will ensure all the binaries are built, signed, publicly available, and functional.
- I will announce the new releases, the CVE number, severity, and impact, and the location of the binaries to get wide distribution and user action. As much as possible this announcement should be actionable, and include any mitigating steps users can take prior to upgrading to a fixed version. An announcement template is available below.

### Security Fix Announcement Template

```
This addresses the following CVE(s):

* CVE-YEAR-ABCDEF (CVSS score $CVSS): $CVESUMMARY
...

Upgrading to $VERSION is encouraged to fix these issues.

**Am I vulnerable?**

Check the project version and if it indicates a base version of $OLDVERSION or
older that means it is a vulnerable version.

<!-- Provide details on features, extensions, configuration that make it likely that a system is
vulnerable in practice. -->

**How do I mitigate the vulnerability?**

<!--
[This is an optional section. Remove if there are no mitigations.]
-->

**How do I upgrade?**

<!--
[Outline upgrade steps]
-->

**Vulnerability Details**

<!--
[For each CVE]
-->
  ```

## Credit

Parts of this process were inspired by the sigstore's security handling process.
