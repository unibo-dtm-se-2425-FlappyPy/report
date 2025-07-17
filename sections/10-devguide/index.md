---
title: Developer Guide
has_children: false
nav_order: 11
---

# Developer Guide

This guide explains how to contribute to the FlappyPy project.

## Development Environment Setup

**Required Software:**
- **Python 3.9+** - FlappyPy supports Python 3.9, 3.10, and 3.11
- **Git** - For version control and collaboration

**Setup:**
```bash
git clone https://github.com/unibo-dtm-se-2425-FlappyPy/artifact.git
cd artifact
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

**Verify Installation:**
```bash
python -m unittest discover -s test -t .
python -m FlappyPy
```

## Development Workflow

**Branch Strategy:**
- **main**: Production-ready code with tagged releases
- **dev**: Integration branch for completed features
- **feature/**: Individual feature development branches

**Development Process:**
1. Create feature branch from dev: `git checkout -b feature/descriptive-name`
2. Make changes and commit: `git commit -m "feat: description"`
3. Create pull request to dev branch
4. Code review and merge after tests pass

## Testing

**Test Structure:**
- **test/test_foundation.py**: Core game setup (6 tests)
- **test/test_bird.py**: Bird physics (4 tests)
- **test/test_physics.py**: Movement mechanics (7 tests)
- **test/test_boundary.py**: Screen boundaries (8 tests)
- **test/test_pipe.py**: Obstacle generation (8 tests)
- **test/test_collision.py**: Collision detection (9 tests)
- **test/test_score_display.py**: Score rendering (4 tests)
- **test/test_game_over_display.py**: Game over screen (3 tests)
- **test/test_scoring.py**: Score calculation (6 tests)

**Running Tests:**
```bash
python -m unittest discover -s test -t .  # Run all 55+ tests
python -m unittest test.test_collision     # Run specific test file
```

**TDD for Scoring System:** The scoring components follow Test-Driven Development practices.

## Coding Conventions

**Python Style Guide (PEP 8):**
- **Indentation**: 4 spaces
- **Line Length**: 79 characters maximum
- **Naming**: `PascalCase` for classes, `snake_case` for functions/variables, `UPPER_CASE` for constants

**Commit Message Format:**
```
type: brief description
```

Types: `feat`, `fix`, `test`, `docs`, `refactor`

## Release Process

**Version Management:** Semantic versioning (MAJOR.MINOR.PATCH)

**Release Steps:**
1. Merge all changes to main branch
2. Run complete test suite: `python -m unittest discover -s test -t .`
3. Create annotated tag: `git tag -a 'X.Y.Z' -m 'Release description'`
4. Push tag: `git push --follow-tags`
5. GitHub Actions automatically creates GitHub release

**Quality Gates:**
- All 55+ tests must pass
- Game runs without errors on all platforms
- Performance meets 60 FPS target

## Getting Help

**Resources:**
- **GitHub Issues** - Bug reports and feature requests
- **Pull Requests** - Code review and discussions
- **README.md** - Project overview and setup instructions
