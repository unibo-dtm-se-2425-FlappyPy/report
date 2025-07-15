---
title: Developer Guide
has_children: false
nav_order: 11
---

# Developer Guide

This guide explains how new developers can join the FlappyPy development team and start contributing to the project effectively.

## Team Organization

### Project Structure

**Repository Organization:**
- **Main Repository**: `unibo-dtm-se-2425-FlappyPy/artifact` - Contains all source code and tests
- **Report Repository**: `unibo-dtm-se-2425-FlappyPy/report` - Contains project documentation

**Communication Channels:**
- **GitHub Issues**: Primary method for bug reports and feature requests
- **Pull Requests**: Code review and discussion platform
- **GitHub Discussions**: General project discussions and questions

### Issue Reporting

**Bug Reports:**
- Use GitHub Issues with "bug" label
- Include Python version, operating system, and pygame version
- Provide steps to reproduce the issue
- Include error messages and stack traces if available

**Feature Requests:**
- Use GitHub Issues with "enhancement" label
- Describe the feature and its benefits
- Consider implementation complexity and project scope
- Link to relevant requirements or user stories

**Security Issues:**
- Report security vulnerabilities privately via GitHub Security tab
- Do not disclose security issues in public GitHub Issues

## Development Environment Setup

### Prerequisites

**Required Software:**
- **Python 3.8+** - FlappyPy supports Python 3.8, 3.9, 3.10, and 3.11
- **Git** - For version control and collaboration
- **Text Editor/IDE** - VS Code, PyCharm, or similar with Python support

**Recommended Tools:**
- **GitHub CLI** - For enhanced GitHub integration
- **pytest** - Alternative testing framework (optional)
- **Black** - Code formatting tool (optional but recommended)

### Initial Setup

**1. Clone the Repository:**
```bash
git clone https://github.com/unibo-dtm-se-2425-FlappyPy/artifact.git
cd artifac
```

**2. Create Virtual Environment:**

**Create virtual environment**
```bash
python -m venv venv
```

**Activate virtual environment**
On Windows:
```bash
venv\Scripts\activate
```
On macOS/Linux:
```bash
source venv/bin/activate
```

**3. Install Dependencies:**

**Install development dependencies**

```bash
pip install -r requirements-dev.txt
```

This installs:
```markdown
- pygame==2.6.1 (game engine)
- pytest>=8.4.1 (testing framework)
- build>=0.6.0 (package building)
- twine>=3.4.2 (PyPI uploading)
```

**4. Verify Installation:**

**Run tests to verify setup**
```bash
python -m unittest discover -s test -t .
```

**Run the game to verify functionality**
```bash
python -m FlappyPy
```

### Development Environment Configuration

**VS Code Configuration:**

Create `.vscode/settings.json`:

```json
{
    "python.defaultInterpreterPath": "./venv/bin/python",
    "python.testing.unittestEnabled": true,
    "python.testing.pytestEnabled": false,
    "python.testing.unittestArgs": [
                                    "-v",
                                    "-s",
                                    "./test",
                                    "-p",
                                    "test_*.py"
                                ],
    "python.linting.enabled": true,
    "python.linting.pylintEnabled": true
}
```

**PyCharm Configuration:**
- Set Project Interpreter to virtual environment Python
- Configure Test Runner to use unittest
- Enable Git integration and GitHub plugin

## Development Workflow

### Git Workflow

