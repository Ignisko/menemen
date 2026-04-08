# 🍳 Menemen Run

A lightweight endless runner game where a pixelated Turkish guy dodges pans, crates, and chickens while collecting ingredients to make the perfect **menemen**.

Inspired by Chrome Dino & Edge Surf — but with more mustache.

## 🎮 Play

**[▶ Play on GitHub Pages](https://ignisko.github.io/menemen/)** — or just open `index.html` locally.

## 🕹️ Controls

| Action | Desktop | Mobile |
|---|---|---|
| Jump | `Space` / `↑` | Tap screen |
| Crouch | `↓` | — |

## 🎯 Gameplay

- **Auto-run** to the right — survive as long as you can
- **Dodge** obstacles: pans 🍳, crates 📦, chickens 🐔
- **Collect** ingredients: eggs 🥚, tomatoes 🍅, peppers 🌶️
- Collect **all three** ingredient types → **MENEMEN COMBO (+50 pts)** + scene changes from outdoor street to kitchen!
- Speed increases over time — soft cap at 2×, then keeps climbing slowly
- High score saved locally

## ✨ Features

- **Single HTML file** — zero dependencies, zero build step
- **< 25 KB** total size
- **Pixel art** drawn entirely in code via Canvas API
- **Web Audio API** sound effects (no audio files)
- **Offline** — works without internet
- **Mobile** — responsive canvas + touch controls
- **Scene transition** — outdoor street → kitchen interior after combo

## 🏗️ Technical

- Plain JavaScript + Canvas 2D
- No frameworks, no libraries, no external assets
- `requestAnimationFrame` game loop
- AABB collision detection with forgiveness margin
- `localStorage` for high score persistence
- Loads instantly on any modern browser

## 📄 License

MIT
