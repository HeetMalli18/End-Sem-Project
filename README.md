# 🐤 Flappy Bird - Console Edition (Smooth Version)

A console-based Flappy Bird game developed in **C++** using **Windows API**. This version simulates real-time gameplay with smooth animations, custom rendering, and multiple difficulty levels.

> Built for fun and practice, this game works entirely in the Windows console with no external libraries (except standard headers).

---

## 📋 Features

- 🐦 Playable Flappy Bird game in console
- 📈 Score tracking and increasing difficulty
- 🎮 Real-time controls using `conio.h`
- 🚀 Smooth rendering with `CHAR_INFO` buffer
- 💡 Difficulty selection (Easy / Medium / Hard)
- 🧱 Pipe collision detection
- ⏸️ Pause / Resume functionality
- ❌ Game over screen with replay/quit options

---

## 🎮 Controls

| Key          | Action                    |
|--------------|---------------------------|
| `Space` / `W`| Jump (Flap the bird)      |
| `P`          | Pause the game            |
| `R`          | Resume after pause        |
| `Q`          | Quit the game             |
| `1` `2` `3`  | Select difficulty level    |

---

## 🧠 How It Works

### 🌀 Game Loop Flow

1. **Start screen** → player selects difficulty
2. **Setup** initializes variables and game state
3. **Game loop** runs until `gameOver == true`:
   - Clears buffer
   - Draws bird, pipes, and borders
   - Renders buffer to console
   - Handles input
   - Updates game logic (gravity, pipe movement, collision)
4. **Game over screen** appears → press `R` to restart or `Q` to quit

### 🖼️ Rendering System

- A `CHAR_INFO` buffer acts as a 2D frame buffer
- All characters (bird, pipes, borders) are drawn into the buffer
- The buffer is written to console using `WriteConsoleOutput`
- No flickering thanks to direct buffer rendering

---

## 🗂️ Data Structures Used

| Data Structure           | Purpose                                              |
|--------------------------|------------------------------------------------------|
| `vector<int> pipeX`      | Stores x-position of each pipe                       |
| `vector<int> pipeGapY`   | Stores vertical gap positions for each pipe          |
| `enum Difficulty`        | Easy, Medium, Hard settings                          |
| `CHAR_INFO[]`            | 1D buffer acting as screen for smooth rendering      |
| `HANDLE`, `COORD`        | Windows API types for console control and cursor     |

---

## 🎯 Difficulty Levels

| Level   | Speed | Gravity | Jump Force |
|---------|-------|---------|-------------|
| Easy    | 1     | 1       | -3          |
| Medium  | 2     | 1       | -4          |
| Hard    | 3     | 2       | -5          |

- Speed controls how fast pipes move
- Gravity determines how fast the bird falls
- Jump Force determines how high the bird jumps

---

## ⚖️ Trade-offs & Design Choices

| Design Choice                                | Trade-off / Reason                                                                 |
|---------------------------------------------|-------------------------------------------------------------------------------------|
| Console-only rendering                       | No graphics library needed, but limits to ASCII visuals                            |
| Direct buffer (`CHAR_INFO[]`) rendering      | Smooth gameplay, avoids `system("cls")` flickering                                 |
| Hardcoded constants (screen size, pipe width)| Simplicity > configurability                                                       |
| No object-oriented structure                 | Straightforward procedural code for readability                                    |
| `conio.h` for input                          | Quick non-blocking key reads, but not portable beyond Windows                      |

---

## 🧪 Example Screenshots (ASCII)

---

## 🔧 How to Compile & Run

### ✅ Requirements

- Windows OS
- C++ compiler (MSVC / MinGW)
- Console that supports `conio.h` and Windows API

### 🛠️ Compile

Using MinGW or similar:

```bash
g++ -o FlappyBird flappybird.cpp

