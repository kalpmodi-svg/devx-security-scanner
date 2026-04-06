# devx Security Scanner

Drop-in GitHub Actions workflow + Renovate CVE-only config for any devx-commerce project.

## What it does

- **TruffleHog** - detects hardcoded secrets and credentials
- **Trivy v0.69.3** - finds vulnerable dependencies (CVEs)
- **Semgrep** - catches dangerous code patterns (injection, insecure crypto, deserialization)
- **Renovate** - automatically opens PRs to fix CVEs found by Trivy (security updates only, no random bumps)

## How to add to your project

### 1. Add the workflow

Copy `.github/workflows/devx-security-scanners.yml` into your project at the same path.

```
.github/workflows/devx-security-scanners.yml
```

No changes needed. It auto-detects base branch and scopes scans accordingly.

### 2. Add Renovate config

Copy `renovate.json` to your project root.

```
renovate.json
```

Then install the [Renovate GitHub App](https://github.com/apps/renovate) on your repo. It will only open PRs for CVE fixes - no noise from regular version bumps.

### 3. Optional - per project config

Add `.security-audit.yml` at your project root to customize behavior:

```yaml
fail_on: high
scan_history: false
exclude_paths:
  - "tests/"
  - "fixtures/"
scanners:
  trufflehog: true
  trivy: true
  semgrep: true
```

## What runs and when

| Layer | When | Purpose |
|-------|------|---------|
| Pre-push hook | Before `git push` | Blocks secrets/CVEs before they reach remote |
| PR gate | Every pull request | New findings only, posts comment + Security tab |
| Weekly scan | Every Monday 00:00 UTC | Full history compliance sweep |
| Renovate | On CVE detection | Auto-PRs to fix vulnerable dependencies |

## Built by

Kalp Modi - devx-commerce
