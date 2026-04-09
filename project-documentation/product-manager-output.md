# Menemen 2: Oceanic Descent - Product Specification

## Executive Summary

- **Elevator Pitch**: A lightweight, fast-paced vertical descent game where players navigate the "Menemen Submarine" deeper into hazardous ocean depths, dodging glowing jellyfish and sea clusters while trying to break their high score.
- **Problem Statement**: The user wants an engaging sequel to the original "Menemen Run" that offers a distinct gameplay loop (moving away from the horizontal Dino Run mechanics) without sacrificing browser performance or adding unnecessary weight. The user also wants to retain access to the first game from a unified start/end screen.
- **Target Audience**: Casual browser gamers and returning players from "Menemen Run" looking for a quick, aesthetically pleasing minigame.
- **Unique Selling Proposition**: A seamless unified launcher screen giving access to two distinct micro-games, combined with a new vertical dodging mechanic that feels smooth, responsive, and visually mesmerizing in an underwater theme.
- **Success Metrics**: 
  - Sub-1-second load times for the canvas elements.
  - Consistent 60FPS on modern web browsers.
  - Positive user feedback on control responsiveness and visual flow.

## Feature Specifications

### Feature: Unified Grand Opening & Game Over Screens
- **User Story**: As a player, I want to see a grand opening screen that gives me the choice between Menemen 1 and Menemen 2, so I can seamlessly choose my experience. When I die, I want the same choices so I can easily retry or switch games.
- **Acceptance Criteria**:
  - Given the app loads, when the splash screen appears, then "Play Menemen 1" and "Play Menemen 2: Deep Dive" buttons are prominent.
  - Given the game ends, when the "Game Over" UI renders, then the exact same navigation choices are present alongside the final score.
- **Priority**: P0
- **Technical Constraints**: Must dynamically hide/show canvases or overlay HTML `div` elements without reloading the page.
- **UX Considerations**: Large, clearly clickable areas, nice hover animations, clean typography to make it feel like a "hub".

### Feature: Oceanic Descent Gameplay Loop (Vertical Scroller)
- **User Story**: As a player, I want to control a falling/diving character moving left and right to dodge obstacles coming from below, so that the game feels fundamentally different from the horizontal runner of Menemen 1.
- **Acceptance Criteria**:
  - Given the player starts Menemen 2, when the game runs, then the environment vertically scrolls upwards (simulating descent).
  - Given the player presses Left/Right arrows (or A/D), when the input registers, then the submarine moves horizontally with smooth acceleration/friction.
  - Given the submarine hits an obstacle (e.g., jellyfish, mine), when collision occurs, then the game transitions to the Game Over state.
- **Priority**: P0
- **Dependencies**: RequestAnimationFrame loop, keyboard event listeners.

### Feature: Dynamic Ocean Environment
- **User Story**: As a player, I want the visual style to look like the ocean depths so it matches the theme perfectly.
- **Acceptance Criteria**:
  - Parallax bubbles rising in the background.
  - The background color smoothly transitions to darker shades of blue as the score (depth) increases.
  - Obstacles are themed (e.g., coral reefs jutting from the sides, jellyfish floating diagonally).
- **Priority**: P1
- **UX Considerations**: Minimalistic vector/canvas rendering to keep it extremely lightweight as per the request. No heavy image assets unless necessary.

---

## Requirements Documentation Structure

### 1. Functional Requirements
- **State Management**: A global game state manager (e.g., `MENU`, `PLAYING_M1`, `PLAYING_M2`, `GAME_OVER`).
- **Input Handling**: Left/Right movement for Menemen 2, Jump/Double Jump for Menemen 1 mapping without conflict.
- **Collision Detection**: AABB (Axis-Aligned Bounding Box) or simple circular collision for Menemen 2 obstacles.

### 2. Non-Functional Requirements
- **Performance**: Vanilla JS + Canvas API. Absolutely no heavy engines (like Unity or Phaser) to keep it lightning fast.
- **Responsiveness**: The canvas should resize appropriately or maintain a standard aspect ratio (e.g., 800x600) scaled to fit the window.

### 3. User Experience Requirements
- **Visual Feedback**: Screen shake on death, bubble burst particles, smooth easing on the menus.
- **Audio (Optional)**: If applicable, underwater ambient sounds or simple synth blips.

---

## Technical Architecture Proposal for "Menemen Hub"
Since we are keeping Menemen 1, the `index.html` structure should be refactored slightly to support a hub:
1. `<div id="ui-layer">` for the Grand Opening and Game Over screens.
2. `<canvas id="game-canvas">` which will be cleared and repurposed by the selected game's logic.
3. Separation of JS logic: `engine.js` (shared loop, UI), `menemen1.js` (runner logic), `menemen2.js` (diver logic).
