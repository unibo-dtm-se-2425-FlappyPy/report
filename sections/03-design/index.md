---
title: Design
has_children: false
nav_order: 4
---

# Design

This chapter explains the strategies used to meet the requirements identified in the analysis. The design focuses on a single-threaded, event-driven desktop game architecture optimized for real-time gameplay and educational clarity.

## Architecture

### Architectural Style Selection

**Chosen Style: Event-Based Architecture with Object-Oriented Design**

**Justification:**

- **Event-driven nature**: Perfect for real-time games where user input, physics updates, and collision detection must respond to discrete events
- **Pygame compatibility**: Aligns naturally with pygame's event system and game loop paradigm
- **Educational clarity**: Clear separation of concerns makes the codebase accessible for learning purposes
- **Testability**: Event-based design enables isolated unit testing of individual components

**Rejected Alternatives:**

- **Layered Architecture**: Too rigid for real-time game requirements where all layers need direct access to timing and input
- **Shared Dataspace**: Unnecessary complexity for a single-threaded desktop application
- **Component-Based**: Overly complex for the straightforward Flappy Bird mechanics

### Actual Architecture: Game Loop with Object-Oriented Components

**High-Level Architecture Overview:**

```markdown
┌─────────────────────────────────────────────────────────────┐
│ Main Game Loop │
│ ┌─────────────┐ ┌─────────────┐ ┌─────────────────────┐ │
│ │ Input │ │ Update │ │ Render │ │
│ │ Handler │ │ Physics │ │ Graphics │ │
│ └─────────────┘ └─────────────┘ └─────────────────────┘ │
└─────────────────────────────────────────────────────────────┘
│
┌─────────────┼─────────────┐
│ │ │
┌─────────────┐ ┌─────────────┐ ┌─────────────┐
│ Bird │ │ Pipe │ │ Collision │
│ Object │ │ Manager │ │ Detector │
│ │ │ │ │ │
│ - position │ │ - pipes[] │ │ - detect() │
│ - velocity │ │ - spawn() │ │ - response()│
│ - update() │ │ - update() │ │ │
│ - draw() │ │ - draw() │ │ │
└─────────────┘ └─────────────┘ └─────────────┘
```

### Component Responsibilities

**Main Game Loop (`main()` function):**

- **Input Processing**: Capture and route keyboard events to appropriate handlers
- **Physics Coordination**: Orchestrate all object updates in correct sequence
- **Render Management**: Control drawing order and screen updates
- **State Management**: Handle game state transitions (playing, game over, restart)

**Bird Object (`Bird` class):**

- **Physics Simulation**: Apply gravity, velocity, and boundary constraints
- **Input Response**: React to spacebar input with upward acceleration
- **Collision Interface**: Provide collision detection methods for external systems
- **Visual Representation**: Handle sprite rendering and position updates

**Pipe Management System:**

- **Procedural Generation**: Create pipe obstacles at timed intervals
- **Movement Coordination**: Update all pipe positions consistently
- **Lifecycle Management**: Remove off-screen pipes to prevent memory leaks
- **Collision Geometry**: Provide accurate collision boundaries for detection

**Collision Detection System:**

- **Spatial Analysis**: Determine sprite intersections using pygame.Rect
- **Event Generation**: Trigger game state changes upon collision detection
- **Multi-object Handling**: Process bird interactions with multiple pipe obstacles

## Infrastructure

### Deployment Architecture

**Single-Machine Desktop Application:**

- **No distributed components** - FlappyPy runs entirely on the user's local machine
- **Self-contained execution** - All game logic, graphics, and state management occur within a single Python process
- **No network dependencies** - Fully offline operation with no external service requirements

**Component Distribution:**

- **All components co-located** - Bird, Pipe, and Collision systems exist within the same process memory space
- **No inter-process communication** - Direct method calls and shared memory for all component interactions
- **Local file system access** - Package installation via pip, execution via Python interpreter

**Dependency Management:**

- **Python Runtime**: Requires Python 3.8+ installation on target system
- **Pygame Library**: Single external dependency for graphics and input handling
- **Package Distribution**: Delivered via PyPI for standardized installation process

## Modelling

### Object-Oriented Design

