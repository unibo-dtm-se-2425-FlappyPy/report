---
title: Development
has_children: false
nav_order: 5
---

# Development

## DVCS

### Git Workflow Strategy

**Branch Management:**
- **main branch**: Production-ready code for releases
- **dev branch**: Integration branch for completed features
- **feature branches**: Individual development work (e.g., `feature/collision-detection`, `feature/foundation`)

**Branching Conventions:**
- Feature branches created from `dev` branch
- Branch naming: `feature/descriptive-name`
- Regular merging from `dev` to keep feature branches current
- Clean merge to `dev` when features complete

### Commit Message Conventions

**Format**: `Action verb following by description`

**Commit Types:**
- `Implement`: New game components
- `Fix`: Bug fixes and corrections
- `Write`: Adding or modifying unit tests
- `Modify`: Documentation updates
- `Refactor`: Code improvements without functional changes

**Examples:**
```markdown
- Implement the sound effects and background music.
- Fix path error of loading assets for different Python versions.
- Write test for "Game Over" screen.
- Modify README and CHANGELOG to release new version 1.2.1.
```

### Release Management

**Semantic Versioning:**
- **v1.0.0**: Initial release with core gameplay mechanics
- **v1.x.x**: Future patches and minor feature additions
- **v2.x.x**: Major feature additions or breaking changes

**Release Process:**
1. Create annotated git tag: `git tag -a 'X.Y.Z' -m 'Release description'`
2. Push tag: `git push --follow-tags`
3. GitHub Actions automatically tests and deploys.

## Technical Details

### Core Technologies

**Programming Language:**
- **Python 3.9+**: Educational requirement and cross-platform compatibility
- **Object-oriented paradigm**: Clear class structure and encapsulation

**Graphics and Input:**
- **pygame 2.6.1**: Industry-standard Python game development library
- **Provides**: Graphics rendering, input handling, collision detection, timing

**Why pygame?**
- Extensive documentation and community support
- Built-in collision detection with `pygame.Rect`
- Cross-platform compatibility (Windows, macOS, Linux)
- Educational accessibility for Python developers

### Development Dependencies

**Runtime Dependencies:**
```markdown
pygame==2.6.1           # Game engin
setuptools==80.9.0      # Python package handler
```

**Development Dependencies:**
```markdown
pytest>=8.4.1   # Unit testing framework
build>=0.6.0    # Package building
twine>=3.4.2    # PyPI deployment
```

### Testing Framework

**Unit Testing:**
- **unittest**: Python's built-in testing framework
- **55+ unit tests** across 9 test modules
- **Test categories**: Foundation, Bird physics, Physics (movement and gravity), Boundary checking, Pipe generation, Collision detection, Score display, Game over display, Scoring system

**Testing Strategy:**
- Individual component testing with isolated unit tests
- Integration testing for system-wide functionality
- Automated testing via GitHub Actions CI/CD

### Build and Deployment

**Package Management:**
- `setuptools`: Python package configuration and building
- **Semantic versioning**: Git tag-based release management

**Continuous Integration:**
- **GitHub Actions**: Automated testing on multiple OS and Python versions
- **Test matrix**: Windows, macOS, Linux × Python 3.9 - 3.11
- **Deployment**: Automatic release on successful test completion

**Installation Method:**
```bash
git clone https://github.com/unibo-dtm-se-2425-FlappyPy/artifact.git
cd artifact
pip install -r requirements.txt
```

### Development Environment

**No External Services:**
- Self-contained desktop application.
- No network dependencies or external APIs.
- No database requirements.
- No authentication or authorization systems.

**Cross-Platform Support:**
- Compatible with Windows, macOS, and Linux
- Standard Python installation requirements only

### Code Organization

**Package Structure:**
```markdown
FlappyPy/                      # Main game package
├── assets/                    # Game assets
├── __init__.py                # Package initialization
├── __main__.py                # Game entry point
└── main.py                    # Complete game

test/
├── __init__.py                # Test package initialization
├── test_foundation.py         # Core game setup tests
├── test_bird.py               # Bird physics tests
├── test_physics.py            # Movement and gravity tests
├── test_boundary.py           # Screen boundary tests
├── test_pipe.py               # Pipe generation tests
├── test_collision.py          # Collision detection tests
├── test_score_display.py      # Scoring display test
├── test_game_over_display.py  # Scoring display test
└── test_scoring.py            # Scoring system tests
```