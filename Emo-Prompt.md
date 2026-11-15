"Build Level 1 ('Jolt's Binary Race') as a single-file HTML5 arcade game for kids aged 7-12, built with a clean, modular architecture so we can easily plug in new levels later.

Core Architecture Requirements:

Keep the core game loop, input handler (arrow keys & touch drag), and UI shell cleanly separated from the Level 1 rule logic.

Theme & Style: Black background (#0c0a09), mint green accents (#34F0A4), chunky retro arcade typography, high-contrast, fully responsive for mobile and desktop.

Level 1 Mechanics (Binary Catcher):

Show a decimal target number (0 to 7) at the top with 3 empty bit slots.

Bits (0 or 1) fall from the top one by one. The player must catch them in strict left-to-right order to fill the binary sequence.

Correct catch: +100 points, happy chime, slot lights up mint green.

Wrong catch: Jolt shakes, minor time penalty, no game over.

When all 3 slots fill, award a time bonus and generate a new target number.

Every 15 seconds, trigger a gate with a multiple-choice binary question (3 answers). Right answer = speed boost; wrong answer = a short friendly 1-line explanation from Jolt and the gate opens anyway.

Run timer: 60 seconds. When time ends, display final score, total Bolt Points, decimal/binary summary, and the 3 lines of code behind the game logic.

Include a manual audio toggle (no autoplay audio ambush)."

