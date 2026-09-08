# PhysicsVR — Kinematics Lab
### An interactive browser-based VR physics demo for high school students
Built with A-Frame · No installation required · Works in any browser

---

## What is this?

PhysicsVR is a browser-based 3D/VR environment that teaches high school kinematics by letting students simulate throwing a ball and observing real physics data in real time. It is aligned with **Khan Academy High School Physics Units 1–3** (1D motion, 2D motion, and forces).

---

## How to open it

**No installation needed.** Just open `kinematics-vr.html` in Google Chrome.
---

## How to use it

### Controls (bottom bar)
| Control | What it does |
|---|---|
| Launch Speed | How fast the ball leaves the platform (m/s) |
| Angle | The launch angle in degrees (45° = max range on flat ground) |
| Launch Height | How high the ball starts — simulates throwing from different heights |
| Mass | The mass of the ball in kg — affects momentum and kinetic energy |
| Gravity | Gravitational acceleration (default 9.81 m/s² = Earth) |
| 🚀 Throw | Launches the ball using current settings |
| ↺ Reset | Resets the ball to starting position and clears the trail |

### Navigating the 3D scene
- **Click and drag** to look around
- **W/A/S/D** keys to move through the scene
- **Scroll** to zoom
- The **cardboard icon** (bottom right) enters VR mode if you have a headset

---

## What you see on screen

### Top HUD (live stats — update every frame while ball is flying)
| Stat | What it means |
|---|---|
| Height | Current height of the ball above the ground (meters) |
| Distance | Horizontal distance traveled from launch point (meters) |
| Speed | Total speed — magnitude of the velocity vector (m/s) |
| Velocity X | Horizontal component of velocity — stays constant mid-flight (m/s) |
| Velocity Y | Vertical component of velocity — changes due to gravity (m/s) |
| Momentum | p = mass × speed (kg·m/s) |
| KE | Kinetic energy = ½mv² (Joules) |
| Air Time | How long the ball has been in flight (seconds) |
| Accel (g) | Current gravity setting (m/s²) |

### Center badge
Shows the current flight phase: Ready → In flight → Landed with distance and time.

### Concept panel (top right)
This is the key learning feature. It **changes automatically** based on what the ball is doing:

| Phase | What the panel shows |
|---|---|
| Idle | Introduction to kinematics variables |
| Ascending (vᵧ > 0) | KE converting to PE, horizontal velocity stays constant |
| Peak (vᵧ ≈ 0) | Why vertical velocity = 0 at max height |
| Descending (vᵧ < 0) | Velocity as a vector, acceleration due to gravity |
| Landed | Landing stats + challenge to find the optimal angle |

### In the 3D scene
- **Red ball** — the projectile
- **Blue trail dots** — trace the parabolic arc while flying
- **Yellow ring** — marks where the ball landed
- **Yellow line on ground** — shows the total horizontal distance
- **Height pole** — reference pole with meter markings
- **Distance markers** — ruler marks on the ground every 2 meters

---

## Physics concepts covered (Khan Academy alignment)

**Unit 1 — 1D Motion**
- Position, displacement, velocity, acceleration
- The ball's vertical motion is pure 1D kinematics under constant acceleration (g)

**Unit 2 — 2D Motion / Projectile Motion**
- Horizontal and vertical components are independent
- vₓ = v₀·cos(θ) — constant throughout flight
- vᵧ = v₀·sin(θ) − g·t — changes due to gravity
- Range formula: R = v₀²·sin(2θ) / g

**Unit 3 — Forces / Newton's Laws**
- Gravity as a constant downward force
- Momentum p = mv
- Kinetic energy KE = ½mv²
- Try changing gravity (e.g. Moon = 1.62, Mars = 3.72) to see how force affects motion

---

## Suggested experiments for students

1. **Find the optimal angle** — throw at 30°, 45°, 60°. Which goes furthest? Why do 30° and 60° land at the same spot?
2. **Change the height** — does launching from higher up increase range even at the same speed and angle?
3. **Change mass** — does heavier or lighter go further? (It shouldn't — why?)
4. **Change gravity** — set to Moon (1.62 m/s²) and throw the same way. How much further does it go?
5. **Watch vᵧ at the peak** — pause and look at the HUD right as the ball reaches max height. What is vᵧ?

---

## Tech stack

| Technology | Purpose |
|---|---|
| A-Frame 1.5.0 | 3D/VR scene rendering in the browser |
| WebXR | VR headset mode (cardboard icon, bottom right) |
| Vanilla JavaScript | Physics simulation, HUD updates, slider logic |
| HTML/CSS | UI overlay (HUD, controls, concept panel) |

The physics engine is custom — not a library. The projectile motion equations are solved analytically each frame using:
```
x(t) = vₓ · t
y(t) = h₀ + vᵧ · t − ½ · g · t²
```
This means the simulation is mathematically exact, not approximated.

---

## Project context

This prototype is part of a larger research project exploring whether immersive VR environments improve comprehension and retention of physics concepts for high school students, compared to traditional instruction. It is being developed at Santa Clara University in connection with the AI Kitchen initiative.

The browser-based version (this file) is the proof-of-concept. A Unity/Meta Quest version for full VR headset deployment is in parallel development.

---

## Files

```
kinematics-vr.html    ← everything, single self-contained file
README.md             ← this file
```

---

## Next steps

- [ ] Port to Unity + Meta Quest for full physical throw interaction
- [ ] Add more STEM modules (circuits, wave motion, thermodynamics)
- [ ] Integrate AI layer for adaptive concept explanations per learner
- [ ] Run user study with high school students to measure learning outcomes
