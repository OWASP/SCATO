# Security Policy

SCATO is an OWASP project. A security tool must be held to a higher standard than the code it scans, so we take reports about SCATO itself seriously.

## Supported Versions

| Version | Supported |
| ------- | --------- |
| 3.x     | Yes       |
| < 3.0   | No        |

Security fixes are released for the latest 3.x minor version only. Upgrade to the latest release before reporting.

## Reporting a Vulnerability

**Do not open a public issue, discussion, or pull request for a security problem.**

Report privately through GitHub Security Advisories:
https://github.com/OWASP/SCATO/security/advisories/new

Please include:

- Affected version or commit
- Steps to reproduce, or a proof of concept
- Impact: what an attacker can do, and under which conditions
- A suggested fix, if you have one

## What to Expect

| Step | Target |
| ---- | ------ |
| Initial response | within 14 days |
| Fix for medium, high, or critical severity | within 60 days |
| Public disclosure | coordinated with the reporter once a fix is released |
| Actively exploited issues | fix or mitigation guidance published as fast as possible |

These timelines follow the [OpenSSF Best Practices](https://www.bestpractices.dev/en/criteria/0) criteria `vulnerability_report_response` and `vulnerabilities_fixed_60_days`.

We will keep you informed of progress, credit you in the advisory and release notes unless you ask us not to, and request a CVE for confirmed vulnerabilities.

## Scope

**In scope:** the SCATO CLI, the `scato serve` web dashboard and API, the GitHub Action (`action.yml`), the CI templates, and the official Docker image.

Examples of what we want to hear about:

- Code execution, file read, or file write triggered by scanning a project or by calling the API
- Authentication, CSRF, or cross-origin issues in the dashboard
- Injection in the GitHub Action or CI templates
- Results that are wrong in a way that hides vulnerabilities (for example, missed matches or underreported severity)
- Leaks of tokens or API keys

**Out of scope:**

- Vulnerabilities in the projects SCATO scans. Report those to the affected project or through [OSV](https://osv.dev).
- Incorrect data in upstream sources (OSV, NVD, GHSA, CISA KEV, EPSS). Report those to the source.
- Findings that require an already-compromised machine or account.
- Missing hardening headers, rate limits, or best practices with no demonstrated impact.

## Safe Harbor

We will not pursue legal action against good-faith research that follows this policy: test only against systems you own or are authorized to test, avoid privacy violations and service disruption, and give us reasonable time to fix before disclosing.

## Using SCATO Safely

Until the hardening work in the current release cycle ships, follow these practices:

- Run `scato serve` only on a trusted machine. Do not expose the dashboard port to a network.
- Scan untrusted code (for example, pull requests from forks) only inside an isolated, disposable environment that holds no secrets.
- Grant the GitHub Action the minimum `permissions:` it needs, and pin it to a release tag or commit SHA.
- Pass API keys through environment variables or CI secrets. Never commit them.

## Contact

- Security reports: [GitHub Security Advisories](https://github.com/OWASP/SCATO/security/advisories/new)
- Everything else: [Issues](https://github.com/OWASP/SCATO/issues)
