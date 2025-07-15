---
title: User Guide
has_children: false
nav_order: 10
---

# User Guide

This guide explains how to install, launch, and play FlappyPy from the user's perspective.

## Installation

**Requirements:**
- Python 3.8 or higher installed on your system
- Internet connection for initial installation

**Install FlappyPy:**
```bash
pip install FlappyPy
```

The installation will automatically download pygame and other required dependencies.

## Launching the Game

**Start FlappyPy:**
```bash
python -m FlappyPy
```

A game window (400x600 pixels) will open immediately, and you're ready to play!

## How to Play

### Basic Controls

**Spacebar** - Your only control for the entire game:
- **During gameplay**: Makes the bird flap and fly upward
- **After game over**: Restarts the game

### Game Objective

**Survive as long as possible** by navigating your bird through gaps between pipe obstacles:

1. **Avoid the pipes** - Flying into any pipe ends the game
2. **Avoid the ground** - Touching the bottom of the screen ends the game  
3. **Stay airborne** - Gravity constantly pulls the bird downward
4. **Timing is key** - Press spacebar to counter gravity and navigate through gaps

### Game Mechanics

**Bird Physics:**
- **Gravity**: The bird constantly falls downward
- **Jumping**: Spacebar applies upward momentum
- **Momentum**: Each jump gives temporary upward velocity that gravity overcomes

**Obstacle System:**
- **Pipe Generation**: New pipe pairs appear regularly from the right side
- **Random Gaps**: Each pipe pair has a gap at a different height
- **Continuous Movement**: All pipes scroll from right to left at constant speed

**Game States:**
- **Playing**: Normal gameplay with physics active
- **Game Over**: Triggered by collision, physics stop, restart available

## Gameplay Tips

**For New Players:**
- **Practice timing** - Don't tap too rapidly or too slowly
- **Watch ahead** - Look at upcoming pipes while navigating current ones
- **Stay centered** - Keep the bird roughly in the middle of the screen when possible
- **Don't panic** - Smooth, measured taps work better than frantic pressing

**Advanced Techniques:**
- **Rhythm development** - Find a consistent tapping rhythm
- **Gap positioning** - Position bird slightly above gap center for easier navigation
- **Momentum control** - Use single taps for fine adjustments, multiple taps for larger movements

## Game Features

**Current Version (1.0.0):**
- **Smooth 60 FPS gameplay** - Responsive, lag-free experience
- **Accurate collision detection** - Precise hit detection for fair gameplay
- **Instant restart** - No delays between game over and new game
- **Cross-platform compatibility** - Works on Windows, macOS, and Linux

**No Data Storage:**
- **Session-based play** - No scores are saved between games
- **No user accounts** - No registration or login required
- **Privacy-friendly** - No personal data collected or transmitted

## Troubleshooting

**Common Issues:**

**Game window doesn't open:**
- Verify Python 3.8+ is installed: `python --version`
- Ensure pygame installed correctly: `python -c "import pygame; print('pygame working')"`
- Try reinstalling: `pip uninstall FlappyPy` then `pip install FlappyPy`

**Spacebar not responding:**
- Ensure the game window has focus (click on it)
- Try pressing spacebar while the game window is active
- Check if other applications are capturing keyboard input

**Game runs too slowly:**
- Close other applications to free up system resources
- Ensure your system meets minimum requirements (any modern computer should)
- Restart the game if performance degrades over time

**Installation problems:**
- Update pip: `pip install --upgrade pip`
- Try with user flag: `pip install --user FlappyPy`
- Check internet connection for PyPI access

## Technical Specifications

**System Requirements:**
- **Operating System**: Windows 7+, macOS 10.12+, or Linux
- **Python**: Version 3.8, 3.9, 3.10, or 3.11
- **Memory**: Minimal requirements (< 50 MB)
- **Disk Space**: < 10 MB for installation
- **Graphics**: Basic graphics capability (any modern system)

**Performance:**
- **Frame Rate**: 60 FPS target on all supported systems
- **Response Time**: Immediate input response (< 16ms)
- **Memory Usage**: Stable memory footprint with automatic cleanup
- **CPU Usage**: Minimal CPU usage during normal gameplay

## Getting Help

**For Technical Issues:**
- Check the [GitHub repository](https://github.com/unibo-dtm-se-2425-FlappyPy/artifact) for known issues
- Create a new issue if you encounter bugs or problems
- Include your Python version and operating system in bug reports

**For Gameplay Questions:**
- Practice is the best teacher - the game rewards patience and timing
- No additional tutorials needed - FlappyPy uses the classic, simple mechanics
- Each restart is a fresh opportunity to improve your skills

## Uninstallation

**Remove FlappyPy:**
```bash
pip uninstall FlappyPy
```

This will completely remove the game and free up the disk space. No additional cleanup required since FlappyPy doesn't create any permanent files or data.

## Version Information

**Current Release**: v1.0.0
- Core Flappy Bird gameplay mechanics
- Complete collision detection system
- Smooth 60 FPS performance
- Cross-platform compatibility

**Future Updates:**
- Check PyPI or the GitHub repository for newer versions
- Update using: `pip install --upgrade FlappyPy`
- New versions will maintain backward compatibility
