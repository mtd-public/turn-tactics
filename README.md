# Void Armada

A turn-based 3D fleet tactics game for the browser, built for touch first (phones and tablets, portrait or landscape) and also playable on desktop with mouse and keyboard.

Play it: **https://mtd-public.github.io/turn-tactics/**

## How a match works

1. **Deploy.** Place your ships in the three rows nearest you, on any of the four Z-layers of the 8 × 8 × 4 grid. Tap a ship, then tap a node, or drag ships around. AUTO places everything for you.
2. **Scout.** The enemy side starts under fog. Each turn, fog lifts from random sectors, and any ship that moves into a sector clears it.
3. **Engage.** Every ship can move and attack each turn, in either order:
   - **Move** into the 3×3 block around the ship (and one layer up or down). Moving burns fuel from a shared tank that refills a little each turn. Blue nodes are plain moves, yellow nodes put an enemy in range, green nodes pick something up.
   - **Attack** resolves right away. Fighters and grunt suits have one weapon; bigger craft pick from two or three, such as the flagship's Main Guns, Flak Screen (hits everything nearby) and Hadron Lance (pierces a whole line, long cooldown). Reticles and shots are coloured by damage.
   - Hitting a target another ship already hit this turn adds a **combo** bonus (+25% per hit).
   - **Shield** halves incoming damage until your next turn; **Repair** uses a kit. Either one takes the place of the attack.
   - **Dogfight** takes one enemy (and any wingmen beside it) into a real-time skirmish, below.
4. Press **END TURN**. The enemy moves and fires, pirates (if any) take their turn, then the fog sweeps again.

## Battlefield events

- **Fuel depots** (+8 fuel) and **munitions caches** (resets a ship's cooldowns and overcharges its next attack) sit in the fog. Enemies use them too.
- A **derelict cruiser** can be salvaged by any side that keeps a ship beside it for two turns with no rival ship next to it. Your salvage brings kits, fuel and a spare part.
- The **Void Jackals** pirates may warp in partway through. They fight everyone, go after salvage, and their captain remembers you between operations.

## Dogfights

A skirmish zooms into a flat 9 × 9 arena. Its flight model is borrowed from [space-lion](https://github.com/mtd-public/space-lion): your ship always flies forward, you steer with a thumbstick on the lower-left of the screen, and you tap or hold anywhere else to fire at the reticle ahead of your nose. Dodge drifting asteroids, grab repair and overdrive pickups, and use SPECIAL once if the ship has a charged big weapon. Win, lose or break off after 45 seconds; hull damage and kills carry back to the map. The rival ace sometimes challenges SERAPH-01 to a duel on her own.

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
| | `1`–`4` switch Z-layer, `Q`/`E` rotate 90°, `M` move, `F` cycle weapons, `S` shield, `R` repair, `Enter` end turn, `Esc` deselect. Dogfight: WASD/arrows steer, Space fires, `E` special |

Most HUD panels collapse with their ▾ buttons: the timeline, log, comms, hint, fleet dock, and the view and layer rails.

## Look

The board renders at low resolution and is dithered down to a three-colour palette (black, white and one accent, in the style of Downwell), with pixel-art talking-head portraits. Only weapon fire, thrusters and explosions break the palette. Shot colour shows damage: blue under 12, green under 23, yellow under 36, red under 56, violet above.

## Tech

- A single `index.html` with no build step.
- [three.js r128](https://threejs.org/), loaded from cdnjs. A vendored copy in `vendor/` is the fallback.
- Pushes to `main` are published to the `gh-pages` branch by `.github/workflows/pages.yml`.

To run locally, open `index.html` in a browser or serve the folder with any static file server.
