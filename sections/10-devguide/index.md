---
title: Developer Guide
has_children: false
nav_order: 11
---

# Developer Guide

## Environment and Workflow

FlappyPy embraces **educational-friendly development practices** that demonstrate professional software engineering while maintaining accessibility for learning purposes. The environment setup requires Python 3.9+ and git for collaborative development, followed by virtual environment creation and dependency installation for immediate development readiness.

```bash
git clone https://github.com/unibo-dtm-se-2425-FlappyPy/artifact.git
cd artifact
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
python -m unittest discover -s test -t .  # Verify 55+ tests pass
```

The **structured branching strategy** employs main for production releases, dev for feature integration, and descriptive feature branches for individual development work, ensuring clear separation between development stages and automated GitHub Actions integration for quality assurance.

## Testing and Code Quality

The comprehensive **55+ test suite spans 9 modules** covering foundation systems, bird physics, collision detection, scoring mechanisms, and display components, with the scoring system uniquely demonstrating Test-Driven Development methodology for educational value. Testing follows Python's unittest framework with discovery-based execution enabling both complete suite validation and targeted module testing for efficient development cycles.

**Development Standards:**
- PEP 8 compliance with 4-space indentation and 79-character line limits
- Semantic commit messages (please! I know I've not used, but for any pull request it would be helpfull.): `feat:`, `fix:`, `test:`, `docs:`, `refactor:`
- Code review requirements before dev branch integration

## Release and Collaboration

**Automated release management** leverages semantic versioning with GitHub Actions integration, where annotated tags trigger comprehensive testing validation followed by automatic GitHub release creation. The quality-gated process ensures all 55+ tests pass across multiple platforms before any code reaches production, demonstrating professional CI/CD practices essential for educational software engineering understanding.

Development collaboration utilizes GitHub Issues for bug reports and feature requests, while Pull Requests facilitate code review discussions and maintain project quality standards through peer review processes.
