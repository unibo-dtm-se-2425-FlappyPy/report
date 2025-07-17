---
title: Development
has_children: false
nav_order: 5
---

# Development

## Development Approach

FlappyPy employs a **Hybrid Development Methodology** that strategically combines conventional development practices with Test-Driven Development based on component complexity and educational value. The majority of core game components including foundation systems, bird physics, collision detection, and pipe generation were developed using conventional methodology involving requirements analysis, implementation-first approach, comprehensive post-implementation testing, and iterative refinement for quality improvement.

The **scoring system** uniquely demonstrates systematic Test-Driven Development methodology, beginning with failing test cases that define expected scoring behavior, implementing minimal code to achieve test passage, refactoring for clean logic while maintaining coverage, and building features incrementally with continuous validation. This selective TDD approach provides educational value while maintaining development efficiency for the broader system.

## Version Control Strategy

### Git Workflow and Release Management

The project employs a structured branching strategy with **main branch** for production releases, **dev branch** for feature integration, and **feature branches** for individual development work following `feature/descriptive-name` conventions. The release process utilizes semantic versioning with annotated git tags, automated GitHub Actions testing and deployment, culminating in **GitHub releases** for package distribution.

**Commit conventions** follow action-verb patterns including Implement for new components, Fix for corrections, Write for test modifications, and Modify for documentation updates, ensuring clear development history and professional collaboration standards.

## Technical Implementation

### Core Technologies and Dependencies

FlappyPy leverages **Python 3.9+** for educational accessibility and cross-platform compatibility, implementing object-oriented paradigms with clear class structure and encapsulation. The graphics foundation utilizes **pygame 2.6.1** as the industry-standard Python game development library, providing comprehensive graphics rendering, input handling, collision detection, and timing capabilities with extensive documentation and built-in collision detection through `pygame.Rect`.

**Development Dependencies:**
- Runtime: `pygame==2.6.1`, `setuptools==80.9.0`
- Development: `pytest>=8.4.1`, `build>=0.6.0` for package building
- GitHub releases deployment (replacing previous PyPI approach)

### Testing and Quality Assurance

The comprehensive testing strategy employs **Python's unittest framework** with **55+ unit tests across 9 test modules** covering Foundation, Bird physics, Physics systems, Boundary checking, Pipe generation, Collision detection, Score display, Game over display, and Scoring system components. Testing includes individual component isolation, integration testing for system-wide functionality, and automated validation through GitHub Actions CI/CD across Windows, macOS, and Linux platforms with Python 3.9-3.11 compatibility.

### Deployment and Environment

The project architecture emphasizes simplicity and educational accessibility through a **self-contained desktop application** requiring no external services, network dependencies, databases, or authentication systems. Cross-platform support ensures compatibility across Windows, macOS, and Linux with standard Python installation requirements.

**Package management** utilizes setuptools for configuration and building with git tag-based semantic versioning, while **continuous integration** through GitHub Actions provides automated testing across multiple operating systems and Python versions, with automatic **GitHub releases** upon successful test completion.

**Installation follows GitHub-based workflow:**
```bash
git clone https://github.com/unibo-dtm-se-2425-FlappyPy/artifact.git
cd artifact
pip install -r requirements.txt
```

### Code Organization

The package structure maintains clear separation between game logic and testing components:

```markdown
FlappyPy/                      # Main game package
├── assets/                    # Game assets
├── __init__.py                # Package initialization
├── __main__.py                # Game entry point
└── main.py                    # Complete game

test/                          # Comprehensive testing suite
├── test_foundation.py         # Core game setup tests
├── test_bird.py               # Bird physics tests
├── test_physics.py            # Movement and gravity tests
├── test_boundary.py           # Screen boundary tests
├── test_pipe.py               # Pipe generation tests
├── test_collision.py          # Collision detection tests
├── test_score_display.py      # Scoring display tests
├── test_game_over_display.py  # Game over display tests
└── test_scoring.py            # Scoring system tests
```