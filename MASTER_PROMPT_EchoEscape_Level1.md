# Master Prompt — Echo's Binary Race (Level 1)

**Intended recipient: Fable 5.2.** Feed this prompt to Fable 5.2 to generate the build.

Synthesized from: `00_README_FOR_EMO.txt`, `00_RUNDOWN_PLAN_PLAN_PLAN.txt`, `FABLE_PROMPT_Echo_Level1_Python.txt`, `STYLE_GUIDE_Echo.txt`, `01_Echo_hero.png.webp`, `02_Background_track.png.webp`, the later "final pack" supersession (`00_RUNDOWN_FINAL.txt`, `01_GRAPHICS_OUTLINE_LOCKED.txt`, `02_FABLE_PROMPT_FINAL.txt`, `03_Kali_final.webp`), plus decisions confirmed by the requester (real stdlib-only Python execution, a play-again button, Fable 5.2 as the build target). Kali's design is now locked via `03_Kali_final.webp` — the earlier "art pending" note is resolved. See the accompanying chat message for source notes, conflicts, an asset checklist, and remaining gaps.

---

## 1. Build this

A single-file HTML5 browser game, **"Echo's Binary Race — Level 1,"** for a kids' Python-teaching program. It must open directly in a browser (double-click or static file server) with zero build step and zero install step.

## 2. Players & learning goals

- **Audience:** kids ~7–12 (`FABLE_PROMPT_Echo_Level1_Python.txt:1`), phone-friendly, high-contrast (`00_RUNDOWN_PLAN_PLAN_PLAN.txt:59`, `FABLE_PROMPT_Echo_Level1_Python.txt:13`).
- **Learning goals, in priority order** (`00_RUNDOWN_PLAN_PLAN_PLAN.txt:31-44`):
  1. **Binary** — how computers count in 0/1.
  2. **Code literacy** — 3 readable lines of real code behind the game.
  3. **AI literacy** — Echo (the in-game AI companion) *explains*; it never does the kid's work for them.
  4. **Digital safety** — a security-themed checkpoint (password strength, suspicious links).
  5. **Python basics** — this level's concrete skill is `print(int("101", 2))` → converts a binary string to the decimal number `5` (`00_RUNDOWN_PLAN_PLAN_PLAN.txt:39`, `00_README_FOR_EMO.txt:15-16`, `STYLE_GUIDE_Echo.txt:6`).
  - Teaching rule: **"You write 3 lines, you see Echo do it, you save it, you check it."** (`00_RUNDOWN_PLAN_PLAN_PLAN.txt:44`) — the end screen is interactive, not just a scoreboard.

## 3. Core gameplay loop

One round = 60 seconds, 3 lives, no game-over state (`00_RUNDOWN_PLAN_PLAN_PLAN.txt:23-28`):

1. Binary digits (bits) fall down a **3-lane neon track**. The target is a binary number in the 0–7 range, shown in **3 bit slots**.
2. Player catches falling bits **left to right, in order**, to fill the 3 slots.
   - Correct catch: **+100 points**, a chime, the slot lights mint green.
   - Wrong catch: a shake effect, **−2 seconds** off the clock. **No life lost, no game over.**
3. **Gate event every 15 seconds:** a 3-choice binary question.
   - Correct → speed boost.
   - Incorrect → a one-line friendly explanation is shown, **and the gate opens anyway.** No-fail is absolute.
4. **Kali checkpoint at 45 seconds:** one digital-safety question (e.g., which password is safer, should you click this link). Same no-fail rule — answering "wrong" teaches, never blocks or penalizes progress.
5. **End screen** shows: final score, **Bolt Points** (awarded only for finishing the level — not for score, speed, or accuracy), a binary↔decimal summary of the round's target numbers, the 3-line Python block (see §12), and a **Play Again** button that restarts a fresh 60-second round (confirmed by requester; not itself sourced from the docs, but the minimum needed for a replayable, testable game).

## 4. Controls

- Left/right lane movement to catch falling bits: keyboard arrows **and** touch/tap or drag for mobile (phone-friendly is an explicit requirement; exact touch scheme is not specified in source material — implement tap-to-lane or swipe, whichever reads as more obvious to a 7–12-year-old, and keep hit targets large).
- Gate and Kali checkpoint questions: tap/click one of 3 answer choices.
- One manual, visible **audio on/off toggle**. **No autoplay audio under any circumstance** (`00_RUNDOWN_PLAN_PLAN_PLAN.txt:28`, `FABLE_PROMPT_Echo_Level1_Python.txt:13`).

