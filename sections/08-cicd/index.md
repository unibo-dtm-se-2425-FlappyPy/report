---
title: CI/CD
has_children: false
nav_order: 9
---

# CI/CD

## CI/CD Workflow Overview

**FlappyPy uses a comprehensive GitHub Actions-based CI/CD pipeline that automates testing, building, and deployment processes.**

### What is Automated?

**Continuous Integration (CI):**
- **Automated testing** on every commit and pull request.
- **Multi-platform testing** across Windows, macOS, and Linux.
- **Multi-version testing** across Python 3.9, 3.10, and 3.11
- **Code quality validation** through comprehensive unit test suite (55+ tests).

**Continuous Deployment (CD):**
- **Automatic GitHub releases** triggered by semantic version tags
- **Source code packaging** and distribution without manual intervention
- **Release documentation** generation from git tag messages
- **Immediate availability** via GitHub releases page

### Why This Approach?

**Quality Assurance Benefits:**
- **Immediate feedback** - Developers know within minutes if changes break tests
- **Consistent environments** - Same testing conditions across all platforms
- **Regression prevention** - No code reaches production without passing all tests
- **Professional standards** - Industry-standard CI/CD practices for reliability

**Deployment Efficiency:**
- **Zero manual deployment** - Eliminates human error in release process
- **Instant availability** - Users can download new versions within minutes of release
- **Rollback capability** - Clear version history enables quick issue resolution
- **Scalable process** - Same pipeline works for patches, minor, and major releases

## GitHub Actions Implementation

### Workflow Architecture

**Two-Stage Pipeline:**

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

### Check Workflow (check.yml)

**Triggers:**
- **All commits** to any branch
- **All pull requests** to main/dev branches
- **Manual dispatch** for testing purposes

**Test Matrix:**
- **Operating Systems**: Ubuntu, Windows, macOS
- **Python Versions**: 3.9, 3.10, 3.11
- **Total Combinations**: 9 test environments per commit

**Workflow Steps:**
1. **Checkout code** from repository
2. **Setup Python environment** for each version
3. **Install dependencies** from requirements-dev.txt
4. **Run complete test suite** using unittest discovery
5. **Report test results** with pass/fail status

**Success Criteria:**
- **All 55+ tests pass** across all environments
- **No import errors** or dependency conflicts
- **Consistent behavior** across all platforms and Python versions

### Release Workflow (release.yml)

**Triggers:**
- **Semantic version tags** pushed to repository (e.g., 1.0.0, 1.1.0)
- **Only after check.yml succeeds** (quality gate)
- **Only from main/master branch** (production readiness)

**Workflow Steps:**
1. **Validate tag format** - Ensure semantic versioning compliance
2. **Checkout tagged code** - Use exact release version
3. **Setup build environment** - Python 3.11 with build tools
4. **Install build dependencies** - build tools and testing framework
5. **Run final test suite** - Last quality check before release
6. **Build source distribution** - Create source code archives
7. **Create GitHub release** - Generate release with tag message as notes
8. **Attach source code** - Upload .zip and .tar.gz files to release

**Quality Gates:**
- **Test suite must pass** before release begins
- **Build process must complete** without errors
- **GitHub release creation must succeed** for release to be considered complete

## Configuration Details

### Environment Variables and Secrets

**GitHub Secrets (Encrypted):**
- **`GITHUB_TOKEN`** - Automatic token for GitHub API access (creating releases)

**Environment Variables:**
- **`RELEASE_DRY_RUN`** - Set to false for actual releases
- **`PYTHON_VERSION`** - Dynamically set based on setup.py configuration

**Security Considerations:**
- **Secrets never logged** - GitHub Actions masks sensitive values
- **Limited scope** - Secrets only accessible to authorized workflows
- **Rotation capability** - Secrets can be updated without code changes

### Repository Configuration

**Branch Protection Rules:**
- **Main branch protected** - Requires passing checks before merge
- **Review requirements** - Code review process for quality assurance
- **Status checks** - CI must pass before branch can be merged

**Workflow Permissions:**
- **Contents: write** - Required for creating releases and tags
- **Actions: read** - Required for workflow execution
- **Checks: write** - Required for status reporting

## Development Workflow Integration

### Developer Experience

**Daily Development:**
1. **Create feature branch** from dev
2. **Implement changes** with accompanying tests
3. **Push commits** - Automatic testing begins
4. **Monitor CI status** - Green checkmarks indicate success
5. **Create pull request** - Automated testing validates changes
6. **Merge after approval** - Changes integrated into main codebase

**Release Process:**
1. **Complete development** on feature branches
2. **Merge to main** after full testing
3. **Create semantic version tag** with descriptive message
4. **Push tag** - Automatic release begins

### Monitoring and Feedback

**Real-time Monitoring:**
- **GitHub Actions tab** - Live workflow execution status

**Failure Handling:**
- **Clear error messages** for debugging
- **Rollback capability** - Previous versions remain available on GitHub
- **Issue tracking** - Failed releases create GitHub issues

## Performance and Reliability

### Pipeline Performance

**Typical Execution Times:**
- **Check workflow**: 4-6 minutes (parallel execution across 9 environments).
- **Release workflow**: 2-4 minutes (sequential build and release creation).
- **Total release time**: 6-10 minutes from tag push to GitHub release availability.

**Optimization Strategies:**
- **Parallel testing** - All platform/version combinations run simultaneously
- **Caching dependencies** - Faster subsequent builds
- **Minimal dependencies** - Only essential packages in requirements.txt
- **Efficient test suite** - Fast-running unit tests for quick feedback

### Reliability Measures

**Error Prevention:**
- **Comprehensive testing** - 55+ tests cover all functionality
- **Multi-environment validation** - Consistent behavior across platforms
- **Automated quality gates** - No manual release decisions.
- **Rollback procedures** - Previous versions always available on GitHub.

**Monitoring and Alerting:**
- **Build status notifications** - Immediate feedback on failures
- **Release verification** - Automated checks for successful GitHub release creation
- **User feedback integration** - GitHub issues for problem reporting.