---
title: Deployment
has_children: false
nav_order: 8
---

# Deployment

## User Installation

FlappyPy delivers **zero-configuration deployment** through GitHub-based distribution, requiring only Python 3.9+ and standard package management tools. The educational-focused architecture eliminates complex setup procedures, enabling immediate gameplay following a simple clone-and-install workflow that supports Windows, macOS, and Linux environments seamlessly.

### Quick Start

```bash
git clone https://github.com/unibo-dtm-se-2425-FlappyPy/artifact.git
cd artifact
pip install -r requirements.txt
python -m FlappyPy
```

**Dependencies:** pygame 2.6.1, setuptools (automatically handled via requirements.txt)

### Launch and Verification

The game launches immediately with `python -m FlappyPy`, opening a 400x600 pixel window with responsive spacebar controls and smooth 60 FPS performance. Installation verification requires no complex testing procedures—successful dependency installation followed by error-free game window opening confirms proper deployment across all supported platforms.

**Cross-Platform Notes:**
- **Windows/macOS**: pygame binaries included, no additional dependencies
- **Linux**: May require `python3-dev` for pygame compilation (`sudo apt-get install python3-dev`)

## Deployment Validation

The comprehensive validation strategy encompasses automated installation testing across Windows 10/11, macOS 10.15+, and Ubuntu 20.04+ systems with Python 3.9-3.11 compatibility verification. Success criteria focus on **100% installation success rate** with immediate gameplay accessibility, ensuring minimal setup barriers align with the educational project's accessibility goals.

**Core Validation Checks:**
- Git clone completion without errors
- Dependencies install via `pip install -r requirements.txt`
- Game window opens with `python -m FlappyPy`
- Spacebar input produces immediate bird movement
- Collision detection and restart functionality operate correctly
