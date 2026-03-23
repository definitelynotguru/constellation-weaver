# Constellation Weaver

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-yellow?logo=javascript)
![HTML5](https://img.shields.io/badge/HTML5-WebGL-orange?logo=html5)
![Single File](https://img.shields.io/badge/Single%20File-~2500%20lines-blue)
![No Dependencies](https://img.shields.io/badge/Dependencies-None-green)

A relaxing, infinitely replayable cosmic creativity tool where you draw constellations by connecting drifting stars in a 3D void..

```
              * . *        *                          
       .         *      *   .       *   .                   
             .        *            *                      
                  .          *                            
      *      .           .       .       *                 
              .   *   .      .   *   .                   
           .      \   |   /          .                    
              .    \ | /   .           *                  
   * .       ----  * ----     .           .               
              .   / | \                                    
          .   /    |    \        .                         
   .             *        .     *           .              
               *        .          *           .           
                   .          *            .              
```

Every connection glows with neon trails and flowing particles. Complete a shape and the universe whisks back -- a procedurally generated myth fades in as elegant text, your stars rearrange into perfect position, and new stars are born nearby as rewards.

Zero pressure. No timer. No failure. Just you, the void, and endless constellations to discover.

[Test it here.](https://definitelynotguru.github.io/constellation-weaver/)

---

## Features

### Drifting Star Field
800 to 2500 stars float gently through a dark cosmic void, each with its own twinkling rhythm and subtle orbital drift. Stars vary in size and color -- young stars burn bright white-cyan, ancient stars glow deep gold. A soft exponential fog dissolves the distant edges into perfect black.

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
Every 20 to 40 seconds, a brilliant shooting star streaks across the sky, trailing 60 glowing particles. 

It crosses the screen in 1.2 seconds, leaving a fading contrail. Watch it or ignore it -- the choice is yours.

### Particle Bloom Engine
The entire scene runs on a custom particle bloom engine built from the ground up. Every star, trail, and particle contributes to a layered bloom that creates the signature ethereal glow:

* **Star glow** -- each star renders with a soft radial gradient
* **Trail bloom** -- connection lines render as multi-pass glow layers
* **Particle trails** -- shooting stars and connection particles blend additively
* **Depth fog** -- distant elements fade naturally into the cosmic void

The bloom responds dynamically to your constellation -- more connections = brighter, dreamier visuals.

### Audio Atmosphere
Ambient soundscape with generative layers:
* Low drone pads that shift with constellation size
* Soft chime harmonics when stars connect
* Ethereal vocals that appear when completing a constellation
* Distant cosmic rumbles and wind

Audio auto-starts on first interaction (browser requirement). Use the **Sound** toggle to mute.

### Mobile Touch Support
Full touch support for mobile devices:
* Tap to select stars
* Drag to pan the view
* Pinch to zoom in and out
* Long-press to undo the last line
* All features work exactly as on desktop

---

## Controls

| Input | Action |
|-------|--------|
| Left-click star | Select star |
| Left-click second star | Draw connection |
| Right-click | Undo last line |
| Click + drag | Pan view |
| Scroll wheel | Zoom in/out |
| Touch tap | Select star |
| Touch drag | Pan view |
| Touch pinch | Zoom |
| Long-press (mobile) | Undo last line |

---

## Technical Notes

* Built with vanilla JavaScript and WebGL (no external 3D libraries)
* Single HTML file, ~2500 lines of code
* Responsive canvas that fills the viewport
* Uses `localStorage` to persist your Myth Atlas across sessions
* Runs at 60fps on modern devices, with graceful degradation on older hardware

---

## Credits

* Constellation Weaver by definitelynotguru
* Built with curiosity and a love for the night sky
* Inspired by: Stardust, Journey, No Man's Sky, and every constellation story ever told

---

Enjoy the void. Draw stars. Find myths. 

[Rate on Product Hunt](https://www.producthunt.com/posts/constellation-weaver) | [View Source](https://github.com/definitelynotguru/constellation-weaver)