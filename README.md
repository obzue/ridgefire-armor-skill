# Ridgefire armor-run skill

Design doctrine for **Ridgefire: Armor Run**, a photoreal side-scrolling armored runner.

This repository records the patterns worth keeping. It does **not** vendor Phaser, Kenney packs, T-Rex Runner, or any other third-party game. Those projects were read for structure (pooling, fair gaps, jump forgiveness, named difficulty bands, juice). The playable game uses original generated plates and sprites.

## What is here

- `SKILL.md` — the skill: threat scale, boards, controls, audio, save, asset rules.
- Use it when adding a theater, retuning speed, or building a sister runner.

## Threat scale

| Band | Name | Promise |
| --- | --- | --- |
| 1 | Contact | Mines and barriers. Both jumpable. |
| 2 | Skirmish | Gun trucks. Shoot them. |
| 3 | Probe | Gunships above the jump. |
| 4 | Pressure | Denser harbor. Gaps shrink with speed. |
| 5 | Black | Night. Trust the reticle. |
| 6 | Crown | One gunship holds the lane until it drops. |
| 7–10 | Afterburn → White Heat | Endless. Speed caps near 18.6 m/s. |

## License of this text

The doctrine text in this repo is released under CC0. Game art and the playable build are not included here.
