---
title: User Guide
has_children: false
nav_order: 10
---

# User Guide

This guide explains how to install, launch, and play FlappyPy from the user's perspective.

## Installation

**Requirements:**
- Python 3.9 or higher installed on your system
- Git for cloning the repository
- Internet connection for downloading

**Install FlappyPy:**
```bash
git clone https://github.com/unibo-dtm-se-2425-FlappyPy/artifact.git
cd artifact
pip install -r requirements.txt
```

## Launching the Game

**Start FlappyPy:**
```bash
cd artifact
python -m FlappyPy
```

A game window (400x600 pixels) will open immediately, and you're ready to play!

## How to Play

**Spacebar** - Your only control:
- **During gameplay**: Makes the bird flap upward
- **After game over**: Restarts the game

**Game Objective:** Navigate through pipe gaps without hitting anything.

**Game Mechanics:**
- **Gravity**: Bird constantly falls downward
- **Jumping**: Spacebar applies upward momentum
- **Obstacles**: Pipes move from right to left with random gap positions
- **Collision**: Hitting pipes or ground triggers game over

## Troubleshooting

**Game window doesn't open:**
- Verify Python 3.9+ is installed: `python --version`
- Ensure pygame installed: `python -c "import pygame; print('pygame working')"`
- Reinstall dependencies: `pip install -r requirements.txt`

**Spacebar not responding:**
- Ensure the game window has focus (click on it)
- Check if other applications are capturing keyboard input

## Technical Specifications

**System Requirements:**
- **Operating System**: Windows, macOS, or Linux
- **Python**: Version 3.9, 3.10, or 3.11
- **Memory**: < 50 MB
- **Disk Space**: < 10 MB

**Performance:** 60 FPS target with immediate input response

## Getting Help

**For Issues:**
- Check the [GitHub repository](https://github.com/unibo-dtm-se-2425-FlappyPy/artifact) for known issues
- Create a new issue if you encounter problems
- Include your Python version and operating system in bug reports
