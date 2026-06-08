# Security Policy

## Supported Versions

| Version | Supported |
| ------- | --------- |
| 1.x     | ✅        |

## Reporting a Vulnerability

We take the security of Character Toolkit seriously. If you discover a security vulnerability, please **do not open a public issue**.

Instead, report it privately through the contact channel on [https://texttool.online](https://texttool.online), or by using GitHub's private security advisory feature on the repository.

Please include:

- A description of the vulnerability and its impact.
- Steps to reproduce or a proof of concept.
- Any suggested remediation, if known.

### What to Expect

- We aim to acknowledge reports within **72 hours**.
- We will work with you to understand and validate the issue.
- Once a fix is ready, we will publish a patched release and credit the reporter (unless anonymity is requested).

## Scope

Character Toolkit is a pure text-processing library with no network or filesystem access. The most relevant risks are denial-of-service patterns (e.g. pathological inputs to expensive functions). Guards such as the `maxLength` limit on `generateAnagrams` are in place; please report any input that causes excessive CPU or memory use.
