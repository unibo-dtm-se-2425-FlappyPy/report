---
title: Concept
has_children: false
nav_order: 2
---

# Concept

## Product Type

FlappyPy is a **desktop application** developed as a complete Python implementation of the classic Flappy Bird game. The product falls into the category of:

- **Interactive Desktop Game Application** - A standalone executable game with real-time graphics and user input
- **Educational Software Package** - Demonstrates professional Python game development practices

The application utilizes the **pygame** library for graphics rendering, input handling, and game loop management, creating a smooth gaming experience on desktop platforms.

## Use Case Collection

### User Demographics and Context

**Primary Users:**
- **Casual Gamers** - Individuals seeking quick, engaging entertainment
- **Python Developers** - Learning game development and pygame usage
- **Students** - Studying software engineering and game development concepts

**Secondary Users:**
- **Educators** - Using the project as a teaching example for Python development
- **Code Reviewers** - Examining professional development practices and testing methodologies

### Interaction Patterns

**When and How Frequently:**
- **Casual Gaming Sessions** - Entertainment breaks throughout the day
- **Development Study** - Sessions for code analysis and learning
- **Educational Demonstrations** - Scheduled classroom or workshop sessions

**Interaction Method:**
- **Primary Input Device** - Computer keyboard (spacebar for jumping)
- **Platform** - Desktop computers (Windows, macOS, Linux)
- **Installation** - Git clone repository: `git clone https://github.com/unibo-dtm-se-2425-FlappyPy/artifact.git` followed by `cd artifact` and then `pip install -r requirements.txt`
- **Execution** - Terminal command: `python -m FlappyPy`

### Data Storage and Management

**User Data Requirements:**
- **No Persistent Data Storage** - FlappyPy v1.2.1 does not store user data, scores, or preferences
- **Session-Based Experience** - Each game session is independent with no saved progress
- **Local Execution** - All game state exists only during active gameplay in system memory

**Technical Data:**
- **No Network Communication** - Fully offline, self-contained application
- **No User Registration** - No accounts, profiles, or personal information collected
- **No External Dependencies** - Beyond pygame library, no external services required

### User Roles and Responsibilities

**End User (Player):**
- Launch the game application
- Navigate bird through pipe obstacles using spacebar input
- Restart game sessions after collision

**Developer/Learner:**
- Install package via Github repository
- Examine source code for educational purposes
- Run comprehensive test suite for learning testing practices
