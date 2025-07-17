---
title: Release
has_children: false
nav_order: 7
---

# Release

## Artifacts and Distribution

FlappyPy delivers a **lightweight Python package** (~1MB) containing complete game logic, assets, and entry point metadata optimized for educational accessibility. The primary distribution leverages **GitHub Releases** as the educational-friendly channel, enabling students and developers to examine the complete codebase while maintaining direct version control integration through git tags.

**Distribution Strategy:**
- **GitHub Releases**: `git clone https://github.com/unibo-dtm-se-2425-FlappyPy/artifact.git`
- **Installation**: `pip install -r requirements.txt` after download
- **Future PyPI**: Planned for enhanced dependency management

GitHub-first distribution eliminates packaging complexity during the educational project phase while providing transparent access to source code and simplified deployment through tag-based releases.

## Release Process

The **automated GitHub Actions pipeline** transforms semantic version tags into production releases through a streamlined workflow. Developers create annotated tags (`git tag -a 'X.Y.Z' -m 'Release description'`) that trigger comprehensive testing across 55+ tests and multiple Python versions, followed by source distribution building and automatic GitHub release creation with attached artifacts.

**Pipeline Configuration:**
- Repository permissions for GitHub Actions write access
- GitHub token stored as secrets for release creation
- Workflow files: `.github/workflows/deploy.yml` and `.github/workflows/check.yml`

## Choice of the License

**Apache License Version 2.0** governs both source code and distributed artifacts, providing comprehensive legal framework that encourages educational use while maintaining commercial viability. This permissive licensing approach maximizes accessibility for students and developers, ensures pygame library compatibility, and delivers explicit patent protection alongside standard liability disclaimers.

The consistent licensing strategy eliminates user confusion while supporting the educational mission through clear attribution requirements and modification freedoms essential for learning environments.

## Versioning Strategy

FlappyPy employs **Semantic Versioning (MAJOR.MINOR.PATCH)** to communicate change impact clearly to Python developers and educational users. This industry-standard approach ensures predictable dependency management while demonstrating professional versioning practices essential for software engineering education.

**Version Evolution:**
- **1.0.0**: Initial release with core gameplay mechanics
- **1.0.x**: Bug fixes (collision detection, boundary handling)  
- **1.x.0**: New features (scoring system, visual improvements)
- **2.0.0**: Major architectural changes or complete overhauls

## Version Creation Process

The structured release workflow begins with feature development on dedicated branches, progresses through integration testing on the dev branch, and culminates with main branch merging followed by comprehensive test suite validation. Version creation follows a precise tagging process where annotated semantic tags trigger automated GitHub Actions deployment.

**Technical Release Workflow:**

```bash
# Feature Development
git checkout feature/new-feature
git add . && git commit -m "Implement new feature"

# Integration Testing  
git checkout dev && git merge feature/new-feature
python -m unittest discover -s test -t .

# Release Preparation
git checkout main && git merge dev
python -m unittest discover -s test -t .

# Version Creation and Deployment
git tag -a 'X.Y.Z' -m 'Release description'
git push --follow-tags
```

**Release Types:**
- **Patch (1.0.x)**: Bug fixes and performance improvements
- **Minor (1.x.0)**: New features maintaining backward compatibility
- **Major (2.0.0)**: Breaking changes or architectural overhauls