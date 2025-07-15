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
- **feature branches**: Individual development work (e.g., `feature/collision-detection`, `feature/pipe-obstacles`)

**Branching Conventions:**
- Feature branches created from `dev` branch
- Branch naming: `feature/descriptive-name`
- Regular merging from `dev` to keep feature branches current
- Clean merge to `dev` when features complete

### Commit Message Conventions

**Format**: `type: description`

**Commit Types:**
- `feat`: New game features (collision detection, pipe generation)
- `fix`: Bug fixes and corrections
- `test`: Adding or modifying unit tests
- `docs`: Documentation updates
- `refactor`: Code improvements without functional changes

**Examples:**
```markdown
- feat: implement collision detection for pipes and ground
- fix: resolve bird falling through bottom boundary
- test: add comprehensive boundary collision tests
- docs: update README with installation instructions
```


### Release Management

**Semantic Versioning:**
- **v1.0.0**: Initial release with core gameplay mechanics
- **v1.x.x**: Future patches and minor feature additions
- **v2.x.x**: Major feature additions or breaking changes

**Release Process:**
1. Create annotated git tag: `git tag -a 'X.Y.Z' -m 'Release description'`
2. Push tag: `git push --follow-tags`
3. GitHub Actions automatically deploys to PyPI

## Implementation Details

### Game Architecture Patterns

**Main Game Loop Pattern:**
- Event-driven architecture using pygame's event system
- Single-threaded execution with frame-based timing
- Sequential processing: Input → Physics → Collision → Render

**Object-Oriented Design:**
- `Bird` class encapsulates player entity behavior
- `Pipe` class manages obstacle generation and movement
- Clean separation of concerns between game objects

**Collision Detection Algorithm:**
- Rectangle-based collision using `pygame.Rect.colliderect()`
- Separate collision methods for different object types
- Frame-perfect collision detection for responsive gameplay

### Data Management

**Runtime Data Structure:**
- Game state stored in local variables within main loop
- Pipe obstacles managed in Python list structure
- No persistent storage in v1.0.0 (session-based gameplay)

**Memory Management:**
- Automatic cleanup of off-screen game objects
- Python garbage collection handles object lifecycle
- No memory leaks through proper list management

## Technological Details

### Core Technologies

**Programming Language:**
- **Python 3.8+**: Educational requirement and cross-platform compatibility
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
pygame==2.6.1
setuptools==80.9.0
```

**Development Dependencies:**
```markdown
pytest>=8.4.1 # Unit testing framework
build>=0.6.0 # Package building
twine>=3.4.2 # PyPI deployment
```

### Testing Framework

**Unit Testing:**
- **unittest**: Python's built-in testing framework
- **44+ comprehensive tests** across 6 test modules
- **Test categories**: Foundation, Bird physics, Collision detection, Boundary checking, Pipe generation

**Testing Strategy:**
- Test-driven development approach
- Individual component testing with isolated unit tests
- Integration testing for system-wide functionality
- Automated testing via GitHub Actions CI/CD

### Build and Deployment

**Package Management:**
- **setuptools**: Python package configuration and building
- **PyPI distribution**: Automated release via GitHub Actions
- **Semantic versioning**: Git tag-based release management

**Continuous Integration:**
- **GitHub Actions**: Automated testing on multiple OS and Python versions
- **Test matrix**: Windows, macOS, Linux × Python 3.8-3.11
- **Deployment**: Automatic PyPI release on successful test completion

**Installation Method:**
```markdown
pip install FlappyPy
python -m FlappyPy
```

### Development Environment

**No External Services:**
- Self-contained desktop application
- No network dependencies or external APIs
- No database requirements
- No authentication or authorization systems

**Cross-Platform Support:**
- Compatible with Windows, macOS, and Linux
- Consistent gameplay experience across platforms
- Standard Python installation requirements only

### Code Organization

**Package Structure:**
```markdown
FlappyPy/
├── init.py # Package initialization
├── main.py # Entry point for python -m FlappyPy
└── main.py # Complete game implementation

test/
├── test_foundation.py # Core game setup tests
├── test_bird.py # Bird physics tests
├── test_physics.py # Movement and gravity tests
├── test_boundary.py # Screen boundary tests
├── test_pipe.py # Pipe generation tests
└── test_collision.py # Collision detection tests
```

**Design Principles:**
- **Single responsibility**: Each class handles one aspect of gameplay
- **Encapsulation**: Game objects manage their own state and behavior
- **Testability**: Clean interfaces enable comprehensive unit testing
- **Maintainability**: Clear code structure for educational purposes