## 5. Progression

- This build ships **Level 1 only, fully playable.**
- Code must include a `LEVELS` registry/array with Level 1 implemented and **placeholder (non-functional, clearly stubbed) entries** for:
  - Level 2 — Loop
  - Level 3 — Cipher
  - Level 4 — Echo Beat
  - Level 5 — Hex
  (`00_README_FOR_EMO.txt:20`, `00_RUNDOWN_PLAN_PLAN_PLAN.txt:29`, `FABLE_PROMPT_Echo_Level1_Python.txt:11`)
- **Do not build Level 2 or beyond.** Planning docs explicitly block this until Level 1 is played and kid feedback is collected (`00_README_FOR_EMO.txt:20`, `00_RUNDOWN_PLAN_PLAN_PLAN.txt:60`).
- Bolt Points have no spend/shop mechanic in any source file — treat them as a pure completion acknowledgment, not a currency, unless told otherwise.

## 6. Feedback & non-negotiable design rules

Direct from `00_RUNDOWN_PLAN_PLAN_PLAN.txt:46-54` and `00_README_FOR_EMO.txt:22` — treat these as hard constraints, not style suggestions:

- **No-fail gates**: every gate and checkpoint opens regardless of the answer; wrong answers get a friendly, short explanation, never a penalty beyond the normal catch-mistake clock cost.
- **No loot boxes, no streaks, no punishing timers, no pay-to-win, no FOMO, no dark patterns, no "come back or lose it."**
- **Bolt Points only for finishing** the level — never for speed, score, or spending.
- If any feature *feels* like a hustle mechanic, cut it rather than ship it.

## 7. Accessibility

- High contrast required (`FABLE_PROMPT_Echo_Level1_Python.txt:13`).
- Phone-friendly / responsive layout required (`00_RUNDOWN_PLAN_PLAN_PLAN.txt:59`, `FABLE_PROMPT_Echo_Level1_Python.txt:1,13`).
- No reliance on audio for comprehension — audio is manual-toggle and must not be required to understand what to do (consistent with no-autoplay rule).
- Source material specifies no additional accessibility requirements (no stated colorblind mode, screen-reader support, or font-size control) — flagged as a gap in the summary below.

## 8. Story & characters

- **Echo** — small robot companion, **the established reference image is final; do not redesign.** Gunmetal metal body, large round eyes showing scrolling green code/digit rain, antenna, black knit beanie, black over-ear headphones, black zip hoodie with "ECHO" in bright neon green bubble lettering across the chest, three hexagonal badges above the text reading **H / Si / Au**, a rainbow-stripe patch on the sleeve, visible articulated metal hands (reference shows Echo holding an open laptop with green code on-screen) (`00_RUNDOWN_PLAN_PLAN_PLAN.txt:4-12`, `01_Echo_hero.png.webp`, `STYLE_GUIDE_Echo.txt:3`).
- **Kali** — the digital-safety checkpoint character at the 45-second mark. **Design is now LOCKED via `03_Kali_final.webp` — do not invent another Kali** (`00_RUNDOWN_FINAL.txt:7,30-32`, `01_GRAPHICS_OUTLINE_LOCKED.txt:4`). A small blue dragon: rounded, cute scaled face with a large genuine smile; large green eyes containing soft, non-distracting binary-digit patterns; no beanie; a row of small horns across the top of the head plus two larger side horns; bat-like wings, slightly oversized, with a neon-green CSS/sprite glow; a black hoodie bearing a glowing green circuit-board line pattern ("OA circuit design" per the source doc — meaning unconfirmed, reproduce the pattern shown in the reference rather than inferring an acronym) and "KALI" in the same neon-green bubble lettering style as Echo's hoodie text; a round shoulder patch on the left arm showing a green alien head on a red/yellow/green ("Rasta") striped background, styled like the Alienware alien logo; the figure fades out toward the bottom edge in the reference (it's a bust/portrait crop, not a full body). Same space/nebula backdrop as Echo's own reference image.
- **Outstanding Kali asset, per the team's own checklist** (`00_RUNDOWN_FINAL.txt:37`): a cropped in-game sprite/bust for the checkpoint panel does not exist yet as a separate file — crop one from `03_Kali_final.webp` for this build; a dedicated sprite is not required to ship.
- **No other named characters appear anywhere in the repository.**

## 9. Visual style

