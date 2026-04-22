# 🚜 Tiny Tractor

A fullscreen keyboard-smash toy for babies and toddlers. Inspired by [tinyfingers.net](https://tinyfingers.net), but with a friendly 3D Kubota-orange tractor driving around a Texas farm with bluebonnets and a big red barn. Switch to a firetruck any time from the parent panel.

Every key press makes something happen — the vehicle bounces, drives, honks, flashes letters, and sprays confetti. Little fingers can smash away without breaking anything.

## Quick start

It's a single HTML file with no build step and no dependencies to install.

```bash
# Just open it
open tractor.html        # macOS
xdg-open tractor.html    # Linux
start tractor.html       # Windows
```

Or drop `tractor.html` into any static host:
- Netlify Drop, Vercel, Cloudflare Pages, GitHub Pages
- Your own domain's web root
- Any folder served by `python -m http.server`

Three.js loads from a CDN (`cdnjs.cloudflare.com`), so you need an internet connection the first time you open the page.

## How it works

Click **Start Smashing!** to enter fullscreen and let the kid go. Every key you press does something.

### Directional driving

The vehicle turns to face the direction it's driving — no more sideways sliding.

- **Arrow keys** drive the vehicle in big, deliberate moves. First press in a new direction turns the vehicle to face that way; the next press drives it forward. (Just like steering a real vehicle.)
- **Every other key** is mapped to its physical position on the keyboard. Top-row keys push the vehicle away from the camera, bottom-row keys pull it toward the camera, left-side keys drive it left, right-side keys drive it right. So `Q` drives up-and-left, `P` drives up-and-right, `Z` drives down-and-left, `/` drives down-and-right, and so on.
- **Space** makes the vehicle jump in place with a honk and a confetti burst.

### What every key does

| Key | Effect |
|-----|--------|
| Arrow keys | Turn + drive (big, intentional moves) |
| Any letter / number / punctuation | Gentle drive in that key's keyboard quadrant |
| Tab, Caps Lock, Enter, Shift, Backspace, etc. | Also drive based on their physical position |
| Function keys (F1–F10, F12) | Drive in the far-top row |
| Ctrl / Alt / Cmd (pressed alone) | Drive in the bottom row |
| Space | Jump + honk + confetti |
| Anything unmapped (rare) | Hashed to a stable pseudo-position — still moves |

Plus on every single key press: a colorful letter pops up, an emoji may burst, a musical note plays, the vehicle gives a little bounce, and occasionally there's a honk or confetti.

### What's reserved for parents

- **Escape** — always exits fullscreen / closes the tab
- **F11** — toggles browser fullscreen (passed through to the browser)
- **Ctrl/Cmd/Alt + another key** — real modifier combos (Ctrl+W, Cmd+Q, etc.) pass through so you can always close the tab

## Parent panel

Type `parent` on the keyboard to open the settings panel. From there you can:

- Toggle sounds on/off
- Toggle engine rev sounds
- Toggle on-screen letter pops
- Toggle emoji bursts
- **Switch between 🚜 Tractor and 🚒 Firetruck**
- Exit fullscreen

The firetruck has a working flashing red/blue light bar, a ladder on top, silver compartment doors, and a chrome front bumper.

## Scene

- Kubota-orange tractor with a white cab roof, yellow-trim wheels with spokes, a smiley face, glowing headlights, and a chrome exhaust pipe
- Alternate firetruck with flashing lights and a ladder
- Big red barn with a gable roof, cupola, and white X-beam door
- Five patches of Texas bluebonnets scattered across the field
- Wildflowers (yellow, white, pink) dotted around
- Shade trees near the barn
- Drifting clouds
- Soft shadows and a gentle blue-to-green sky gradient

## Tech

- **Vanilla HTML + JavaScript** — single file, no build step
- **[Three.js](https://threejs.org/) r128** for the 3D scene, loaded via ES module import map from CDN
- **Web Audio API** for engine revs, honks, and musical notes (no audio files)
- **CSS animations** for letter pops and emoji bursts

## Safety notes for parents

- Designed to work well with iPad **Guided Access** and Android **screen pinning**, so kids can't accidentally swipe out
- No accounts, no tracking, no storage of any kind
- Escape remains functional so you can always bail out

## Customizing

Everything is in `tractor.html`. Common places to tweak:

- **Vehicle colors / shape** — find `buildTractor()` and `buildFiretruck()` in the `<script>` block
- **Movement amounts** — search for `ARROW_STEPS` (big moves) and the quadrant `step` constant (small moves)
- **Keyboard layout** — `keyboardRows` is a literal grid of every physical key
- **Scene decoration** — barn, trees, bluebonnet patches, and clouds are all built in the same script
- **Sounds** — `playTone`, `playHonk`, `playEngineRev` generate sound procedurally

## License

Do whatever you want with it. Go make kids happy.
