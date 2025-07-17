---
title: Design
has_children: false
nav_order: 4
---

# Design

## Architecture

### Architectural Style

FlappyPy employs an **Event-Based Architecture with Object-Oriented Design** that seamlessly integrates audio feedback, visual state management, and resource management systems. The architecture supports sprite handling, sound effects, and background music while maintaining state-based gameplay with comprehensive restart functionality that ensures clean game session transitions.

### High-Level Architecture Overview

The game architecture follows a structured initialization flow beginning with pygame setup, resource loading for images and audio assets, and game window creation. The main game loop operates continuously at 60 FPS, processing user events, updating game state, and rendering visual elements while managing critical decision points including event processing for user input, game state differentiation between normal gameplay and game over conditions, multi-layered collision detection for pipes and boundaries, scoring logic for successful pipe passage, and dynamic resource management for obstacle spawning and cleanup.

**Activity UML Diagram**
![Activity UML Diagram](assets/UMLActivity.png)

### Component Responsibilities

The architectural foundation centers around a **Main Game Engine** that orchestrates all subsystems while managing the primary game loop and overall state coordination. Game object components include the Bird component with integrated physics simulation and collision detection, the Pipe component managing obstacle generation with randomized gap placement, and the Score component handling tracking and display logic.

**System Integration:**
- Audio System manages background music and sound effects with resource loading
- Graphics System handles rendering operations for sprites, text, and screen updates
- Input Handler processes keyboard events for spacebar control
- Resource Loader manages asset loading with fallback handling
- Collision Detection implements physics simulation algorithms

The architecture leverages **pygame framework** as the core dependency while interfacing with system resources through well-defined APIs for game loop coordination, physics simulation, rendering operations, audio playback, input processing, and asset management.

**Component UML Diagram**
![Component UML Diagram](assets/UMLComponent.png)

## Infrastructure

### Resource Management and Deployment

FlappyPy ensures cross-platform compatibility through Python 3.9+ support with importlib.resources, implementing fallback mechanisms including mock sprites and silent audio for testing environments, while organizing assets in structured package directories.

The deployment strategy follows a modern CI/CD pipeline leveraging **GitHub repository** for source control and workflow orchestration, **GitHub Actions runners** for multi-platform testing and deployment execution, culminating in **GitHub releases** for final package distribution.

**Deployment UML Diagram**
![Deployment UML Diagram](assets/UMLDeployment.png)

## Modelling

### Class Design

FlappyPy's object-oriented architecture centers on four primary classes that collaborate to deliver complete game functionality. The **Bird class** encapsulates all physics-related attributes including position, velocity, and gravity while managing sprite states for flying versus falling animations and implementing collision detection with pipes, ground, and ceiling boundaries through its update() method.

The **Pipe class** represents moving obstacles with positioning and gap calculation management, containing drawing logic for both top and bottom segments while tracking scoring opportunities when the bird successfully passes through. The **Score class** provides simple score tracking with increment methods and current value retrieval for main game loop integration, while the **GameUtilities class** encompasses utility functions, main game loop coordination, resource loading for images and audio, and game over screen display management.

**Class UML Diagram**
![Class UML Diagram](assets/UMLClass.png)

### Object Relationships Design

The object interaction model demonstrates how Bird-Pipe collision detection operates through individual pipe instance checking, while collection management maintains multiple pipe instances within pipes_list. The scoring system monitors bird progress relative to pipe positions, and the rendering pipeline ensures proper screen object rendering order for all game elements.

**Object UML Diagram**
![Object UML Diagram](assets/UMLObject.png)

## Interaction

The interaction model demonstrates comprehensive game flow beginning with initialization where the main loop establishes Bird instances, empty pipes collections, scoring systems, and audio resources while creating the game window. The core gameplay iteration showcases user input processing when players press SPACE triggering bird flap() and jump() methods with corresponding audio feedback, followed by physics updates for bird and pipe positions and collision detection systems.

**Conditional Flow Management:**
The game employs alt/else structures differentiating between collision paths that trigger game over sequences with sound effects and game over screens, versus normal paths continuing with score checking, element rendering, and ongoing gameplay. State management includes frame rate control through clock.tick(FPS), bird state transitions upon SPACE release, and comprehensive game reset functionality during restart sequences.

**Sequence UML Diagram**
![Sequence UML Diagram](assets/UMLSequence.png)

## Behaviour

FlappyPy operates through distinct behavioral states including initialization for pygame setup and resource loading, normal gameplay with active bird control and collision detection, game over state triggered by collision detection, and specialized bird states for flying and falling within gameplay sessions.

**State transitions** respond to user input through space key press/release for bird control and restart functionality, collision detection when bird contacts pipes or boundaries, system events including pygame quit events, and timer events controlling pipe spawning and frame rate management.

**State UML Diagram**
![State UML Diagram](assets/UMLState.png)

## Data-Related Aspects

The data architecture optimizes performance through strategic resource management including audio resources loaded once at startup, sprite caching within Bird objects, frame counters for pipe generation timing, and score persistence until restart. The system emphasizes efficient asset reuse with sprites and sounds loaded once then reused throughout gameplay, list comprehension for pipe removal, and complete object recreation during state reset operations.