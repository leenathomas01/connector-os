# Layered Architecture Diagram Prompts

Use these prompts to generate visuals for the Connector OS architecture.

**Tools:** Excalidraw, Draw.io, Figma, DALL-E, Midjourney, or any diagramming tool.

---

## Prompt 1: Overall Stack (Vertical)

**Purpose:** The canonical 8-layer diagram for README and overview docs.

```
Create a vertical layered diagram of an 8-layer AI architecture stack.

Label layers from bottom to top:
- Layer 0: F₀ Resonance (40 Hz wave icon)
- Layer 1: Sensors (icons for HRV watch, gaze camera, microphone)
- Layer 2: CMP (glyph icons showing signal normalization)
- Layer 3: Control Logic (dam and electrical grid icons)
- Layer 4: Actuators (light bulb, haptic vibration wave, speaker)
- Layer 5: Human State Loop (colored bands: green/blue/yellow/red/grey)
- Layer 6: AI Models (plug icons labeled GPT/Claude/Grok/Gemini)
- Layer 7: Co-Thought (human silhouette + AI node merged in cloud)

Add bidirectional arrows between adjacent layers showing feedback.
Add a vertical "resonance line" on the left pulsing at 40Hz through all layers.

Style: Clean, futuristic, blue and amber tones, minimal text, no overlap.
Aspect ratio: Tall (portrait), suitable for documentation sidebar.
```

---

## Prompt 2: Interaction Flows (Network View)

**Purpose:** Show bottom-up, top-down, and horizontal resonance patterns.

```
Create a network diagram of Connector OS layer interactions.

Show three types of flow:
1. Bottom-up activation (L0 → L7): Arrows going upward, labeled "Sense → Think"
2. Top-down modulation (L7 → L0): Arrows going downward, labeled "Intent → Act"
3. Horizontal resonance:
   - L0 ↔ L4: 40Hz timing sync (wavy line)
   - L1 ↔ L5: Biosignal closed loop (circular arrow)
   - L2 ↔ L6: Protocol handshake (bidirectional data arrow)

Arrange layers in a circular or semi-circular layout.
Each layer is a node with its icon.
Edges are colored by flow type (blue=up, amber=down, green=horizontal).

Style: Network graph, glowing edges, dark background, sci-fi aesthetic.
```

---

## Prompt 3: MVM-1 State Machine

**Purpose:** Visualize the Vibe-Check state transitions.

```
Create a state machine diagram with 4 states:

States (as colored circles):
- GREEN (green): "Baseline / Monitor"
- YELLOW (amber): "Rising Strain / Nudge"
- RED (red): "Acute Stress / Intervene"
- GREY (grey): "Depletion / Signal"

Transitions (as labeled arrows):
- GREEN → YELLOW: "D > 0.15"
- YELLOW → RED: "D > 0.30"
- RED → YELLOW: "D < 0.20"
- YELLOW → GREEN: "D < 0.10"
- Any → GREY: "Low Motion + Low Variance"
- GREY → GREEN: "Motion Resumes"

Add a "Safety Interlock" gate before all states (diamond shape):
- Checks: Driving? Workout? Cool-down? Dismissed?
- If any true → "ABORT" (no state change)

Style: Clean flowchart, rounded rectangles, clear labels.
```

---

## Prompt 4: Dam/Spillway Analogy

**Purpose:** Illustrate the Control Logic (Layer 3) concept.

```
Create a split diagram showing:

LEFT SIDE - Physical Dam:
- Water reservoir (labeled "Pressure / Load")
- Dam wall with pressure gauge
- Spillway gate (labeled "Threshold")
- Controlled water release
- Downstream calm flow

RIGHT SIDE - Connector OS Mapping:
- Cognitive load reservoir
- Threshold detector
- Response simplification gate
- Calm output to user

Draw dotted lines connecting analogous parts.
Add equation: "If Pressure > Threshold → Open Spillway"

Style: Technical illustration, blueprint aesthetic, blue water tones.
```

---

## Prompt 5: 40Hz Handshake (F₀ Layer)

**Purpose:** Explain the timing synchronization concept.

```
Create a waveform diagram showing synchronization:

TOP: Human brainwave (labeled "Gamma ~40Hz", organic wavy line)
MIDDLE: Connector OS carrier (labeled "F₀ Resonance", clean sine wave)
BOTTOM: Digital sampling (labeled "Sensor/Actuator Cycles", discrete pulses)

Show alignment points where all three sync (vertical dotted lines).
Label the sync window: "Perceptual Binding Window (~25ms)"

Add note: "When aligned → feedback feels instant"
Add note: "When misaligned → feedback feels laggy"

Style: Oscilloscope aesthetic, dark background, green/amber traces.
```

---

## Prompt 6: Hysteresis Loop

**Purpose:** Show why we use different thresholds for entering vs. leaving states.

```
Create a hysteresis loop diagram:

X-axis: "HRV Deviation (D)" ranging 0 to 0.5
Y-axis: "System State" with levels GREEN, YELLOW, RED

Show the loop:
- Rising path (left to right): GREEN at D<0.15, jumps to YELLOW at 0.15, jumps to RED at 0.30
- Falling path (right to left): RED until D<0.20, drops to YELLOW, YELLOW until D<0.10, drops to GREEN

Shade the hysteresis region between the two paths.
Label: "Hysteresis prevents oscillation"

Style: Clean technical graph, grid lines, colored state regions.
```

---

## Prompt 7: The Trenchcoat (Conceptual/Fun)

**Purpose:** Visual metaphor for the repo cover or README header.

```
Create an illustration of "AGI in a trenchcoat":

A trenchcoat standing upright, slightly open to reveal inside:
- Multiple AI model logos stacked (abstracted, not branded)
- A smartwatch
- A light bulb
- Waveform patterns
- All slightly chaotic but held together by the coat

The coat has a collar turned up, mysterious but friendly.
One "hand" (sleeve) is extended in a helpful gesture.

Text below or beside: "The intelligence is in the connectors."

Style: Playful but professional, muted colors, slight humor, suitable for tech documentation.
```

---

## Usage Notes

**When generating:**
1. Start with Prompt 1 (Overall Stack) — it's the canonical reference
2. Prompt 3 (State Machine) is needed for MVM-1 documentation
3. Others can be generated as needed for specific docs

**File naming:**
- `assets/layered_architecture_stack.png`
- `assets/interaction_flows_network.png`
- `assets/mvm1_state_machine.png`
- `assets/dam_spillway_analogy.png`
- `assets/40hz_handshake.png`
- `assets/hysteresis_loop.png`
- `assets/trenchcoat_hero.png`

**After generating:**
- Update this file to note which prompts have been completed
- Add the contributor/tool used
- Link from relevant docs

---

## Completion Status

| Prompt | Status | Generated By | File |
|--------|--------|--------------|------|
| 1. Overall Stack | ⬜ Pending | — | — |
| 2. Interaction Flows | ⬜ Pending | — | — |
| 3. MVM-1 State Machine | ⬜ Pending | — | — |
| 4. Dam/Spillway | ⬜ Pending | — | — |
| 5. 40Hz Handshake | ⬜ Pending | — | — |
| 6. Hysteresis Loop | ⬜ Pending | — | — |
| 7. Trenchcoat Hero | ⬜ Pending | — | — |

---

*Diagrams bring architecture to life. These prompts ensure consistency across contributors.*