**Core Data Types and Relationships:**
#### class **Bird()**
##### Attributes:
```markdown
- x: int # Horizontal position (constant)
- y: float # Vertical position (variable)
- width: int # Sprite width for collision detection
- height: int # Sprite height for collision detection
- velocity: float # Current vertical velocity
- gravity: float # Gravitational acceleration constant
```
##### Methods:
```markdown
- update(): void # Apply physics and boundary checking
- jump(): void # Apply upward velocity from input
- draw(screen): void # Render bird sprite
- get_rect(): pygame.Rect # Get collision rectangle
- check_collision_with_pipe(pipe): boolean
- check_collision_with_ground(): boolean
- check_collision_with_ceiling(): boolean
```
#### class **Pipe()**
##### Attributes:
```markdown
- x: int # Horizontal position
- width: int # Pipe width
- gap_center_y: int # Vertical center of gap
- gap_size: int # Gap size between pipe segments
 - speed: int # Horizontal movement speed
- top_height: int # Height of top pipe segment
- bottom_y: int # Y-position of bottom pipe segment
- bottom_height: int # Height of bottom pipe segment
```
##### Methods:
```markdown
- update(): void # Move pipe horizontally
- draw(screen): void # Render both pipe segments
```

**Object Relationships:**

- **Bird ↔ Pipe**: One-to-many collision detection relationship
- **Main Loop → All Objects**: Composition relationship for lifecycle management
- **Collision System → Bird + Pipes**: Dependency relationship for spatial analysis

### Domain Concepts

**Game State Management:**

- **Active Play State**: Normal physics simulation and input processing
- **Game Over State**: Suspended physics with restart input handling
- **Transition Events**: Collision detection triggers state changes

**Physics Domain:**

- **Gravity System**: Constant downward acceleration applied to bird
- **Velocity Integration**: Position updates based on current velocity
- **Boundary Constraints**: Screen edge collision and response

**Obstacle Generation Domain:**

- **Timed Spawning**: Regular pipe creation based on frame counting
- **Randomized Positioning**: Gap center varies within safe boundaries
- **Lifecycle Management**: Automatic cleanup of off-screen obstacles

## Interaction

### Component Communication Patterns

**Event-Driven Input Processing:**

```
User Input (Spacebar) → pygame.event → Main Loop → Bird.jump()
```

**Physics Update Sequence:**

```
Main Loop → Bird.update() → Pipe.update() → Collision Detection
```

**Collision Response Chain:**

```
Collision Detection → Game State Change → Physics Suspension → Input Mode Change
```

**Render Pipeline:**

```
Main Loop → Background Fill → Pipe.draw() → Bird.draw() → Display Update
```

### Timing and Coordination

**Frame-Based Synchronization:**

- **60 FPS Target**: All updates synchronized to 16.67ms intervals
- **Sequential Processing**: Input → Physics → Collision → Render pipeline
- **Deterministic Timing**: Frame counter used for obstacle spawning and game events

**State Synchronization:**

- **Immediate State Changes**: Game over triggered instantly upon collision
- **Consistent Object States**: All objects updated before collision detection
- **Atomic Restart**: Complete game state reset occurs in single frame

## Behaviour

### Component State Management

**Bird Behavior:**

- **Idle State**: Affected by gravity, responsive to input
- **Jumping State**: Upward velocity applied, then returns to idle
- **Collision State**: Physics frozen, awaiting restart input
- **Boundary State**: Position clamped to screen edges with velocity reset

**Pipe System Behavior:**

- **Generation State**: Create new pipes at timed intervals
- **Movement State**: Continuous horizontal translation
- **Cleanup State**: Remove pipes that have moved off-screen
- **Collision State**: Provide accurate boundaries for detection

**Game State Transitions:**

```
Initialize → Playing → Collision Detected → Game Over → Restart → Playing
```

### Event Response Patterns

**Input Events:**

- **Spacebar (Playing)**: Apply upward velocity to bird
- **Spacebar (Game Over)**: Reset game state and restart
- **Window Close**: Clean shutdown of pygame systems

**Physics Events:**

- **Gravity Application**: Continuous downward acceleration
- **Boundary Contact**: Position clamping and velocity adjustment
- **Collision Detection**: Immediate state transition to game over

**Timing Events:**

- **Pipe Spawn Timer**: Regular obstacle generation
- **Frame Update**: Coordinate all object updates
- **Collision Check**: Validate spatial relationships each frame

## Data-Related Aspects

### Data Storage Requirements

**No Persistent Storage:**

- **Session-Based Design**: FlappyPy v1.0.0 maintains no persistent data
- **No Score Tracking**: Current implementation doesn't save high scores or player progress
- **No Configuration**: No user preferences or game settings storage
- **Stateless Sessions**: Each game execution starts fresh without previous session data

**Runtime Data Management:**

- **Game State**: Stored in local variables within main game loop
- **Object Collections**: Pipes stored in Python list structure
- **Collision Data**: Temporary pygame.Rect objects for spatial calculations
- **Input State**: Processed immediately without buffering or storage

**Memory Management:**

- **Automatic Cleanup**: Python garbage collection handles object lifecycle
- **List Maintenance**: Off-screen pipes removed from active collections
- **No Memory Persistence**: All game data exists only during active execution
