---
title: CI/CD
has_children: false
nav_order: 9
---

# CI/CD

## CI/CD Workflow Overview

FlappyPy implements a **GitHub Actions-based pipeline** that demonstrates industry-standard automation practices while supporting educational objectives. The comprehensive workflow validates code quality through automated testing across Windows, macOS, and Linux platforms with Python 3.9-3.11 compatibility, followed by seamless deployment to GitHub releases when semantic version tags trigger the release process.

This educational-focused approach eliminates manual deployment errors while providing immediate feedback to developers, ensuring the 55+ test suite maintains code reliability across all supported environments before any release reaches users.

## GitHub Actions Implementation

The **two-stage pipeline architecture** orchestrates continuous integration through `check.yml` and continuous deployment via `release.yml`, creating a quality-gated workflow where comprehensive testing across 9 environments (3 operating systems × 3 Python versions) must succeed before any release deployment begins.

```markdown
┌──────────────────────────────┐    ┌──────────────────────────────┐
│         check.yml            │    │        release.yml           │
│                              │    │                              │
│  ▸ Run Tests                 │    │  ▸ Build Source              │
│  ▸ Multi-OS Testing          │───▶│  ▸ Create GitHub Release     │
│  ▸ Multi-Python Versions     │    │  ▸ Attach Source Files       │
│                              │    │                              │
└──────────────────────────────┘    └──────────────────────────────┘
     Continuous Integration              Continuous Deployment
```

**Check Workflow:** Triggers on all commits and pull requests, executing parallel testing across Ubuntu, Windows, and macOS with Python 3.9-3.11 compatibility validation.

**Release Workflow:** Activates exclusively on semantic version tags from the main branch, performing final test validation before creating GitHub releases with attached source distributions.

**Quality Gates:**
- All 55+ tests must pass across environments
- Build process completion without errors  
- Successful GitHub release creation and source attachment

## Configuration and Security

The pipeline leverages **GitHub's integrated security model** with encrypted secrets management for API access tokens and branch protection rules that require passing CI checks before code integration. Repository permissions include write access for release creation and check reporting, while workflow execution remains isolated within GitHub's secure environment.

**Development Integration:**
- Feature branches trigger automatic testing upon commit push
- Pull requests undergo validation before merge approval
- Semantic version tags initiate automated release workflows
- Failed builds provide clear debugging information with rollback capabilities

## Performance and Reliability

The optimized pipeline architecture achieves **6-10 minute total release cycles** from tag creation to GitHub release availability, leveraging parallel testing execution across all platform combinations and dependency caching for enhanced performance. The comprehensive 55+ test suite provides complete functionality coverage while maintaining fast execution through efficient unit testing practices designed for immediate developer feedback.

**Reliability Features:**
- Multi-environment validation ensures consistent cross-platform behavior
- Automated quality gates prevent manual release decisions
- GitHub release history maintains complete rollback capabilities
- Real-time build notifications provide immediate failure feedback