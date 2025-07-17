---
title: Release
has_children: false
nav_order: 7
---

# Release

## Artifacts and Distribution

**Single Artifact: Python Package**

FlappyPy produces **one primary artifact** from the project codebase:

- **Python Package (.whl and .tar.gz)** - Complete game distribution with all dependencies specified.
- **Contents**: Game logic, assets, entry point, and metadata for pip installation.
- **Size**: Lightweight package (~1MB) with minimal dependencies.

**Repository Distribution:**

**GitHub Releases (Primary Distribution)**
- **Primary distribution channel** for FlappyPy releases.
- **Installation method**: Download source code from GitHub releases page.
- **Access**: `git clone https://github.com/unibo-dtm-se-2425-FlappyPy/artifact.git`.
- **Manual installation**: `pip install -r requirements.txt` after download.

**PyPI (Python Package Index) - Future Implementation**
- **Planned distribution channel** for future releases.
- **Future installation command**: `pip install FlappyPy` (*not yet available*).
- **Status**: Implementation planned for future versions.
- **Benefits**: Will provide automatic dependency management when implemented.

**Why GitHub Releases First?**
- **Educational project phase** - Suitable for current development stage.
- **Direct access to source** - Students and developers can examine complete codebase.
- **Version control integration** - Releases directly tied to git tags.
- **No packaging complexity** - Simpler distribution during development phase.

## Release Process

**Automated Release via GitHub Actions**

**Trigger Method: Git Tag-Based Deployment**
1. **Developer creates semantic version tag**: `git tag -a 'X.Y.Z' -m 'Release description'`
2. **Push tag to GitHub**: `git push --follow-tags`
3. **GitHub Actions automatically activated** by tag push event.
4. **Automated pipeline executes**: Test → Build → Deploy.

**Release Pipeline Steps:**
1. **Checkout code** from tagged commit.
2. **Install dependencies** (pytest, build tools).
3. **Run complete test suite** (55+ tests across multiple Python versions).
4. **Build source distribution** (prepare code artifacts).
5. **Create GitHub release** with tag description as release notes.
6. **Attach source code** (.zip and .tar.gz) to release.

**Configuration Requirements:**
- **Repository permissions**: GitHub Actions needs write access for releases.
- **GitHub token**: Stored as GitHub Secrets for release creation.
- **Workflow files**: `.github/workflows/deploy.yml` and `.github/workflows/check.yml` handles entire process.

## Choice of the License

**Apache License Version 2.0 Selected for Both Code and Artifacts**

**For FlappyPy Code Repository:**
- **License**: Apache License Version 2.0, January 2004
- **Rationale**: 
  - **Educational project** - Permissive license encourages learning and modification.
  - **Maximum accessibility** - Students and developers can freely use and study code.
  - **Commercial-friendly** - Allows future commercial use if desired.
  - **Patent protection** - Provides explicit patent grant and protection.
  - **Industry standard** - Widely recognized and understood by developers.

**For FlappyPy Package Distribution:**
- **License**: Apache License Version 2.0 (consistent with source code)
- **Rationale**:
  - **Consistency** - Same license for source and distributed package.
  - **User clarity** - No confusion about usage rights.
  - **Pygame compatibility** - Apache 2.0 license compatible with pygame's licensing.
  - **Distribution simplicity** - No licensing complications for end users.
  - **Legal clarity** - Comprehensive terms and conditions for enterprise use.

**License Benefits:**
- **Freedom to modify** - Users can customize game for learning purposes.
- **Attribution requirement** - Maintains credit to original development.
- **Patent grant** - Explicit patent rights granted to users.
- **Liability protection** - Standard software warranty disclaimers.
- **Open source compliance** - Meets educational and professional open source standards.

## Choice of the Versioning Schema

**Semantic Versioning (SemVer) Schema**

**Format: MAJOR.MINOR.PATCH (e.g., 1.0.0)**

**Versioning Rules:**
- **MAJOR**: Increment for breaking changes or complete rewrites.
- **MINOR**: Increment for new features that maintain backward compatibility.
- **PATCH**: Increment for bug fixes and small improvements.

**FlappyPy Version Strategy:**
- **1.0.0**: Initial release with core gameplay mechanics.
- **1.0.x**: Bug fixes and small improvements (collision detection fixes, performance improvements).
- **1.x.0**: New features (scoring system, sound effects, visual improvements).
- **2.0.0**: Major architectural changes or complete feature overhauls.

**Why Semantic Versioning?**
- **Industry standard** - Widely understood by Python developers.
- **Predictable updates** - Users understand impact of version changes.
- **Dependency management** - pip and other tools work well with SemVer.
- **Educational value** - Demonstrates professional versioning practices.

## Version Creation Process

**When to Create New Versions:**

**Patch Release (1.0.x):**
- **Trigger**: Bug fixes, performance improvements, minor corrections
- **Examples**: 
  - Fix collision detection accuracy
  - Resolve bird falling through boundaries
  - Improve frame rate stability
- **Timeline**: As needed when bugs are discovered and fixed.

**Minor Release (1.x.0):**
- **Trigger**: New features that don't break existing functionality
- **Examples**:
  - Add scoring system
  - Implement sound effects
  - Add start screen or game over screen
- **Timeline**: Planned feature releases.

**Major Release (2.0.0):**
- **Trigger**: Breaking changes or major architectural overhauls
- **Examples**:
  - Complete graphics system rewrite
  - Multiplayer functionality
  - Major API changes
- **Timeline**: Rare, only for significant project evolution.

**Technical Release Steps:**

**1. Development and Testing:**
**Complete development work on feature branch**
```bash
git checkout feature/new-feature
```
**Implement and test changes**
```bash
git add .
git commit -m "Implement new feature"
```

**2. Integration and Validation:**
**Merge to dev branch**
```bash
git checkout dev
git merge feature/new-feature
```
**Run complete test suite**
```bash
python -m unittest discover -s test -t .
```

**3. Release Preparation:**
**Merge to main branch**
```bash
git checkout main
git merge dev
```
**Ensure all tests pass**
```bash
python -m unittest discover -s test -t .
```

**4. Version Tag Creation:**
**Create annotated tag with semantic version**
```bash
git tag -a 'X.Y.Z' -m 'Changelogs'
```

**5. Automated Deployment:**

**Push tag to trigger automated release**
```bash
git push --follow-tags
```
**GitHub Actions handles the rest automatically**