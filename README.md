# Flappy Bird - Console Version in C++
Open Source Project: https://github.com/BlackyDrum/flappy-bird.git

---![Screenshot 2025-04-16 115420](https://github.com/user-attachments/assets/3fab4764-56c9-4f5d-9d6a-4558ff62c69b)

![Screenshot 2025-04-16 140552](https://github.com/user-attachments/assets/f0850e3b-d68f-44da-b1c8-044ba6d8a05f)

![Screenshot 2025-04-16 140605](https://github.com/user-attachments/assets/c15a35ae-b9df-4025-a24a-6ea72c97c1ae)



 Overview

This is a fully functional console-based Flappy Bird clone built in **C++** using **Windows API (Win32)**. The game runs entirely in the terminal, utilizing character-based graphics and `CHAR_INFO` buffers for rendering. It features:

- Dynamic difficulty selection (Easy, Medium, Hard)
- Colorful console-based graphics
- Real-time input handling
- Score tracking
- Gravity, pipe generation, and collision mechanics
- Smooth animations with minimal flicker

---

## 📽️ Game Preview


---

## 🧠 How It Works

### 1. **Console Rendering with `CHAR_INFO`**
Instead of using graphics libraries, we simulate a screen using a 2D array of `CHAR_INFO`. The buffer is rendered using `WriteConsoleOutput`.

- `CHAR_INFO consoleBuffer[HEIGHT][WIDTH];`: a 2D grid to store characters and their colors.
- `renderBuffer()`: sends this buffer to the console efficiently, enabling fast updates without flickering.

### 2. **Game Loop**
The game follows a loop structure:
```cpp
while (!gameOver) {
    processInput();
    updateGame();
    clearBuffer();
    drawGame();
    renderBuffer();
    Sleep(30);
}
This loop handles input, updates physics, renders frames, and manages frame timing.

3. Input Handling
Using _kbhit() and _getch() from <conio.h> for non-blocking input. Pressing:

SPACE makes the bird "flap" upwards.

ESC exits the game.

4. Game Physics
Gravity pulls the bird down every few frames based on difficulty.

Pipes move from right to left.

Collision is detected against pipes and screen edges.

5. Difficulty Mechanics
Easy: Large gaps, slow pipe speed, slow gravity.

Medium: Moderate settings.

Hard: Small gaps, fast pipe movement, faster gravity.

6. Pipe Logic
Pipes are stored as a vector of pairs:

cpp
Copy
Edit
std::vector<std::pair<int, int>> pipes;
Where:

first = X position of the pipe

second = Y center of the gap

Pipes move left over time and get removed when off-screen.

📦 Data Structures Used

Structure	Purpose
vector<pair<int,int>>	Stores pipes with their position and gap center
CHAR_INFO buffer[][]	Stores each character and its color on-screen
int variables	For tracking bird position, score, difficulty, etc.
⚙️ Technical Approach
✅ Rendering
Uses CHAR_INFO and WriteConsoleOutput() to simulate real-time graphics.

No third-party libraries required — runs in plain Windows terminal.

✅ Input
Real-time, non-blocking keystroke handling with <conio.h>.

✅ Timing
Uses Sleep(30) for frame pacing.

Gravity, pipe spawning, and movement are based on frameCount % rate.

✅ Trade-offs
Pros:

No need for graphics libraries.

Cross-system within Windows.

Clean, colored console rendering.

Cons:

Platform-dependent (<windows.h>, <conio.h>).

Limited graphic fidelity due to ASCII constraints.
🕹️ Controls

Key	Action
SPACE	Flap (bird jumps)
ESC	Quit game
1 2 3	Select difficulty
🧪 Features & Gameplay
Bird is always at X = 20 and moves vertically.

Pipes have gaps, with difficulty scaling gap size.

Collisions occur if bird hits pipe or screen bounds.

The score increments when the bird successfully passes a pipe.

Full game over and restart menu.

Difficulty selection menu with color-coded options.

🧩 File Structure
less
Copy
Edit
flappy-bird/
├── main.cpp       // Complete game code
├── README.md      // You are here!
🖥️ Setup Instructions
Requirements:
Windows OS

C++ Compiler (MSVC / g++)

Terminal with ANSI color support

To Compile (Windows):
Using g++:

bash
Copy
Edit
g++ main.cpp -o flappy-bird
Or use any IDE like Code::Blocks or Visual Studio.

To Run:
bash
Copy
Edit
flappy-bird.exe
📈 Difficulty Settings

Difficulty	Gap Size	Pipe Speed	Gravity Rate	Pipe Spawn Rate
Easy	12	Slow	Slow	Sparse (40 frames)
Medium	10	Medium	Medium	Normal (30 frames)
Hard	8	Fast	Fast	Dense (25 frames)
🧠 Future Enhancements (Ideas)
High score tracking

Custom skins (ASCII options)

Sound effects (Beep tones)

Multi-bird or multiplayer support

Enhanced animations (e.g., wings)

💻 Developed With
C++

Windows Console API

<windows.h>, <conio.h>, <vector>, <ctime>

👨‍💻 Contributors
Heet Malli

Aum Vaghela

Jainish Chaudhary

Krish Paghdar


