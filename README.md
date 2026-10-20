TEMPO — A Watchmaker's Arcade
An interactive, gamified horology experience built as one static page. Every scroll, hover, tap and material choice has its own synthesised sound. The whole calibre — dial, case, movement, complications, configurator and rhythm trial — is drawn with CSS and procedural SVG. No frameworks, no audio files.

Run it
Open index.html in a modern browser. That is the whole install.

For a local server (optional):

bash


npx serve .
# or
python -m http.server 8000
Sound is synthesised live with the Web Audio API, so the first entry is deliberately gated behind a click: Enter with sound or Enter silently. The toggle in the top bar switches it on later.

What is scored
Action	XP
Enter the atelier	20
Enter a trial (first time)	10
Log a component while scrolling the calibre	10
Log all 11 components	+40
Log a complication	40
Log all four complications	+60
Make a commission decision (first time per group)	10
Seal a commission	80
Complete the escapement trial	90
Reach a x4 / x8 / x12 combo	10 each
Six marks of the bench sit in the ledger: First Wind, Anatomist, Complicationist, Commissioner, Metronome and Grand Complication. Five ranks run from Apprentice to Grand Complication. Progress, badges, sound preference and the commissioned piece are stored in localStorage (tempo.ledger.v1). The ledger can be wiped from the final section.

Controls
Scroll — the anatomy section explodes the movement; each newly revealed part is logged and makes its own note.
Hover / tap — interactive elements and material swatches have distinct voices.
Complication cards — click or press Enter to log one and hear its signature (tourbillon ticks, calendar carillon, moon chime, minute-repeater gongs).
Commission — choose case, dial and strap; every material has a sound. Seal the commission for a serial number.
Escapement trial — press the BEAT pad or Space as the needle crosses the gold arc. Twelve clean hits. The tempo rises with every hit, and so does the pitch. The page auto-scrolls the dial and beat pad into view before the clock starts.
Sound toggle / volume — top bar and footer.
Files
Code block


index.html          page structure and content
css/style.css       visual system, live watch, responsive layout
js/audio.js         Web Audio synthesis engine (ticks, chimes, gongs, materials, reverb)
js/watch.js         live DOM/CSS watch and timekeeping
js/movement.js      procedural SVG calibre, exploded scroll states, assembly log
js/game.js          escapement rhythm game
js/main.js          XP, ranks, badges, configurator, interactions, persistence
Notes on the sound
All sound is generated at runtime from oscillators, filtered noise and a generated reverb impulse. There are no samples and no network audio. The hero watch ticks every second while it is in view; scroll produces a quiet ratchet; the escapement trial raises a sine pitch with the combo. Audio is muted until a user gesture unlocks it, and respects the mute toggle and volume slider.

Accessibility and motion
Keyboard-operable buttons, cards and material swatches.
Visible focus outlines.
prefers-reduced-motion disables the grain, levitation, tilt and most transitions; the game remains playable.
The game is usable with Space as well as the on-screen BEAT pad.
Colour contrast is tuned for the dark theme; the primary UI avoids colour-only status (labels change as well as colour).
