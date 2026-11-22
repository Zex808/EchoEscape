# EchoEscape

**Echo's Binary Race — Level 1.** A browser game that teaches kids (about 7–12) how binary works, then lets them run one line of real Python: `print(int("101", 2))`.

## Play it

Open `index.html` in a browser. That is the whole install. It is one file with no build step.

- **Move Echo:** tap a lane, or use the ← → keys (A / D also work).
- **Answer gates:** tap a choice, or press 1 / 2 / 3.
- **Pause:** the pause button, P or Esc.
- **Sound:** off until you press the speaker button.
- **Race speed:** a slider on the title screen and the pause screen, 0.5x–1.5x. It is saved on this device and slows the whole simulation down (not just the drawing), so it stays smooth at any frame rate.

The Python panel on the end screen needs an internet connection the first time, to fetch the Python runtime (Pyodide, pinned to 0.29.5, standard library only). Everything else works offline, including onboarding, points and rewards.

## Onboarding, points and rewards

Pressing **Play** (or **Play again**) walks through four quick picks before the race starts: a **subject** (Binary Numbers, or Online Safety - which makes every gate a Kali safety question instead of just the 45s one), an **avatar** (a cosmetic glow colour only - Echo's design never changes), a **course** (Explorer is easier, Trailblazer gives fewer free bits and spawns them faster), and a **mission** (the classic 60-second race, or a shorter 40-second Checkpoint Sprint with gates every 10s). Each pick is a small override of `Level1Rules.config` - see `Game.applyProfile` - so it is still the one built Level 1, just configured differently. Gate questions also get harder across a round: gate 1 asks a concept question, later gates ask you to read or build the actual bits.

Right answers at gates and finishing a race earn points. Points and unlocks are a **guest profile saved in this browser's `localStorage`** (`ee_progress_v1`) - there is no account server, so none of it syncs between devices or survives clearing site data. Doing that for real would need a backend: an authenticated API this code could call instead of `localStorage`, with the server (not the browser) deciding what a round actually earned. Until that exists:
  - every reward grant carries a one-time key (see `Game.sessionId` and `Progress.grant`) so a duplicated or replayed event can't pay out twice
  - loading progress rejects negative or non-numeric points
  - this stops accidental or naive tampering, not a determined user editing `localStorage` by hand in devtools - only a real server can fully close that, which is the point above

**Rewards** (see the `REWARDS` table and the "My rewards" button): two cosmetic Echo glow colours (Mint is default, Rainbow is free at onboarding, Gold unlocks automatically at 150 points - none change Echo's locked design), and three power-ups bought with points from the rewards screen: **Shield** (60 pts, absorbs your next wrong catch, one use), **Rush** (80 pts, +15% race speed for 20 real seconds, stacks on top of your speed slider), **Extra Time** (50 pts, +5 seconds the moment your next race starts, one use).

No payments, no real-world redemption, nothing bought with real money - every number above is just points earned in-game.

## Change it

`index.html` is split into labelled sections. The comment at the top of the file lists them.

| To change | Go to |
| --- | --- |
| Round length, points, penalties, questions, the Python lesson | `2. LEVEL 1 RULES` |
| Which levels exist | `3. LEVELS` (Level 1 is built. Levels 2–5 are placeholders.) |
| Sounds | `4. SOUND` |
| The rewards catalogue (cosmetics, power-ups, cost, effect, duration) | `4b. REWARDS CATALOGUE` |
| Guest points/progress storage and anti-duplicate grants | `4c. PROGRESS` |
| The subject/avatar/course/mission onboarding flow | `4d. ONBOARDING` |
| Controls | `5. INPUT` |
| How the world, track and Echo are drawn | `7. UI: WORLD` |
| Panels and HUD | `8. UI: SCREENS`, plus `STYLES` and `MARKUP` |
| Race speed and per-round session id | `Game` (search `setSpeed` / `applyProfile`) |

### Tests

`test/features.spec.cjs` (Playwright, run with `node test/features.spec.cjs`) covers speed persistence, onboarding progression and config isolation, the gate-question difficulty ramp, reward deduplication/tamper-resistance, and power-up purchase/expiry. It needs no network.

Rules that are not up for change: no game over, every gate opens whatever the answer, Bolt Points only for finishing, no autoplay sound, nothing that feels like hustle. See `00_RUNDOWN_FINAL.txt`.

## Source material

- `MASTER_PROMPT_EchoEscape_Level1.md` — the full build spec.
- `00_RUNDOWN_FINAL.txt`, `01_GRAPHICS_OUTLINE_LOCKED.txt`, `02_FABLE_PROMPT_FINAL.txt`, `STYLE_GUIDE_Echo.txt` — the team's plan.
- `01_Echo_hero.png.webp`, `02_Background_track.png.webp`, `03_Kali_final.webp` — locked art. The Echo and Kali pictures inside the game are crops of these, embedded in `index.html`.
