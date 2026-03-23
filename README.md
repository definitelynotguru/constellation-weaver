# Constellation Weaver

*A relaxing, infinitely replayable cosmic creativity tool where you draw constellations by connecting drifting stars in a 3D void.*

```
         *  .  *        .            *
    .        *      .    *    .          .
         .        *              .
              .           *
    *    .         .        .     *
         .   *  .     .   *    .
       .    \   |   /      .
         .    \ |  /   .       *
    * .   ----  *  ----   .        .
         .    / | \     .
       .    /   |   \      .
    .        *      .    *      .
         *      .         *        .
              .      *        .
```

Every connection glows with neon trails and flowing particles. Complete a shape and the universe whispers back -- a procedurally generated myth fades in as elegant text, your stars rearrange into perfect position, and new stars are born nearby as rewards.

Zero pressure. No timer. No failure. Just you, the void, and endless constellations to discover.

[Test it here.](https://definitelynotguru.github.io/constellation-weaver/)

---

## Features

### Drifting Star Field
800 to 2500 stars float gently through a dark cosmic void, each with its own twinkle rhythm and subtle orbital drift. Stars vary in size and color -- young stars burn bright white-cyan, ancient stars glow deep gold. A soft exponential fog dissolves the distant edges into perfect black.

Use the **Star Count** slider to tune the density from sparse to dense. The change takes effect instantly without reloading.

### Connection Drawing
Click any star to select it, then click a second star to draw a glowing line between them. Lines animate with living particle trails that flow from start to end along an ease-in-out curve. Line color shifts with distance -- short connections burn cyan, long ones stretch toward magenta and gold.

Each new line increases bloom intensity, making your constellation glow brighter as it grows.

**Right-click** (or long-press on mobile) to undo the last line. There is no limit -- draw freely, undo freely.

### Completion Detection and Myth Revelation
When you close a loop or accumulate 8 to 12 lines in a coherent shape, the system evaluates your constellation. If it qualifies:

* The camera gently orbits your new creation
* The connected stars smoothly rearrange into perfect geometric alignment over 3 seconds
* 4 to 8 new brighter stars spawn nearby as a reward
* A procedurally generated myth fades in at the center of the screen

Myths are built from 30+ base templates with word-level recombination:

```
"The [Animal] of [Emotion]"
"The [Object] that [Action] the [Concept]"
"The [Title]'s [Relic]"
```

Every myth is unique. The Myth Atlas (accessible via **Show Atlas**) collects every myth you have discovered across sessions, stored in your browser.

### Shooting Star Events
Every 20 to 40 seconds, a brilliant shooting star streaks across the sky dome trailing 60 glowing particles. If it passes near an existing star, a golden suggestion line fades in -- click it within 5 seconds to accept the connection, or watch it dissolve away.

Shooting stars are pure ambient events. You can engage with them or ignore them entirely.

### Real Astronomical Constellations
Hidden within the star field are 7 real Earth constellations: Orion, Big Dipper, Cassiopeia, Scorpius, Leo, Cygnus, and Pegasus. When your drawn connections match a real pattern (evaluated via pairwise distance matching with rotation invariance), you unlock it with a special gold discovery effect and its authentic ancient mythology.

Discovered real constellations are marked with a star symbol in your Myth Atlas and persist across sessions via localStorage.

### Auto-Weave Mode
Toggle **Auto-Weave** to let the universe take the pen. Every 45 to 90 seconds, the system connects 2 to 3 stars using a weighted algorithm that prefers golden-ratio angles and symmetry. Auto-Weave completes constellations, triggers myths, and continues indefinitely -- perfect for a second monitor or background ambiance.

### Seed Codes
Every constellation you build can be shared as a compact alphanumeric seed code. Click **Share** to generate your code, copy it, and send it to anyone. They paste it into the import field and click **Load Constellation** to rebuild your exact star connections against their own star field. The code encodes normalized connection pairs using base64url JSON.

### Procedural Ambient Audio
Click **Start Ambient** to initialize the generative soundscape. Four layered Web Audio oscillators create a living cosmic drone:

* **Base drone** -- two detuned sine waves at 40Hz and 60Hz, barely audible, felt more than heard
* **Harmonic pad** -- root, fifth, and octave sine waves that fade in as you draw more connections
* **Shimmer layer** -- high-frequency oscillators with slow random LFO detune modulation
* **Twinkle accents** -- occasional pentatonic notes (C major pentatonic) that chime as connections grow

The **Ambient Vol** slider controls the master volume of all layers in real time.

### Visual Polish
* **Bloom post-processing** -- UnrealBloomPass tuned for soft neon halos around every star and line
* **Twinkle shader** -- per-instance vertex color modulation with unique phase offsets so every star sparkles independently
* **Particle trails** -- 40 instanced particles per line, flowing along an ease-in-out path with opacity that fades head to tail
* **FBM nebula background** -- a slowly rotating BackSide sphere with layered fractal noise in deep purple and blue, barely visible but adding cosmic depth
* **Mobile support** -- touch orbit, pinch zoom, and long-press to undo

---

## Controls Reference

| Input | Action |
|---|---|
| Left-click drag | Orbit camera |
| Scroll / pinch | Zoom in and out |
| Left-click star | Select first connection point |
| Left-click second star | Draw connection |
| Right-click / long-press | Undo last connection |
| Click **Auto-Weave** toggle | Enable / disable auto drawing |
| Click **Clear Lines** | Remove all connections |
| Click **Reset Camera** | Return to default view |
| Click **Show Atlas** | Toggle myth collection panel |
| Click **Share** | Generate / import seed code |
| Click **Start Ambient** | Initialize generative audio |

---

## Technical Architecture

All code is 100% procedural. No external images, textures, models, or assets of any kind. Every star, line, particle, myth, and nebula effect is generated algorithmically at runtime.

The single deliverable is `index.html` -- open it in any modern browser and it runs immediately.

**Stack:**
* Three.js r182 (WebGPU renderer with WebGL fallback) via CDN importmap
* Three.js addons: OrbitControls, EffectComposer, RenderPass, UnrealBloomPass
* lil-gui for all parameter controls
* Web Audio API for all sound
* localStorage for myth atlas and discovered constellation persistence

**Key techniques:**
* InstancedMesh with per-instance BufferAttributes (aPhase, aSize, aColor, aBasePos) for efficient star rendering and per-star twinkling
* Simplex noise (inline Gustavson implementation) for gentle star drift
* LineSegments with AdditiveBlending for neon glow lines
* InstancedMesh particle pools reused per connection for zero allocation trails
* Connection graph (Map of starIndex to Set) for efficient BFS loop detection
* Pairwise distance set matching for real constellation recognition (rotation invariant)
* FBM noise shader on BackSide sphere for nebula depth

---

## GUI Panels

**Agents**
* Star Count -- adjust star density live (800 to 2500)
* Auto-Weave -- toggle automatic constellation drawing
* Clear Lines -- erase all connections

**Visuals**
* Bloom Strength -- tune neon glow intensity (0.5 to 3.0)
* Ambient Vol -- master volume for generative audio (0.0 to 1.0)

**Top-level buttons**
* Reset Camera
* Show Atlas
* Share
* Start Ambient

---

## Myth Atlas

The Atlas panel slides in from the top-left. It collects every myth you have unlocked, both procedural and real astronomical discoveries. Real constellations are prefixed with a star symbol for distinction.

The Atlas persists in localStorage. Your discoveries survive browser restarts and system reboots.

---

## Shareable Art

Every constellation you build is a unique piece of generative cosmic art. Use the **Share** button to generate a seed code encoding all your connections. Share the code alongside a screenshot and the myth text to recreate the exact same constellation anywhere in the world.

The seed code is compact, URL-safe, and survives across different star field generations through nearest-star tolerance matching.

---

*Constellation Weaver is a single HTML file built with Three.js. Open it, breathe, and draw the sky.*
