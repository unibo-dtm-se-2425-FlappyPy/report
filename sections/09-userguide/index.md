---
title: User Guide
has_children: false
nav_order: 10
---

# User Guide

## Quick Start

FlappyPy delivers **immediate gaming satisfaction** through a streamlined installation process requiring only Python 3.9+ and git access. The educational-friendly design eliminates complex configuration, enabling players to experience classic Flappy Bird gameplay within minutes of download completion.

```bash
git clone https://github.com/unibo-dtm-se-2425-FlappyPy/artifact.git
cd artifact
pip install -r requirements.txt
python -m FlappyPy
```

The game launches instantly in a 400x600 pixel window, ready for spacebar-controlled bird navigation through randomly positioned pipe obstacles.

## Gameplay Mechanics

The **spacebar serves as your complete control interface**, providing upward thrust during gameplay and restart functionality after collision events. Navigate through continuously moving pipe obstacles that generate with randomized gap positions, creating unique challenge patterns while maintaining consistent horizontal movement speed and physics-based gravity effects.

**Game Objective:** Successfully pass through pipe gaps without collision to achieve maximum scoring.

## Support and Technical Details

**Common Issues:** Window focus problems can affect spacebar responsiveness (click game window), while pygame installation issues resolve through dependency reinstallation via `pip install -r requirements.txt`.

**System Compatibility:** Windows, macOS, and Linux with Python 3.9-3.11 support, requiring minimal system resources (< 50 MB memory, < 10 MB disk space) while targeting smooth 60 FPS performance.

**Additional Help:** Visit the [GitHub repository](https://github.com/unibo-dtm-se-2425-FlappyPy/artifact) for issue reporting and include your Python version plus operating system details for effective troubleshooting assistance.