- **Palette** (`STYLE_GUIDE_Echo.txt:2`): background black `#0c0a09`; mint `#34F0A4`; electric neon green `#00FF88`; deep blue `#1A3CFF`; purple nebula tones.
- **World — one world only, do not build multiple backgrounds** (`00_RUNDOWN_PLAN_PLAN_PLAN.txt:14-20`): deep black starfield with purple/blue nebula swirl, two comets with trails, binary 0/1 rain (more opaque per the locked reference, still layered behind the track), an electric neon-green 3-lane track with etched circuit-board line patterns and lane dots, a large glowing mint gate on the horizon. The reference image (`02_Background_track.png.webp`) additionally shows glowing teal alien flora along the track edges and a reflective ground surface — treat these as part of the locked reference, not inventions.
- Three framings of the same single world are referenced: START (wide), RACE (on-track), GATE (darker, zoomed) (`00_RUNDOWN_PLAN_PLAN_PLAN.txt:19`).
- Use the provided images as **visual reference for style**, not necessarily as a literal background image — if the photographic reference hurts in-game readability at gameplay speed, redraw a simplified code-drawn version so Echo and the falling bits stay legible (`00_RUNDOWN_PLAN_PLAN_PLAN.txt:59`).

## 10. Audio

- Manual on/off toggle only. No autoplay audio, anywhere, under any condition.
- No specific sound asset list, music style, or SFX palette exists in any source file beyond "chime" on correct catch (`00_RUNDOWN_PLAN_PLAN_PLAN.txt:25`). Treat audio content itself as an open gap (see checklist below).

## 11. Interface & required art/audio assets

- **UI must show, in-game, without relying on external assets beyond what's listed:** 3 bit slots, falling bits, lane track, lives indicator, 60-second timer, score, gate question UI (3 choices), Kali checkpoint UI (1 question), end screen (score, Bolt Points, binary/decimal summary, 3-line Python block, Play Again button), audio toggle control.
- **Provided assets, all locked, do not redesign** (`00_RUNDOWN_FINAL.txt:4-7`):
  - `01_Echo_hero.png.webp` — Echo reference art.
  - `02_Background_track.png.webp` — world/background reference art, labeled as "binary more opaque version."
  - `03_Kali_final.webp` — Kali reference art (see §8).
- **Explicitly deferred by the team itself, with a stated fallback** (`00_RUNDOWN_FINAL.txt:37-41`, `01_GRAPHICS_OUTLINE_LOCKED.txt:5`): a cropped Kali in-game sprite/bust (fallback: crop from `03_Kali_final.webp`), a title logo (fallback: text in code), and UI icons (fallback: code-drawn). The team's own note: *"No more art needed to START."*
- **Not provided, needed, and not found anywhere in this repo:** sound/music files. See the checklist below.

## 12. Technical requirements

- **Format:** one self-contained HTML file (HTML/CSS/JS inline), matching the explicit instruction in `FABLE_PROMPT_Echo_Level1_Python.txt:1` and `00_RUNDOWN_PLAN_PLAN_PLAN.txt:59`. The repository currently has **no existing code, framework, or package manifest** — this is a greenfield single-file build, so there is no existing stack to preserve other than this single-file convention itself.
- **No unnecessary dependencies**, with one confirmed exception: the Python runtime below. No build step, no bundler, no extra JS framework, nothing the kid or a parent has to install by hand.
- **Required internal architecture** (explicit in three of the four planning files — `00_README_FOR_EMO.txt:20`, `00_RUNDOWN_PLAN_PLAN_PLAN.txt:29`, `FABLE_PROMPT_Echo_Level1_Python.txt:11`): separate, clearly named code sections/modules for:
  - **Game Loop**
  - **Input**
  - **UI**
  - **Level 1 rules**
  - **A `LEVELS` registry** holding Level 1 (active/implemented) plus stub entries for Levels 2–5 (inactive, clearly marked as not implemented, must not be reachable or break the game if selected).
  This separation exists specifically so another developer or model can extend it later without rewriting Level 1.
