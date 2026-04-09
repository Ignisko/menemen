# Menemen 3: Galactic Harvest (Product Plan)

### Executive Summary

- **Elevator Pitch**: A fast-paced, retro 8-bit space shooter where Iggy and Ibo pilot a wok-shaped starship to blast cosmic space rocks and space-pirates, harvesting floating ingredients to cook the ultimate Galactic Menemen!
- **Problem Statement**: The Menemen Arcade Hub currently features an endless runner and a vertical descent game. We need to complete the arcade trifecta with a classic space shooter (Galaga/Space Invaders style) that ties into the over-arching culinary theme, offering an instant action format.
- **Target Audience**: Retro arcade enthusiasts, casual web gamers, and fans of the Iggy & Ibo adventures.
- **Unique Selling Proposition**: Blends classic arcade space combat with a cooking twist, maintaining a zero-dependency, lightweight single HTML file form factor.
- **Success Metrics**: High user engagement (measured by replayability), responsive mobile/touch controls, and successful integration of the 3rd game into the Core Hub.

### Feature Specifications

- **Feature**: Space Combat Gameplay
- **User Story**: As a player, I want to maneuver my ship and shoot lasers, so that I can destroy incoming cosmic threats (asteroids and alien pans).
- **Acceptance Criteria**:
  - Given the game is running, when the player inputs left/right (keys or touch), the ship moves smoothly.
  - Given the player inputs UP/Space/Tap, the ship fires neon lasers.
  - Collisions between lasers and threats destroy the threat and add to the score.
  - Collisions between threats and the ship reduce lives.
- **Priority**: P0
- **Dependencies**: Web Canvas API for rendering and collision detection.
- **Technical Constraints**: Keep particle effects lightweight to sustain 60 FPS on mobile browsers.
- **UX Considerations**: Include screen shake on hits and retro Web Audio API explosion sound effects.

- **Feature**: Ingredient Harvesting & Feast Bonus
- **User Story**: As a player, I want destroyed enemies to drop Menemen ingredients, so that I can complete the recipe and earn large bonus points.
- **Acceptance Criteria**:
  - Destroying a threat has a 25% chance of spawning an ingredient (Egg, Tomato, Pepper).
  - Collecting one of each triggers a combo multiplier.
- **Priority**: P0
- **Dependencies**: Combat Gameplay.

### Requirements Documentation Structure

1. **Functional Requirements**  
   - Scrolling starfield background.
   - Dynamic spawn logic for enemy waves and asteroids.
   - Responsive Touch/Keyboard controls (Left/Right + Tap to shoot).
   - LocalStorage for High Score integration (`menemen3Hi`).

2. **Non-Functional Requirements**  
   - Performance targets: Solid 60FPS utilizing `requestAnimationFrame`.
   - Visual: Consistent CRT filter overlay, pixelated Canvas rendering utilizing the `Press Start 2P` font.

3. **User Experience Requirements**  
   - Narrative intro explaining the transition to space ("The universe is hungry...").
   - Consistent UI overlays (score, lives, ingredient HUD) matching Menemen 1 & 2.

### Critical Questions Checklist

- [x] Are there existing solutions we're improving upon? Yes, expanding upon the Menemen engine we established in games 1 and 2.
- [x] What's the minimum viable version? A single-page fixed shooter with one enemy type, asteroids, and three collectable items for version 1.0.
- [x] What are the potential risks or unintended consequences? The difficulty curve might be too steep for casual tap gamers if enemies swarm too fast.
- [x] Have we considered platform-specific requirements? Touch event handling requires `passive: false` to prevent window scrolling.
- [ ] What GAPS exist that you need more clarity on from the user?
  - Do you want the ship to look like a Space-Wok/Pan, or a traditional sci-fi rocket?
  - Should the enemies shoot back, or just act as falling hazards/kamikaze units for version 1.0?
