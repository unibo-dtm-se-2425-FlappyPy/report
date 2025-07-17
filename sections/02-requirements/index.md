---
title: Requirements
has_children: false
nav_order: 3
---

# Requirements

## User Stories

### Personas

**Casual Gamer**
- As a casual gamer, I want to play a simple, engaging game during short breaks so that I can have quick entertainment without complex setup.
- As a casual gamer, I want the game to start immediately when I launch it so that I don't waste time on menus or configuration.

**Python Developer**
- As a Python developer, I want to examine well-structured game code so that I can learn pygame development practices.
- As a Python developer, I want to run tests so that I can understand professional testing methodologies.

**Educator**
- As an educator, I want to demonstrate complete software development lifecycle so that I can teach students professional practices.

## Requirements Analysis

### Functional Requirements

**FR1: Game Launch and Initialization**
- The system shall provide a command-line interface for launching the game via `python -m FlappyPy`.
- The system shall initialize a game window with specified dimensions and frame rate.

**FR2: Bird Movement Control**
- The system shall respond to spacebar input by applying upward velocity to the bird.
- The system shall continuously apply gravity to the bird, causing downward acceleration.

**FR3: Obstacle Generation and Movement**
- The system shall generate pipe obstacles at regular intervals.
- The system shall create randomized gap positions for each pipe pair.
- The system shall move all pipes horizontally from right to left at consistent speed.

**FR4: Collision Detection**
- The system shall detect collisions between bird and pipe obstacles.
- The system shall detect collisions between bird and ground boundary.
- The system shall trigger game over state upon any collision.

**FR5: Game State Management**
- The system shall maintain active gameplay state during normal play.
- The system shall transition to game over state upon collision detection.
- The system shall provide restart functionality via spacebar when in game over state.
- The system shall reset all game objects to initial positions upon restart.

### Non-Functional Requirements

**NFR1: Performance**
- The system shall maintain smooth FPS gameplay during normal operation.
- The system shall handle obstacle generation without frame rate drops.
- The system shall complete collision detection within acceptable response time.

**NFR2: Usability**
- The system shall require only spacebar input for all gameplay interactions.
- The system shall provide immediate visual feedback for all player actions.

**NFR3: Reliability**
- The system shall operate without crashes during extended gameplay sessions.

**NFR4: Portability**
- The system shall execute on Windows, macOS, and Linux operating systems.
- The system shall require only Python 3.9+ and pygame library dependencies.

### Implementation Requirements

**IR1: Programming Language**
- The system shall be implemented in Python 3.9 or higher.

**IR2: Graphics Library**
- The system shall use pygame library for graphics rendering and input handling.

**IR3: Testing Framework**
- The system shall include unit tests using Python's unittest framework.

## Glossary

**Bird**: The player-controlled sprite that responds to spacebar input with upward movement and experiences continuous gravity.

**Collision Detection**: The process of determining when the bird sprite intersects with pipe obstacles or screen boundaries.

**Frame Rate**: The frequency at which the game updates graphics and physics, measured in frames per second (FPS).

**Game Loop**: The continuous cycle of input processing, game state updates, and screen rendering.

**Game Over State**: The non-interactive state triggered by collision, where only restart input is accepted.

**Velocity**: The rate of change of the bird's position, modified by gravity and player input.

**Gravity**: The constant downward acceleration applied to the bird sprite each frame.

**Pipe Obstacles**: Rectangular barriers that move horizontally across the screen with randomized gap positions.

**Scoring**: The point system that increments by one each time the bird successfully passes through a pipe gap.

## Acceptance Criteria

### FR1 Acceptance Criteria
- Game window opens within 2 seconds of command execution.
- Window displays at correct defined resolution (default is `400x600` pixels).
- Bird sprite appears at initial position (default are `x=50`, `y=300`).
- Game runs at stable 60 FPS as measured by pygame clock.

### FR2 Acceptance Criteria
- Spacebar input immediately applies upward velocity (default is `-8` pixels/frame).
- Gravity constantly increases downward velocity (default is `+0.5` pixels/frame²).
- Bird position updates smoothly each frame based on current velocity.
- Multiple rapid spacebar inputs are processed correctly.

### FR3 Acceptance Criteria
- New pipe pair generates every 2 seconds (default is `120` frames at `60` FPS).
- Gap center position varies randomly between safe boundaries.
- All pipes move at consistent (default `3` pixels/frame) speed.

### FR4 Acceptance Criteria
- Collision detection triggers within `1` frame of sprite overlap.
- Top pipe, bottom pipe, and ground collisions are detected separately.
- Ceiling collision clamps bird position without game over.
- Collision detection accuracy verified through unit tests.

### FR5 Acceptance Criteria
- Game over state prevents all physics updates.
- Restart functionality resets bird to initial position and velocity.
- Restart clears all existing pipe obstacles.
