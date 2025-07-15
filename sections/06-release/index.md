---
title: Release
has_children: false
nav_order: 7
---

# Release

## Artifacts and Distribution

**Single Artifact: Python Package**

FlappyPy produces **one primary artifact** from the project codebase:

- **Python Package (.whl and .tar.gz)** - Complete game distribution with all dependencies specified
- **Contents**: Game logic, assets, entry point, and metadata for pip installation
- **Size**: Lightweight package (~10KB) with minimal dependencies

**Repository Distribution:**

**PyPI (Python Package Index)**
- **Primary distribution channel** for FlappyPy releases
- **Installation command**: `pip install FlappyPy`
- **Global accessibility** - Available worldwide for Python developers
- **Automatic dependency management** - pip handles pygame installation

**Why PyPI?**
- **Standard Python distribution** - Expected channel for Python packages
- **Educational accessibility** - Easy installation for students and developers
- **Professional credibility** - Demonstrates proper packaging practices
- **Automated integration** - Works seamlessly with Python development workflows

## Release Process

**Automated Release via GitHub Actions**

**Trigger Method: Git Tag-Based Deployment**
1. **Developer creates semantic version tag**: `git tag -a 'X.Y.Z' -m 'Release description'`
2. **Push tag to GitHub**: `git push --follow-tags`
3. **GitHub Actions automatically activated** by tag push event
4. **Automated pipeline executes**: Test → Build → Deploy

**Release Pipeline Steps:**
1. **Checkout code** from tagged commit
2. **Install dependencies** (pytest, build, twine)
3. **Run complete test suite** (44+ tests across multiple Python versions)
4. **Build package artifacts** (.whl and .tar.gz)
5. **Deploy to PyPI** using automated credentials
6. **Create GitHub release** with tag description as release notes

**Configuration Requirements:**
- **Repository permissions**: GitHub Actions needs write access for releases
- **PyPI credentials**: Stored as GitHub Secrets for secure deployment
- **Workflow files**: `.github/workflows/deploy.yml` handles entire process

**Benefits of Automated Release:**
- **Consistent process** - Same steps executed every time
- **Quality assurance** - Tests must pass before deployment
- **Immediate availability** - Package available within minutes of tag creation
- **Error prevention** - Automated process reduces human mistakes

## Choice of the License

**MIT License Selected for Both Code and Artifacts**

**For FlappyPy Code Repository:**
- **License**: MIT License
- **Rationale**: 
  - **Educational project** - Permissive license encourages learning and modification
  - **Maximum accessibility** - Students and developers can freely use and study code
  - **Commercial-friendly** - Allows future commercial use if desired
  - **Industry standard** - Widely recognized and understood by developers

**For FlappyPy Package Distribution:**
- **License**: MIT License (consistent with source code)
- **Rationale**:
  - **Consistency** - Same license for source and distributed package
  - **User clarity** - No confusion about usage rights
  - **Pygame compatibility** - MIT license compatible with pygame's licensing
  - **Distribution simplicity** - No licensing complications for end users

**License Benefits:**
- **Freedom to modify** - Users can customize game for learning purposes
- **Attribution requirement** - Maintains credit to original development
- **Liability protection** - Standard software warranty disclaimers
- **Open source compliance** - Meets educational and professional open source standards

## Choice of the Versioning Schema

**Semantic Versioning (SemVer) Schema**

**Format: MAJOR.MINOR.PATCH (e.g., 1.0.0)**

**Versioning Rules:**
- **MAJOR**: Increment for breaking changes or complete rewrites
- **MINOR**: Increment for new features that maintain backward compatibility
- **PATCH**: Increment for bug fixes and small improvements

**FlappyPy Version Strategy:**
- **1.0.0**: Initial release with core gameplay mechanics
- **1.0.x**: Bug fixes and small improvements (collision detection fixes, performance improvements)
- **1.x.0**: New features (scoring system, sound effects, visual improvements)
- **2.0.0**: Major architectural changes or complete feature overhauls

**Why Semantic Versioning?**
- **Industry standard** - Widely understood by Python developers
- **Predictable updates** - Users understand impact of version changes
- **Dependency management** - pip and other tools work well with SemVer
- **Educational value** - Demonstrates professional versioning practices

**Single Artifact Versioning:**
- **Unified versioning** - One version number for the entire package
- **Git tag alignment** - Version tags directly correspond to releases
- **No complexity** - Simple versioning since only one artifact is produced

## Version Creation Process

**When to Create New Versions:**

**Patch Release (1.0.x):**
- **Trigger**: Bug fixes, performance improvements, minor corrections
- **Examples**: 
  - Fix collision detection accuracy
  - Resolve bird falling through boundaries
  - Improve frame rate stability
- **Timeline**: As needed when bugs are discovered and fixed

**Minor Release (1.x.0):**
- **Trigger**: New features that don't break existing functionality
- **Examples**:
  - Add scoring system
  - Implement sound effects
  - Add start screen or game over screen
- **Timeline**: Planned feature releases, typically monthly or quarterly

**Major Release (2.0.0):**
- **Trigger**: Breaking changes or major architectural overhauls
- **Examples**:
  - Complete graphics system rewrite
  - Multiplayer functionality
  - Major API changes
- **Timeline**: Rare, only for significant project evolution

**Technical Release Steps:**

**1. Development and Testing:**
**Complete development work on feature branch**
```markdown
git checkout feature/new-feature
```
**Implement and test changes**
```markdown
git add .
git commit -m "feat: implement new feature"
```

**2. Integration and Validation:**
**Merge to dev branch**
```markdown
git checkout dev
git merge feature/new-feature
```
**Run complete test suite**
```markdown
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
git tag -a '1.1.0' -m 'Add scoring system and sound effects
   - Implement point counting when bird passes through pipes.
   - Add jump and collision sound effects.
   - Display current score during gameplay.
   - Update UI with score visualization'.
```

**5. Automated Deployment:**

**Push tag to trigger automated release**
```bash
git push --follow-tags
```
**GitHub Actions handles the rest automatically**

**Version Management Best Practices:**
- **Clear commit messages** - Enable accurate version determination
- **Comprehensive testing** - All tests must pass before tagging
- **Descriptive tag messages** - Serve as release notes for users
- **Regular releases** - Maintain momentum and user engagement
- **Documentation updates** - Keep README and docs aligned with versions

**Release Monitoring:**
- **GitHub Actions status** - Monitor deployment pipeline success
- **PyPI package availability** - Verify successful upload
- **Installation testing** - Confirm `pip install FlappyPy` works correctly
- **User feedback** - Monitor for any release-related issues
