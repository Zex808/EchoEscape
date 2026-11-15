# EchoEscape

**Echo's Binary Race — Level 1.** A browser game that teaches kids (about 7–12) how binary works, then lets them run one line of real Python: `print(int("101", 2))`.

## Play it

Open `index.html` in a browser. That is the whole install. It is one file with no build step.

- **Move Echo:** tap a lane, or use the ← → keys (A / D also work).
- **Answer gates:** tap a choice, or press 1 / 2 / 3.
- **Pause:** the pause button, P or Esc.
- **Sound:** off until you press the speaker button.

The Python panel on the end screen needs an internet connection the first time, to fetch the Python runtime (Pyodide, pinned to 0.29.5, standard library only). Everything else works offline.

## Change it

`index.html` is split into labelled sections. The comment at the top of the file lists them.

| To change | Go to |
| --- | --- |
| Round length, points, penalties, questions, the Python lesson | `2. LEVEL 1 RULES` |
| Which levels exist | `3. LEVELS` (Level 1 is built. Levels 2–5 are placeholders.) |
| Sounds | `4. SOUND` |
| Controls | `5. INPUT` |
| How the world, track and Echo are drawn | `7. UI: WORLD` |
| Panels and HUD | `8. UI: SCREENS`, plus `STYLES` and `MARKUP` |

Rules that are not up for change: no game over, every gate opens whatever the answer, Bolt Points only for finishing, no autoplay sound, nothing that feels like hustle. See `00_RUNDOWN_FINAL.txt`.

## Source material

- `MASTER_PROMPT_EchoEscape_Level1.md` — the full build spec.
- `00_RUNDOWN_FINAL.txt`, `01_GRAPHICS_OUTLINE_LOCKED.txt`, `02_FABLE_PROMPT_FINAL.txt`, `STYLE_GUIDE_Echo.txt` — the team's plan.
- `01_Echo_hero.png.webp`, `02_Background_track.png.webp`, `03_Kali_final.webp` — locked art. The Echo and Kali pictures inside the game are crops of these, embedded in `index.html`.
