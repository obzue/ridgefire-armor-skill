---
name: ridgefire-armor
description: >
  Design doctrine for Ridgefire-style photoreal side-scrolling armored runners:
  threat scale, fair spawn, theater boards, juice, HUD, and original asset
  pipeline. Use when extending Ridgefire, adding a theater, tuning difficulty,
  or building a similar browser runner that must stay fair at high speed.
metadata:
  short-description: "Armored runner: threat scale, theaters, fair spawns, photoreal boards"
user-invocable: false
---

# Ridgefire armor-run doctrine

Distilled for a browser runner from public game-design practice. It does **not**
vendor or clone third-party engines, art, or code. Patterns were taken from
the strongest open references, then rebuilt as original play and original art.

## What to copy (ideas, not repositories)

| Source | Take | Leave |
| --- | --- | --- |
| photonstorm/phaser groups | Pool actors, bullets, particles. Never allocate per spawn. | The engine itself |
| wayou/t-rex-runner | Speed ramp with a hard cap, day/night as a board change, instant restart, local best | Chrome dinosaur IP |
| Canabalt (Game Developer write-up) | Chunk spawns that always leave a readable gap | Their level script |
| GMTK platformer toolkit | Jump buffer ~140ms, coyote ~120ms, jump cut on release | — |
| Gaffer On Games, Fix Your Timestep | Fixed 1/60 step, delta cap 50ms | — |
| GameHelix/temple_run | Hull bar, i-frames, combo multiplier, procedural Web Audio, mobile buttons | Neon corridor renderer |
| code-yeongyu/gallag-omo-native | Attract scroll, score pops, shake, citation persistence | Galaga layout |
| MuhammadTanveerAbbas/Nebula-Runner-Game | Named difficulty bands the player can read | Space theme |
| leigest519/OpenGame | A living skill: template + verified fixes, not a one-off prompt | Their model weights |
| Kenney CC0 (kenney.nl) | License-safe stylized filler if a prototype needs it | Do not mix Kenney flats into a photoreal theater |

Photoreal military plates are generated originals. Do not drop CC0 pixel packs
into the same camera. If a new theme is stylized on purpose, switch the whole
theater, including the tank.

## Threat scale

Bands are the difficulty contract. Speed is meters/second before boost. Gap is
the minimum seconds between spawn anchors. Reaction distance is `speed * gap`
and must stay above ~300px.

| Band | Name | Where | Promise to the player |
| --- | --- | --- | --- |
| 1 | Contact | Dust Basin | Mines and barriers only. Both are jumpable. |
| 2 | Skirmish | Wadi Cut | Trucks arrive. Rams hurt. Cannon is the clean answer. |
| 3 | Probe | Cedar Line, River Ford | Gunships spawn above the jump apex. |
| 4 | Pressure | Harbor Ash, Drydock | Density rises. Gap shrinks with speed. |
| 5 | Black | Black Hour, Signal Hill | Night plate. Reticle carries more than silhouette. |
| 6 | Crown | Glacier Shelf, Iron Crown | One gunship locks the lane until destroyed. |
| 7 | Afterburn I | Endless, first 1.1 km | Theaters cycle every 700 m. |
| 8 | Afterburn II | Next 1.1 km | Gap sits on the 0.72s fairness floor. |
| 9 | Afterburn III | Next | Multiplier is the score. Hull still comes first. |
| 10 | White Heat | Cap | Speed hard-capped near 18.6 m/s. |

Never spawn two mines back to back. Never spawn a gunship low enough that a
full jump intersects it. Trucks may be barely clearable. Bosses are targets,
not rams. Do not respawn the Crown gunship after it drops.

## Boards

Five plates, two sectors each, then an endless cycle:

1. Dust Basin
2. Cedar Line (River Ford adds rain)
3. Harbor Ash (Drydock adds dusk)
4. Black Hour
5. Iron Crown (alpine storm)

A new theater needs a scenery-only 16:9 plate with an empty lower road, a
ground-line fraction, a short musical motif, and two sectors on the scale.
Do not bake enemies, UI, or the player into the plate.

## Controls

Side view, not a chase camera.

- A / Left moves the hull left on screen.
- D / Right moves right and boosts.
- W boosts. S brakes. Space jumps. X or pointer fires along the reticle.

## Juice

Screen shake on hit, short hit-stop on a kill, score pops, combo up to x4,
track dust, muzzle flash, i-frame blink, weapon timer, drone battery.
Shake never moves hitboxes.

## Audio and save

Unlock Web Audio inside the first gesture. Music and effects use separate
gains. Map sliders with slider squared. Persist best score, sectors cleared,
mix, and citations in localStorage with a version field. No accounts required.

## Asset pipeline

1. Scenery plate, 16:9, no actors.
2. Sprites as 2x2 grids on flat magenta, one subject, consistent scale.
3. Enemies that approach from the right are drawn flipped. The player faces right.
4. Hitboxes use the opaque fraction of the cell, not the transparent padding.
5. Reject a sheet that touches a cell edge or changes scale between frames.

## Do not

- Uncap speed.
- Use setInterval for the simulation.
- Award distance with the combo multiplier (kills only).
- Mix a second art style into an existing plate.
