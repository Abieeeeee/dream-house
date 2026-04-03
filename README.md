# Dream Villa VR — A-Frame Project

> **Course Submission** | Tools: A-Frame 1.4 · VS Code

---

## Project Structure

```
Examination/
├── index.html                  ← Main VR scene (open this in a browser)
└── assets/
    └── textures/
        ├── marble.jpg          ← Interior floor
        ├── wood.jpg            ← Furniture surfaces
        ├── grass.jpg           ← Garden ground
        ├── concrete.jpg        ← Foundation slab
        ├── water.jpg           ← Pool water layer
        ├── tile.jpg            ← Pool deck / kitchen
        ├── sky.jpg             ← Sky backdrop
        └── wall.jpg            ← Exterior / interior walls
```

---

## Features Implemented

### Rooms (≥3 required)
| Room | Contents |
|------|----------|
| **Living Room** | L-shaped sofa, coffee table, TV unit, bookshelf, floor lamp, ceiling pendant, rug, indoor plant, wall artwork |
| **Bedroom** | Double bed + headboard, pillows, blanket, two bedside lamps, wardrobe, vanity mirror, rug, wall art |
| **Kitchen** | Counter with sink + faucet, upper cabinets, refrigerator, kitchen island + 3 bar stools, pendant light |

### Animated Swimming Pool
- Water surface with colour-shift animation (`animation__ripple1`)
- Gentle bobbing motion (`animation__bob`)
- Custom `water-ripple` A-Frame component for per-tick RGB shimmer
- Underwater point light that pulses
- Pool deck tiles, ladder, lounge chairs, and umbrella

### Lights & Home Decor
- Directional sun (shadow-casting, PCF soft shadows)
- Ambient + hemisphere fill lights
- Animated flicker on all interior point/spot lights
- Wall-mounted facade spotlights
- Garden path lights with breathing animation
- Artwork spotlight in living room

### Additional Models
- 3 palm trees with swaying fronds animation
- Conical background trees
- Decorative bushes along villa walls
- Flower pots at front entrance (rotating bloom animation)
- Patio dining table + 4 chairs
- Garden stepping-stone path
- Perimeter garden wall / fence
- Red sports car with headlights and wheel hubs

### VR & Controls
- `movement-controls` (WASD + arrow keys)
- `look-controls` with pointer lock
- Gaze cursor for mobile (fuse 1.5 s)
- HUD teleport buttons (Garden / Living / Bedroom / Kitchen / Pool)
- Room name label updates on teleport

### Performance
- Textures are 512 × 512 (fast load)
- Shadow map 2048 × 2048 (good quality/perf balance)
- Physical lights + `colorManagement` enabled
- `fog` adds depth and reduces draw-distance cost

---

## How to Run

### Option A — VS Code Live Server (recommended)
1. Open the `Examination/` folder in VS Code
2. Install the **Live Server** extension
3. Right-click `index.html` → **Open with Live Server**
4. Browser opens at `http://127.0.0.1:5500/`

### Option B — Python HTTP server
```bash
cd Examination
python3 -m http.server 8080
# open http://localhost:8080
```

### Option C — Deploy to subdomain
Upload entire `Examination/` folder to your hosting and access at:
```
https://YourIndexNumber.ceiscy.com/Examination/
```

---

## Navigation Controls

| Input | Action |
|-------|--------|
| WASD / Arrow keys | Move |
| Mouse drag / Touch drag | Look around |
| HUD buttons | Teleport to room |
| Headset + controllers | Full VR |

---

## Design Choices

- **Flat-roof Mediterranean villa** — large overhangs, white plaster walls, natural wood accents
- **Warm gold lighting palette** (#ffd07a) — creates luxury ambiance, consistent across all rooms
- **Animated pool** — combines A-Frame `animation` declarative system + a custom JS component for smooth real-time RGB shimmer
- **Procedurally generated textures** — ensures fast load (no external CDN dependencies after initial A-Frame load)

## Technical Challenges

1. **Pointer lock on mobile** — solved by adding gaze cursor (`fuse`) as fallback
2. **Shadow banding** — mitigated with `pcfsoft` shadow type and tight shadow camera bounds
3. **Water animation smoothness** — combined declarative `animation` attributes with a custom `tick()`-based component for more organic colour variation

## Future Improvements

- Replace box primitives with GLTF `.glb` models for higher realism
- Add audio (ambient birds, pool water splash) using `a-sound`
- Implement day/night cycle with a smooth sun arc animation
- Add an interactive front door (open/close on click)
- Network multiplayer using `networked-aframe`
