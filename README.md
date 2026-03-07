# .github

Organization-level GitHub configuration for **PavelGuzenfeld** repositories.

This is a [special `.github` repository](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file) that provides default community health files and reusable workflow templates across all repos in the organization.

## What's Inside

### Workflow Templates

Starter workflows that appear in the **Actions > New workflow** tab of every repo. Each template calls reusable workflows from [PavelGuzenfeld/standard](https://github.com/PavelGuzenfeld/standard) — a centralized CI/CD quality-gate framework.

| Template | Description | Tools |
|----------|-------------|-------|
| **Standard C++ Quality** | Diff-aware C++ quality gates | clang-tidy, cppcheck, clang-format, flawfinder, ShellCheck, Hadolint, Gitleaks |
| **Standard Python Quality** | Diff-aware Python quality gates | ruff, pytest, Semgrep, pip-audit, ShellCheck, Gitleaks |
| **Standard Full Quality** | Combined C++ + Python gates | All of the above + cmake-lint |

To use a template: go to your repo's **Actions** tab > **New workflow** > look for "Standard" templates.

### Org-Wide Compliance Workflows

Scheduled workflows that scan all repositories for standards adoption and supply-chain security.

| Workflow | Schedule | Purpose |
|----------|----------|---------|
| **Compliance** | Monday 9am UTC | Scans all repos for `standard` adoption drift. Can auto-open PRs to update drifted repos. |
| **CIS Compliance** | Saturday 10am UTC | Runs [CIS Software Supply Chain v1.0](https://www.cisecurity.org/benchmark/software_supply_chain) benchmarks across repos. Creates tracking issues for failures. |

Both can also be triggered manually via `workflow_dispatch`.

## Repository Structure

```
.github/
  workflows/
    compliance.yml          # Weekly standards compliance scan
    cis-compliance.yml      # Weekly CIS supply-chain audit
workflow-templates/
    standard-cpp-quality.yml             # C++ starter workflow
    standard-cpp-quality.properties.json
    standard-python-quality.yml          # Python starter workflow
    standard-python-quality.properties.json
    standard-full-quality.yml            # C++ + Python starter workflow
    standard-full-quality.properties.json
    standard-icon.svg                    # Shared icon for templates
```

## Related

- [PavelGuzenfeld/standard](https://github.com/PavelGuzenfeld/standard) — The reusable workflow library and `standard-ci` CLI that powers everything above.