**Branch Strategy:**
- **main**: Production-ready code, tagged releases only
- **dev**: Integration branch for completed features
- **feature/**: Individual feature development branches
- **hotfix/**: Emergency fixes for production issues

**Typical Development Cycle:**

**1. Start New Feature:**

**Switch to dev branch and pull latest**

```bash
git checkout dev
git pull origin dev
```

**Create feature branch**
```bash
git checkout -b feature/descriptive-name
```

Examples:
```markdown
feature/add-scoring-system
feature/improve-collision-detection
feature/add-sound-effects
```

**2. Development Process:**

**Make changes and commit frequently**
```bash
git add .
git commit -m "feat: implement basic scoring system"
```

**Push to remote regularly**
```bash
git push origin feature/descriptive-name
```

**3. Create Pull Request:**
- Create PR from feature branch to dev branch
- Include clear description of changes
- Reference related issues or requirements
- Ensure all tests pass before requesting review

**4. Code Review Process:**
- At least one team member review required
- Address feedback and push updates
- Maintain professional, constructive discussion

**5. Merge and Cleanup:**

**After PR approval and merge**
```bash
git checkout dev
git pull origin dev
git branch -d feature/descriptive-name
```

### Testing Workflow

**Test-Driven Development (TDD):**
1. **Write failing test** for new functionality
2. **Implement minimal code** to make test pass
3. **Refactor** while maintaining test coverage
4. **Repeat** for each small feature increment

**Running Tests:**

**Run all tests**
```bash
python -m unittest discover -s test -t .
```

**Run specific test file**
```bash
python -m unittest test.test_collision
```

**Run specific test method**
```bash
python -m unittest test.test_collision.TestCollisionDetection.test_bird_collision
```

**Test Coverage Expectations:**
- **100% test coverage** for new functionality
- **All existing tests must pass** before merging
- **Add tests for bug fixes** to prevent regression

## Coding Conventions

### Python Style Guide

**Follow PEP 8 Standards:**
- **Indentation**: 4 spaces (no tabs)
- **Line Length**: 79 characters maximum
- **Naming Conventions**:
  - Classes: `PascalCase` (e.g., `Bird`, `Pipe`)
  - Functions/Methods: `snake_case` (e.g., `update_position`, `check_collision`)
  - Constants: `UPPER_CASE` (e.g., `WINDOW_WIDTH`, `GRAVITY`)
  - Variables: `snake_case` (e.g., `bird_velocity`, `pipe_x`)

**Code Organization:**

**File structure for new modules:**
```markdown
1. Module docstring
2. Imports (standard library first, then third-party, then local)
3. Constants
4. Classes
5. Functions
6. Main execution block (if applicable)
```

### Project-Specific Conventions

**Game Object Design:**
- **Encapsulation**: Each game object (Bird, Pipe) manages its own state
- **Update Method**: All game objects have `update()` method for physics
- **Draw Method**: All game objects have `draw(screen)` method for rendering
- **Collision Interface**: Provide collision detection methods

**Testing Conventions:**
- **Test file naming**: `test_<module_name>.py`
- **Test class naming**: `Test<ClassName>`
- **Test method naming**: `test_<specific_behavior>`
- **Setup method**: Use `setUp()` for test initialization
- **Descriptive assertions**: Include meaningful assertion messages

**Commit Message Format:**
```markdown
type: brief description
    - Detailed explanation if needed
    - List specific changes
    - Reference issue numbers with #123
```

Types:
```markdown
feat: New feature
fix: Bug fix
test: Adding or modifying tests
docs: Documentation updates
refactor: Code improvements without functional changes
```

## Testing Procedures

### Unit Testing

**Test Structure:**
- **test/test_foundation.py**: Core game setup and constants
- **test/test_bird.py**: Bird class behavior and physics
- **test/test_physics.py**: Physics simulation and mechanics
- **test/test_boundary.py**: Screen boundary collision detection
- **test/test_pipe.py**: Pipe generation and movement
- **test/test_collision.py**: Collision detection and game state

**Writing New Tests:**

```python
import unittest
from FlappyPy.main import Bird, WINDOW_HEIGHT

class TestNewFeature(unittest.TestCase):
    def setUp(self):
        """Create test objects for each test."""
        self.bird = Bird()

    def test_specific_behavior(self):
        """Test description of what is being validated."""
        # Arrange
        initial_position = self.bird.y
        
        # Act
        self.bird.jump()
        
        # Assert
        self.assertLess(self.bird.velocity, 0, 
                    "Jump should create upward velocity")
```

### Integration Testing

**Component Integration:**
- Test Bird + Physics interaction
- Test Collision Detection + Game State
- Test Pipe Generation + Movement systems
- Test Input Handling + Game Response

**System Testing:**
- Complete gameplay cycles
- Multi-platform compatibility
- Performance under load
- Error handling and recovery

### Continuous Integration

**GitHub Actions Workflow:**
- **Automatic testing** on all commits and pull requests
- **Multi-platform testing** (Windows, macOS, Linux)
- **Multi-version testing** (Python 3.8-3.11)
- **Deployment gate** - releases only after all tests pass

**Local Pre-commit Testing:**

**Run complete test suite before committing**
```bash
python -m unittest discover -s test -t .
```

**Check for any import errors**
```bash
python -c "import FlappyPy; print('Import successful')"
```

**Test game launch**
```bash
python -m FlappyPy
```

## Release Procedures

### Version Management

**Semantic Versioning:**
- **MAJOR.MINOR.PATCH** format (e.g., 1.0.0)
- **PATCH**: Bug fixes and small improvements
- **MINOR**: New features, backward compatible
- **MAJOR**: Breaking changes or major rewrites

**Release Process:**

**1. Prepare Release:**

**Ensure all changes are merged to main**
```bash
git checkout main
git pull origin main
```

**Run complete test suite**
```bash
python -m unittest discover -s test -t .
```

**Update documentation if needed**

**2. Create Release Tag:**

**Create annotated tag**
```bash
git tag -a 'X.Y.Z' -m 'Release X.Y.Z
                        - Feature 1: Description
                        - Feature 2: Description
                        - Bug fix: Description'
```

**Push tag** (triggers automated deployment)
```bash
git push --follow-tags
```

**3. Monitor Deployment:**
- Check GitHub Actions for successful deployment
- Verify package appears on PyPI
- Test installation: `pip install FlappyPy==X.Y.Z`

### Quality Assurance

**Pre-release Checklist:**
- [ ] All unit tests pass (44+ tests)
- [ ] Integration tests complete successfully
- [ ] Game runs without errors on all platforms
- [ ] Performance meets 60 FPS target
- [ ] Documentation updated and accurate
- [ ] Version number follows semantic versioning

**Post-release Verification:**
- [ ] PyPI package installs correctly
- [ ] Game launches via `python -m FlappyPy`
- [ ] All gameplay mechanics function properly
- [ ] No regression in existing functionality

## Development Tools

### Recommended IDE Setup

**VS Code Extensions:**
- **Python** - Microsoft's official Python extension
- **Pylint** - Python linting and error detection
- **GitLens** - Enhanced Git integration
- **Python Test Explorer** - Visual test runner

**PyCharm Configuration:**
- **Professional or Community Edition** both work well
- **Enable Git integration** for version control
- **Configure Python interpreter** to virtual environment
- **Set up test runner** for unittest framework

### Command Line Tools

**Essential Commands:**

Package management
```bash
pip install -r requirements-dev.txt
pip list # Show installed packages
```

Testing
```bash
python -m unittest discover -s test -t .
python -m unittest test.test_collision -v
```

Game execution
```bash
python -m FlappyPy
```

Package building (for testing)
```bash
python -m build
python -m twine check dist/*
```

### Debugging Tools

**Common Debugging Techniques:**
- **Print statements** for simple debugging
- **Python debugger (pdb)** for complex issues
- **IDE debugger** for step-through debugging
- **Logging** for production debugging

**Game-Specific Debugging:**
- **Visual debugging** - Use pygame draw functions for collision boxes
- **Frame rate monitoring** - Check FPS consistency
- **State logging** - Track game state changes
- **Input validation** - Verify event handling

## Getting Help

### Internal Resources

**Code Documentation:**
- **README.md** - Project overview and setup instructions
- **Docstrings** - Function and class documentation
- **Comments** - Inline code explanations
- **Test files** - Examples of expected behavior

**Project History:**
- **Git log** - Complete development history
- **GitHub Issues** - Past problems and solutions
- **Pull Requests** - Code review discussions
- **Release notes** - Version change summaries

### External Resources

**Python and pygame:**
- **pygame documentation** - Official pygame library docs
- **Python documentation** - Standard library reference
- **Stack Overflow** - Community Q&A for specific problems

**Development Tools:**
- **Git documentation** - Version control best practices
- **GitHub Docs** - Platform-specific features
- **pytest documentation** - Alternative testing framework

### Support Channels

**For Technical Issues:**
- **GitHub Issues** - Public bug reports and feature requests
- **Code Review** - Pull request discussions
- **Direct Communication** - Contact team leads for urgent issues

**For Learning:**
- **Pair Programming** - Work with experienced team members
- **Code Reviews** - Learn from feedback on your contributions
- **Documentation** - Study existing code and tests
