# Pixel Path

A retro 20-level 2D browser platformer built entirely with vanilla web technologies, without external game engines, frameworks, or physics libraries.

[![HTML5 Canvas](https://img.shields.io/badge/HTML5-Canvas-E34F26?logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API)
[![Vanilla JavaScript](https://img.shields.io/badge/JavaScript-Vanilla%20ES6+-F7DF1E?logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![Web Audio API](https://img.shields.io/badge/Audio-Web%20Audio%20API-blue)](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

[Play Online](https://deepakpradhan1021.github.io/Pixel_Path/) • [Features](#-features) • [Controls](#-controls) • [Architecture](#-game-architecture) • [How to Run](#-how-to-run-locally) • [License](#-license)

---

## 🕹️ Play Online (Live Demo)

Play the full 20 levels directly in your web browser:  
👉 **[Launch Pixel Path](https://deepakpradhan1021.github.io/Pixel_Path/)**

---

## ✨ Features

- **20 Progressive Stages:** Spread across 5 visual biomes (*Meadow*, *Forest*, *Caves*, *Sky Isles*, *Ember Keep*).
- **Custom 2D Physics:** Pure mathematical physics implementation featuring gravity (1060 px/s²), terminal velocity, horizontal momentum damping, coyote time (0.1s grace window), and jump buffering (0.12s input buffer).
- **AABB Collision Resolution:** Axis-Aligned Bounding Box collision detection that prevents clipping through solid platform surfaces and moving obstacles.
- **Interactive Elements:** Moving floating platforms, spring launch pads, breakable coin blocks (`?`), patrolling enemies, and mid-level checkpoint flags.
- **8-Bit Sound Synthesis:** Dynamic retro sound effects generated procedurally via the native browser **Web Audio API** (`AudioContext` oscillators) with zero external audio assets.
- **Cross-Platform Controls:** Desktop keyboard controls and on-screen virtual d-pad touch controls on mobile devices.
- **Progress Persistence:** Unlocked level state saved locally in `localStorage`.

---

## 🎮 Controls

### Desktop Keyboard:
- **Move Left / Right:** `A` / `D` or `Left` / `Right` Arrow keys
- **Jump:** `W`, `Up` Arrow, or `Spacebar` (supports variable jump heights)

### Mobile Touchscreen:
- **Move Left / Right:** Bottom-left virtual arrow buttons
- **Jump:** Bottom-right red action button

---

## 🏗️ Game Architecture

```
┌────────────────────────────────────────────────────────┐
│                   Game Loop                            │
│               requestAnimationFrame(loop)              │
└──────────────────────────┬─────────────────────────────┘
                           │
                           ▼
┌────────────────────────────────────────────────────────┐
│                   Physics Update (tick)                │
│  - Apply player velocity & momentum damping            │
│  - Apply gravity (1060 px/s²) & terminal velocity      │
│  - Coyote time & jump buffer tracking                  │
│  - Moving platform sinusoidal oscillation              │
│  - Enemy boundary detection & patrol reversal          │
│  - AABB bounding box collision resolution             │
└──────────────────────────┬─────────────────────────────┘
                           │
                           ▼
┌────────────────────────────────────────────────────────┐
│                    Canvas Render (draw)                │
│  - Biome background gradient interpolation             │
│  - Parallax cloud rendering                            │
│  - Camera offset translation (-cam_x)                  │
│  - Pixel terrain, spring pads, coin blocks & flags     │
│  - Animated particle burst effects                     │
│  - HUD: Level, Coin Counter, and Checkpoints           │
└────────────────────────────────────────────────────────┘
```

---

## 💻 How to Run Locally

Because the entire game is contained in a single self-contained file with no external build steps:

1. **Clone the repository:**
   ```bash
   git clone https://github.com/deepakpradhan1021/Pixel_Path.git
   cd Pixel_Path
   ```

2. **Open in browser:**
   Double-click `index.html` or open it with any local development server (e.g. VS Code Live Server or `python -m http.server 8000`).

---

## 📜 License

This project is open source and available under the [MIT License](LICENSE).
