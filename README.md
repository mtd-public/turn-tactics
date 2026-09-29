# Void Armada

A turn-based 3D fleet tactics game for the browser, built for touch first (phones and tablets, portrait or landscape) and also playable on desktop with mouse and keyboard.

Play it: **https://mtd-public.github.io/turn-tactics/**

## How a match works

1. **Deploy.** Place your ships in the two rows nearest you, on any of the four Z-layers of the 8 × 8 × 4 grid. Tap a ship, then tap a node, or drag ships around. AUTO places everything for you.
2. **Scout.** The enemy side starts under fog. Each turn, fog lifts from random sectors, and any ship that moves into a sector clears it.
3. **Engage.** Each ship gets one move and one action per turn:
   - **Move** burns fuel (a shared pool that refills a little each turn). Heavier ships burn more per cell.
   - **Fire** queues an attack. Closer shots hit harder, and each extra ship firing on the same target adds 25% (focus fire).
   - **Shield** halves incoming damage until your next turn.
   - **Repair** uses a repair kit.
   - **Charge** arms the ship's special for its next shot (Hadron Lance, Missile Storm, Twin Buster, Torpedo Run).
4. Press **ENGAGE**. Your orders resolve, the enemy moves and fires, then the fog sweeps again.

Sink the enemy dreadnought **Grauhalle** to win. If your flagship **Hyperion** is lost, the match is over.

## War timeline

The strip under the status bar has one notch per turn, up to turn 12, when the enemy main fleet arrives and forces a withdrawal. Notches mark reinforcement waves. Near turns show wave size (▮ to ▮▮▮) and ◆ for an elite signature. Far turns only show rough signals (▲, ~). Tap the timeline for an intel summary.

## Campaign

Each match is one operation in an ongoing campaign:

- **Victory** loots supplies (repair kits, fuel, spare parts) for the next operation.
- **Withdrawing** (FLEE, or the timeline running out) and **defeat** bring no loot. Destroyed and badly damaged ships go to the repair bay and sit out the next one or two operations. Spare parts shorten repairs.
- **Valor heroes:** your officers earn valor from kills, specials and victories. Their portraits change as they level up: slicked-back hair, then a flight jacket, then aviators.
- **Rivals and villains:** the enemy ace, Capt. Sigrun Vex, and Marshal von Grau escape when beaten and come back marked by it: a scar, then an eyepatch, then a cybernetic eye.
- Wins unlock extra palettes, selectable from the ≡ menu.

The campaign and the match in progress are saved in your browser (`localStorage`). Reopening the page resumes where you left off. **New Campaign** on the title screen erases the save.

## Controls

| Touch | Mouse / keyboard |
| --- | --- |
| Drag empty space to orbit | Left-drag to orbit |
| Pinch to zoom, twist to rotate | Scroll to zoom |
| Two-finger drag to pan | Right-drag or Shift-drag to pan |
| Tap ships, nodes and reticles | Click, or drag ships to move them |
| | `1`–`4` switch Z-layer, `Q`/`E` rotate 90°, `M` `F` `S` `R` `C` for actions, `Enter` to engage, `Esc` to deselect |

Most HUD panels collapse with their ▾ buttons: the timeline, log, comms, hint, fleet dock, and the view and layer rails.

## Look

The board renders at low resolution and is dithered down to a three-colour palette (black, white and one accent, in the style of Downwell), with pixel-art talking-head portraits. Only weapon fire, thrusters and explosions break the palette. Shot colour shows damage: blue under 12, green under 23, yellow under 36, red under 56, violet above.

## Tech

- A single `index.html` with no build step.
- [three.js r128](https://threejs.org/), loaded from cdnjs. A vendored copy in `vendor/` is the fallback.
- Pushes to `main` are published to the `gh-pages` branch by `.github/workflows/pages.yml`.

To run locally, open `index.html` in a browser or serve the folder with any static file server.
