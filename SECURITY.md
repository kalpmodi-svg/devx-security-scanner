# Security Policy

## Reporting a Vulnerability

If you have found a security vulnerability in the devx security scanner workflow or its configuration, please report it privately so it can be addressed before public disclosure.

**Do not open a public GitHub issue for security vulnerabilities.**

### How to report

Use GitHub's private vulnerability reporting:

1. Go to the [Security tab](https://github.com/kalpmodi-svg/devx-security-scanner/security)
2. Click **"Report a vulnerability"**
3. Fill in the details - what you found, steps to reproduce, and potential impact
4. Submit - it goes directly to the maintainer without public exposure

Alternatively, reports can be sent directly to the maintainer via GitHub: [@kalpmodi-svg](https://github.com/kalpmodi-svg)

### What to include

- Description of the vulnerability
- Steps to reproduce
- Affected file(s) and line numbers if applicable
- Potential impact
- Suggested fix if you have one

### Response timeline

| Action | Timeline |
|--------|---------|
| Acknowledgement | Within 48 hours |
| Initial assessment | Within 5 business days |
| Fix or mitigation | Depends on severity - CRITICAL within 7 days, HIGH within 14 days |
| Public disclosure | After fix is released |

### Scope

This security policy covers:

- `.github/workflows/devx-security-scanners.yml` - the GitHub Actions workflow
- `renovate.json` - the Renovate CVE-only configuration
- Any supply chain risks introduced by pinned tool versions (TruffleHog, Trivy v0.69.3, Semgrep)

### Out of scope

- Vulnerabilities in TruffleHog, Trivy, or Semgrep themselves - report those to their respective projects
- Vulnerabilities found by the scanner in projects that adopt this workflow - those belong to the respective project owners

---

Maintained by Kalp Modi - devx-commerce
