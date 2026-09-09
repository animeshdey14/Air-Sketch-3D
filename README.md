# Air Sketch 3D ⚡🖐️🎨

> **Designed by Animesh_D**
>
> **Mid-Air Hand Gesture Drawing & 3D Hologram AR Synthesizer in Pure WebGL & WebAssembly.**

[![License: MIT](https://img.shields.io/badge/License-MIT-cyan.svg)](https://opensource.org/licenses/MIT)
[![Three.js](https://img.shields.io/badge/Three.js-r128-black?logo=three.js)](https://threejs.org/)
[![MediaPipe](https://img.shields.io/badge/MediaPipe-Hands_0.4-00f0ff?logo=google)](https://developers.google.com/mediapipe)
[![Platform](https://img.shields.io/badge/Platform-Mobile_%7C_Desktop-purple.svg)](#)
[![PWA](https://img.shields.io/badge/PWA-Ready-00ff66.svg)](#)

---

## 📌 GitHub Repository Quick Info

- **Repository Name**: `air-sketch-3d` (or `gesture-air-draw-3d`)
- **Tagline (About Section)**:
  > *Turn your webcam into an interactive mid-air sketchpad. Pinch to draw in 3D air space, voice-describe your sketch, and materialize it into an AR hologram with two-hand gesture manipulation.*
- **Suggested Topics / Tags**:
  `mediapipe`, `hand-tracking`, `threejs`, `computer-vision`, `gesture-recognition`, `augmented-reality`, `webgl`, `web-speech-api`, `pwa`, `mobile-first`, `air-drawing`, `3d-generation`, `creative-coding`

---

## 🌟 Overview

**Air Sketch 3D** transforms any device camera into a futuristic, Iron Man / VisionOS-style mid-air canvas. 

Using **MediaPipe Hands** running entirely in-browser via WebAssembly, the app tracks finger landmarks in real-time. When you pinch your thumb and index finger together, a glowing neon light trail with drifting spark particles follows your fingertip. 

Once your air sketch is finished, describe what you drew using the built-in **Web Speech API** or text, watch the live stopwatch time-frame counter synthesize the object, and interact with the materialized 3D model floating directly over your live camera scene using **two-hand mid-air gestures**!

---

## ✨ Key Features

### 🖐️ 1. Mid-Air Pinch Gesture Drawing
- Real-time 21-point hand landmark tracking via **MediaPipe Hands** (WASM/WebGL).
- Distance metric between **Thumb Tip (Landmark 4)** and **Index Fingertip (Landmark 8)** normalized against hand scale.
- **Hysteresis state machine** (Pinch In `< 0.28`, Pinch Out `> 0.38`) eliminates stroke flickering.
- **Exponential Moving Average (EMA)** smoothing filters out hand tremors for silky smooth brushstrokes.

### 🎨 2. Neon Bloom Canvas & Sparks
- Multi-layer glow rendering with cyber bloom (Cyan, Magenta, Gold, Emerald, Violet, White).
- Dynamic stardust spark emitters trail your movement.
- Full **Undo**, **Clear**, and adjustable **Brush Width**.
- **Touch & Mouse Fallback**: Can also draw directly via touch screen or mouse.

### 🎙️ 3. Voice & Archetype Prompting
- Speak your sketch description using the **Web Speech API** with real-time audio transcription.
- Quick archetype suggestions: *Sports Car, Coffee Mug, Spaceship, Cyber Blade, Diamond Ring, Cute Cat, Magical Tree, Crystal Vase, Heart, Star, Jet Plane, Ringed Planet*.
- Square cyber-thumbnail snapshot preview.

### ⏱️ 4. Live Synthesis Time-Frame & Progress
- High-tech holographic progress modal with an active digital stopwatch timer (`0.00s` → `1.24s`).
- 4-stage visual pipeline: Contour Analysis → Archetype Parsing → Mesh Construction → Camera AR Anchoring.
- Stamped render duration displayed in the 3D HUD info card.

### 👐 5. Two-Hand 3D AR Camera Manipulation
- **Zoom IN / OUT**: Spread hands apart to enlarge, bring hands together to shrink.
- **360° Turntable Rotation**: Move hands horizontally to spin around Y-axis; move vertically to tilt.
- **Steering Roll**: Twist hands relative to each other to roll along the Z-axis.
- **Hologram Pan / Grab**: Pinch with both hands to anchor and move the object around your room.
- **Mode Switching**: Bring hands together quickly (clap gesture) or tap to cycle between:
  1. **Solid PBR Mode** (reflective metallic finish)
  2. **Neon Wireframe Mode** (glowing cyber wireframe)
  3. **Holo X-Ray Mode** (translucent crystal with inner glow)

### 🔊 6. Procedural Web Audio & Haptics
- 100% offline procedural sound synthesis using the **Web Audio API** (tactile clicks, continuous drawing hum, pinch chime, and 3D materialize chords) + vibration haptics (`navigator.vibrate`).

### 💾 7. 3D Model Export
- One-click export to standard **Wavefront `.OBJ`** format for Blender, Unity, Unreal Engine, or 3D printing.

---

## 🕹️ Gestures & Controls

| Gesture / Control | Where | Action |
| :--- | :--- | :--- |
| **🤏 Pinch Thumb + Index** | Drawing Mode | Automatically starts sketching with glowing neon ink |
| **✋ Release Pinch** | Drawing Mode | Stops current stroke and saves to history |
| **👐 Spread Hands Apart** | 3D View | **Zoom IN (+)** — expands the 3D model |
| **🤲 Bring Hands Together** | 3D View | **Zoom OUT (-)** — shrinks the 3D model |
| **↔️ Move Hands Left / Right** | 3D View | **360° Yaw Rotation** around turntable axis |
| **↕️ Move Hands Up / Down** | 3D View | **Pitch Tilt** (tilts model up/down) |
| **🔄 Twist / Tilt Hands** | 3D View | **Roll** (steers model along Z-axis) |
| **🤏 Pinch Both Hands** | 3D View | **Pan / Reposition** hologram in AR camera space |
| **👏 Two-Hand Quick Tap** | 3D View | **Cycle Modes** (Solid PBR ↔ Wireframe ↔ X-Ray) |
| **👆 1-Finger / Mouse Drag** | 3D View | OrbitControls 360° fallback rotation |

---

## 🚀 Getting Started

### Prerequisites
A modern browser with webcam and WebGL support (Chrome, Edge, Safari, Firefox).

### Option 1: One-Click Run (Windows)
Double-click [`start.bat`](start.bat). This will start the local server and automatically pop open **`http://localhost:8080`** in your browser.

### Option 2: PowerShell
```powershell
powershell -ExecutionPolicy Bypass -File .\server.ps1 -Port 8080
```
Then open `http://localhost:8080`.

### Option 3: Python / Node.js
```bash
# Python:
python -m http.server 8080

# Or npx:
npx serve -l 8080 .
```

---

## 📁 Project Architecture

```
air-sketch-3d/
├── index.html            # Main mobile-first application layout
├── manifest.json         # PWA installation manifest
├── start.bat             # One-click Windows launcher
├── server.ps1            # Local HTTP development server
├── css/
│   └── style.css         # Cyberpunk / VisionOS glassmorphism theme & animations
├── js/
│   ├── app.js            # Master state machine & interaction coordinator
│   ├── camera.js         # Camera stream manager with multi-tier driver fallback
│   ├── hand-tracker.js   # Dual-hand MediaPipe tracking, gesture deltas & AR beam HUD
│   ├── canvas-drawer.js  # 2D neon air sketch engine, particles, & snapshot generator
│   ├── audio-fx.js       # Web Audio API procedural sound synthesizer & haptics
│   ├── speech-input.js   # Web Speech voice capture & quick archetype tags
│   ├── shape-extruder.js # 2D sketch to 3D beveled Extrude, Lathe & Tube meshes
│   ├── procedural-3d.js  # Semantic procedural 3D archetypes (car, mug, sword, etc.)
│   ├── three-scene.js    # Three.js AR overlay, OrbitControls & hologram shaders
│   ├── ai-service.js     # Modular 3D synthesis & external AI API adapter
│   └── exporter.js       # Wavefront .OBJ 3D model exporter
└── README.md             # Project documentation
```

## 👤 Author & Design

**Designed by Animesh_D**
- **Creator & Lead Designer**: Animesh_D
- **Project**: Air Sketch 3D (Gesture-to-3D AR Canvas)

---

## 📄 License

Distributed under the **MIT License**. Free for personal and commercial use.
