# Joy - Bowling Game

A modern bowling game implemented using C++ for the physics engine and Python with PyGame for the user interface.

## Features

- **Realistic Physics**: C++ engine simulates ball movement, pin collisions, and scoring
- **Modern UI**: Clean black and white interface with smooth animations
- **Standard Bowling Rules**: 10-frame scoring with strikes, spares, and proper 10th frame handling
- **Interactive Controls**: Adjustable force and angle sliders for precise control
- **Score Tracking**: Real-time scoring with high score persistence
- **Cross-Platform**: Works on Linux, macOS, and Windows

## Project Structure

```
joy/
├── cpp/                    # C++ Game Engine
│   ├── BowlingEngine.h     # Header file with game classes
│   ├── BowlingEngine.cpp   # Implementation of physics and game logic
│   ├── main.cpp           # Test harness for C++ engine
│   └── CMakeLists.txt     # Build configuration
├── python/                # Python UI and Game Logic
│   ├── config.py          # Game configuration and constants
│   ├── score.py           # Score management and bowling rules
│   ├── ui.py              # PyGame UI components and rendering
│   └── game.py            # Main game loop and integration
└── README.md              # This file
```

## Requirements

### C++ Engine
- CMake 3.10 or higher
- C++11 compatible compiler (GCC, Clang, MSVC)
- Math library (libm on Unix systems)

### Python Game
- Python 3.6 or higher
- PyGame 2.0 or higher

## Installation and Setup

### 1. Build the C++ Engine

```bash
cd cpp/
cmake .
make
```

This will create the executable at `bin/JoyBowlingGame`.

### 2. Install Python Dependencies

```bash
pip install pygame
```

### 3. Run the Game

```bash
cd python/
python game.py
```

## How to Play

### Game Controls

1. **Force Slider**: Adjust the power of your roll (10-100)
2. **Angle Slider**: Control the angle of your throw (-45° to +45°)
3. **ROLL Button**: Execute your bowling throw
4. **RESET Button**: Start a new game
5. **QUIT Button**: Exit the game

### Keyboard Shortcuts

- **SPACE**: Start game from menu
- **R**: Reset current game
- **ESC**: Quit game

### Scoring

The game follows standard 10-pin bowling rules:

- **Strike**: Knock down all 10 pins on first roll (10 + next 2 rolls)
- **Spare**: Knock down all 10 pins in 2 rolls (10 + next 1 roll)
- **Regular Frame**: Sum of pins knocked down in 2 rolls
- **10th Frame**: Special rules allow up to 3 rolls if you get a strike or spare

## Game Architecture

### C++ Engine (`BowlingEngine`)

The C++ component handles:
- **Physics Simulation**: Ball trajectory, friction, and momentum
- **Collision Detection**: Ball-pin interactions and chain reactions
- **Pin Management**: 10-pin formation and knockdown logic
- **Core Scoring**: Basic scoring calculations

Key Classes:
- `BowlingGame`: Main game controller
- `Ball`: Ball physics and movement
- `Pin`: Individual pin state and collision
- `Lane`: Lane properties and boundaries
- `Scoreboard`: Score calculation and tracking

### Python UI (`PyGame`)

The Python component provides:
- **Modern Interface**: Clean, responsive UI with animations
- **User Input**: Sliders, buttons, and keyboard controls
- **Visual Feedback**: Real-time ball movement and pin animations
- **Game Flow**: Menu system, game states, and transitions
- **Score Display**: Live scoring with frame-by-frame breakdown

Key Modules:
- `game.py`: Main game loop and state management
- `ui.py`: UI components and rendering
- `score.py`: Advanced scoring logic and persistence
- `config.py`: Game settings and constants

## Integration

The Python game can operate in two modes:

1. **With C++ Engine**: Calls the compiled C++ binary for physics simulation
2. **Python Simulation**: Falls back to Python-based physics if C++ engine is unavailable

The integration uses subprocess calls to communicate between Python and C++, making the system modular and maintainable.

## Customization

### Visual Customization

Edit `config.py` to modify:
- Window dimensions
- Colors and themes
- UI layout and positioning
- Animation speeds
- Game physics parameters

### Physics Tuning

Modify `BowlingEngine.cpp` to adjust:
- Ball physics and friction
- Collision detection sensitivity
- Pin interaction mechanics
- Lane properties

## Troubleshooting

### C++ Engine Issues

1. **Compilation Errors**: Ensure you have a C++11 compatible compiler
2. **Missing Math Library**: Link with `-lm` flag on Unix systems
3. **CMake Not Found**: Install CMake from your package manager

### Python Game Issues

1. **PyGame Not Found**: Install with `pip install pygame`
2. **Display Issues**: Ensure you have a graphical environment
3. **Performance**: Reduce FPS in config.py for slower systems

### Integration Issues

1. **C++ Engine Not Found**: The game will automatically fall back to Python simulation
2. **Permission Errors**: Ensure the C++ executable has execute permissions
3. **Path Issues**: Check that the C++ binary is in the expected location

## Development

### Adding Features

1. **New UI Elements**: Add to `ui.py` and handle events in `game.py`
2. **Physics Improvements**: Modify the C++ engine and recompile
3. **Scoring Variants**: Extend `score.py` for different game modes
4. **Visual Effects**: Add animations and effects in the UI module

### Testing

- **C++ Engine**: Run `./bin/JoyBowlingGame` for standalone testing
- **Python Components**: Use Python's unittest framework
- **Integration**: Test both modes (with and without C++ engine)

## License

This project is open source. Feel free to modify and distribute according to your needs.

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## Credits

- **Physics Engine**: Custom C++ implementation
- **UI Framework**: PyGame library
- **Game Design**: Classic 10-pin bowling rules
- **Graphics**: Modern minimalist design with black and white theme