- **Python teaching mechanic — real execution, stdlib only.** Confirmed by both the requester and the team's own final doc: **"Real Python, zero install, stdlib only"** (`00_RUNDOWN_FINAL.txt:17`, `02_FABLE_PROMPT_FINAL.txt:11`). The kid's 3 lines must actually run as real Python, not a simulated/canned output; nothing may require the kid (or a parent) to manually install anything; and nothing in the Python snippets may depend on a third-party package — every snippet across Levels 1–5 (`print`, `int`, `for`/`range`, `if`/`else`, lists, `hex`) is pure standard-library/builtin Python, so this is achievable without ever installing a package.
  - Use **Pyodide** (a WebAssembly CPython build) loaded via a single `<script>` tag pointing at a CDN (e.g. the official `pyodide.js` CDN URL), initialized automatically on page load with a visible "loading Echo's brain…" state while it downloads — this is the only sanctioned exception to "single file, no dependencies," and it's the only practical way to get real, zero-install Python running in-browser. Do not call Pyodide's `micropip` or load any non-stdlib package — none is needed for any Level 1–5 snippet.
  - The kid's typed/tapped code is passed to Pyodide's `runPython`, and the **actual** printed result is what's displayed (e.g. running `print(int("101", 2))` must genuinely produce `5` from the Python interpreter, not a hardcoded string).
  - **Trade-offs to flag to the team, since they affect "opens directly, no install" in practice:** (1) first load requires an internet connection to fetch the Pyodide runtime (several MB) — the game is not fully offline-capable the first time it runs; (2) there will be a short loading delay before the Python-dependent parts of the end screen are usable; (3) this is a real external dependency (a CDN fetch), which is a deliberate, confirmed exception to the "no unnecessary dependencies" principle, not an oversight.
  - If Fable 5.2 cannot wire up Pyodide reliably, flag it back rather than silently falling back to a simulated/fake result — the "real Python" requirement is explicit and non-negotiable per the requester.

## 13. Acceptance criteria (playable, testable result)

The build is done when all of the following are true:

- [ ] Opens in a browser from the file directly, no server or build step required.
- [ ] Renders correctly on a phone-width viewport and in high contrast.
- [ ] Echo's appearance matches the locked reference description in §8 without redesign.
- [ ] One world, three framings (start/race/gate), matching §9 — no extra backgrounds.
- [ ] A full round runs: 60-second timer counts down, 3 lives tracked, bits fall and are catchable left-to-right into 3 slots.
- [ ] Correct catch: +100 score, chime (if audio on), slot lights mint. Wrong catch: shake, −2s, **no life lost, no game over ever.**
- [ ] A gate event fires every 15 seconds with a 3-choice question; right answer boosts speed; wrong answer shows a one-line explanation and **the gate opens regardless.**
- [ ] A distinct Kali checkpoint fires at 45 seconds with one safety question, same no-fail behavior as gates, using the locked Kali design from `03_Kali_final.webp` (a cropped bust/sprite is acceptable — see §8).
- [ ] End screen displays: score, Bolt Points (awarded for finishing only), a binary→decimal summary, the 3-line Python block, and a working **Play Again** button that starts a fresh round.
- [ ] The 3-line Python block actually executes via a real Python runtime (Pyodide, stdlib only, no `micropip`/package installs) and displays its genuine output — `print(int("101", 2))` must be computed, not hardcoded.
- [ ] Audio is off by default; a visible manual toggle turns it on; nothing plays automatically.
- [ ] No loot boxes, streaks, countdown-pressure dark patterns, or pay-to-win mechanic exists anywhere in the build.
- [ ] Code contains a `LEVELS` registry with Level 1 playable and Levels 2–5 present only as inert placeholders — selecting/encountering them must not crash or unlock gameplay.
- [ ] Game Loop, Input, UI, and Level 1 rules exist as separable, identifiably-named sections of the code.

## 14. Guidance for future modification

- Whoever extends this (model or developer) should **only** add to the `LEVELS` registry and implement the next level's own rules module — Game Loop, Input, and UI are meant to be reused, not forked per level.
- Do not alter Echo's design, the world's visual identity, or the no-fail/no-hustle rules in §6 when adding levels; those are locked product decisions, not implementation details.
- Each future level has a named concept and Python line already specified in `00_RUNDOWN_PLAN_PLAN_PLAN.txt:40-43` (Level 2 Loop: `for i in range(3): print("Echo says hi")`; Level 3 Cipher: `if password == "strong": ... else: ...`; Level 4 Echo Beat: `beat = [1, 0, 1, 1]`; Level 5 Hex: `print(hex(255))`) — treat these as the intended direction, not yet authorized for implementation.
- Per the team's own process rule: **"if it's not in GitHub, it didn't happen"** (`00_RUNDOWN_PLAN_PLAN_PLAN.txt:53`) — any change to scope, character design, or rules should be committed, not just discussed.
