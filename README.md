# Camera Web Experiments

Camera-based browser experiments that run as standalone HTML pages on GitHub Pages.

## Files

- `index.html` - GitHub Pages launcher for the playable works
- `photon_harp_codex.html` - latest playable version with monochrome camera projection, light strings, and audio/visual effects
- `hand_glitch_v2.html` - hand-tracking glitch visualizer with camera panels, layout switching, snapshots, and audio
- `finger_maze_race.html` - two-player finger maze race game with camera hand tracking, items, and score rounds
- `in_between_v2_1.html` - hand-tracked audiovisual synth with glitch bursts, sustained tones, and phantom autoplay
- `photon_harp.html` - original version
- `camera_test.html` - camera-only diagnostic page for permission and browser checks
- `PHOTON_HARP_9専門家エグ.md` - expert review and project direction notes
- `GITHUB_UPLOAD_GUIDE.md` - upload, GitHub Pages, and camera troubleshooting checklist

## Play

- Launcher: https://apaapaapaapaapa2006-source.github.io/photon-harp-codex/
- Photon Harp: https://apaapaapaapaapa2006-source.github.io/photon-harp-codex/photon_harp_codex.html
- HAND//GLITCH: https://apaapaapaapaapa2006-source.github.io/photon-harp-codex/hand_glitch_v2.html
- Finger Maze Race: https://apaapaapaapaapa2006-source.github.io/photon-harp-codex/finger_maze_race.html
- in_between ... v2: https://apaapaapaapaapa2006-source.github.io/photon-harp-codex/in_between_v2_1.html
- Camera Test: https://apaapaapaapaapa2006-source.github.io/photon-harp-codex/camera_test.html

Open a page in a browser, allow camera access, and hold your hands in front of the camera.

## Photon Harp Controls

- Pinch thumb and index finger to start the drone string.
- Pinch thumb and middle finger to pluck a brighter tone.
- Use the round buttons on the right to toggle sound and visual effects:
  - `ECHO` - repeating delay and ghosted image trails
  - `SHIM` - shimmering high reflections and crystalline scan light
  - `VOID` - dark low resonance and deeper visual pull

## Finger Maze Race Controls

- Player 1 uses the left side, and Player 2 uses the right side.
- Move an index finger from `START` to `GOAL` without touching the walls.
- Pick up orbs for shield, ghost, and glitch effects.
- First player to win 3 rounds wins the match.

## HAND//GLITCH Controls

- Hold both hands in front of the camera.
- Move both hands closer or farther apart to gather and spread the panels.
- Flip a palm to change the color set and layout.
- Use the buttons to take a snapshot, clear panels, change layout, switch mode, or mute audio.

## in_between ... v2 Controls

- Move your fingers to trigger pitched sounds.
- Hold a hand still to swell sustained tones.
- Move quickly to trigger glitch bursts and chord changes.
- Pinch thumb and index finger to create rapid clicks.
- Leave the camera empty for a moment and phantom mode begins playing quietly.

## Notes

These pages use MediaPipe from a CDN, so an internet connection is required unless the dependency is later bundled locally. Camera access works best from `https://` pages such as GitHub Pages.

For publishing and troubleshooting steps, see `GITHUB_UPLOAD_GUIDE.md`.
