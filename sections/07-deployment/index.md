---
title: Deployment
has_children: false
nav_order: 8
---

# Deployment

## User Installation

**FlappyPy requires Python environment setup and package installation on the user's machine.**

### Prerequisites

**Required Software:**
- **Python 3.9 or higher** - FlappyPy is compatible with Python 3.9, 3.10, and 3.11
- **pip package manager** - Usually included with Python installations
- **Operating System**: Windows, macOS, or Linux

**Installation Commands:**

**Install FlappyPy from GitHub Releases (Current Method)**
```bash
git clone https://github.com/unibo-dtm-se-2425-FlappyPy/artifact.git
cd artifact
pip install -r requirements.txt
```

**Future PyPI Installation (Not Yet Available)**
```bash
pip install FlappyPy  # Not yet implemented
```

**Manual Dependency Installation:**
- **pygame 2.6.1** - Graphics and input handling library (install via requirements.txt)
- **setuptools** - Package management utilities (install via requirements.txt)

### Configuration

**No Configuration Required:**
- **Zero configuration** - FlappyPy runs immediately after installation
- **No config files** - No settings files to create or modify
- **No environment variables** - No system environment setup needed
- **Ready to play** - Game launches with default settings

### Launch Instructions

**Running FlappyPy:**
**Launch the game**
```bash
cd artifact
python -m FlappyPy
```

**What happens:**
1. **Game window opens** - 400x600 pixel window appears
2. **Immediate gameplay** - Bird appears and responds to spacebar input
3. **No setup menus** - Game starts in playable state immediately

### Verification

**Test Installation:**
**Verify installation**
```bash
cd artifact
python -c "import FlappyPy; print('FlappyPy installed successfully')"
```
**Test game launch (should open game window)**
```bash
cd artifact
python -m FlappyPy
```

**Expected Results:**
- **No error messages** during installation
- **Game window opens** without crashes
- **Spacebar input responsive** - Bird jumps when pressed
- **Smooth 60 FPS gameplay** - No lag or stuttering

### Platform-Specific Notes

**Windows:**
- **Python installation**: Download from python.org or use Microsoft Store
- **Command prompt**: Use cmd or PowerShell for installation commands
- **No additional dependencies** - pygame binaries included in package

**macOS:**
- **Python installation**: Download from python.org or use Homebrew
- **Terminal**: Use Terminal.app for installation commands
- **No additional dependencies** - pygame binaries included in package

**Linux:**
- **Python installation**: Usually pre-installed, or use package manager
- **Additional packages**: May need `python3-dev` for pygame compilation
- **Installation example**: `sudo apt-get install python3-dev` (Ubuntu/Debian)

## Server-Side Installation

**Not Applicable: FlappyPy is a Desktop Application**

## Deployment Verification

**User Experience Validation:**

**Installation Test Checklist:**
- ✅ **Python 3.9+ available** - `python --version` shows compatible version
- ✅ **Git functioning** - `git --version` shows working version control
- ✅ **pip functioning** - `pip --version` shows working package manager
- ✅ **FlappyPy clones** - `git clone` completes without errors
- ✅ **Dependencies install** - `pip install -r requirements.txt` completes without errors
- ✅ **Game launches** - `python -m FlappyPy` opens game window
- ✅ **Gameplay works** - Spacebar input produces bird movement
- ✅ **Physics active** - Bird falls due to gravity when not jumping
- ✅ **Collision detection** - Game over occurs when bird hits pipes or ground
- ✅ **Restart functions** - Spacebar restarts game after game over

**Cross-Platform Validation:**
- **Windows testing** - Verified on Windows 10/11 systems
- **macOS testing** - Verified on macOS 10.15+ systems  
- **Linux testing** - Verified on Ubuntu 20.04+ and similar distributions
- **Python version testing** - Verified on Python 3.9, 3.10, 3.11

**Success Criteria:**
- **100% installation success rate** across supported platforms
- **Immediate gameplay** - Minimal setup required after git clone
- **Consistent performance** - 60 FPS gameplay on all platforms
- **Manual configuration only** - Dependencies installed via requirements.txt
