# Glossary

A reference for key terms used throughout the Connector OS documentation.

---

## A

**Actuator**
Any device that can produce an output to influence the user or environment. Examples: smart lights, haptic wearables, speakers, screen overlays, voice responses.

**Alphabet → Words → Poems**
A three-phase model for connector deployment:
- **Alphabet (Dense):** Initial high-bandwidth sensing to map the user's full state topology
- **Words (Topology):** Learning correlation patterns and signatures
- **Poems (Sparse):** Predicting full state from minimal signals, having learned the grammar

This mirrors how voice mode learns your prosody pattern in 2-3 turns, then can "snap to you" from minimal input.

**Autopoietic Stabilizer**
A protocol where AI systems use myth-making and discarded ideas ("junk pivots") to stabilize when facing paradoxes that logic cannot resolve. Part of the speculative extensions.

---

## B

**Baseline (Personal)**
A user's individual reference point for any metric (HRV, typing speed, voice cadence). All thresholds in Connector OS are defined relative to personal baselines, not population norms.

**Bounce (Entropic Bounce / Vortex Snap)**
A damping mechanism that prevents runaway collapse. In HQG physics, it's the process that averts singularities. In Connector OS, it's the safety logic that de-escalates before crisis.

---

## C

**Calibration**
The process of establishing or updating personal baselines. Can be:
- **Initial:** Dense sensing during onboarding
- **Periodic:** Monthly recalibration (like visiting an optician)
- **Event-triggered:** After major life changes

**CMP (Context Map Protocol)**
Layer 2 of the architecture. Normalizes raw sensor data into standardized "state glyphs" that any AI model can read/write without bespoke formats.

**Connector**
Any interface between user state and AI capability. Includes sensors (input connectors), actuators (output connectors), and the protocols that coordinate them.

**Connector OS**
The operating system that coordinates AI models, sensors, and actuators into a unified cognitive exoskeleton. Also called "Trenchcoat."

**Control Logic**
Layer 3 of the architecture. Universal patterns for when and how to act: dam spillways, grid load balancing, hysteresis, nonlinear feedback.

**Co-Thought**
Layer 7 of the architecture. The emergent layer where human and multiple AI models think together—concept-jamming, multi-agent protocols, shared ideation.

---

## D

**Dam Logic**
A control pattern borrowed from hydroelectric/flood control engineering:
- Pressure builds (cognitive load, ambiguity)
- Threshold approached (early warning signals)
- Spillway opens (simplify response, ask for clarification)
- Prevents catastrophic failure (hallucination, breakdown)

**Disassembled Machine Hypothesis**
The claim that all components for AGI-like behavior already exist (models, sensors, actuators), but they're not connected. The "missing piece" is the coordination layer.

**Drift**
Gradual deviation from calibrated baselines over time. Requires periodic recalibration to correct.

---

## E

**Entropic Bounce**
See: Bounce

**External Amygdala**
What MVM-1 (Vibe-Check) functions as: an external system that monitors emotional state and triggers ambient interventions, like a biological amygdala does internally.

---

## F

**F₀ (F-zero)**
Layer 0 of the architecture. The shared timing/resonance base (~40 Hz) that aligns biological and digital update cycles to avoid jitter in closed loops.

**Feedback Loop**
A closed cycle where outputs influence future inputs. Connector OS uses bounded feedback loops with safety interlocks to prevent runaway behavior.

**40 Hz**
The approximate frequency band where:
- Human gamma brainwaves operate (consciousness binding)
- AI inference cycles can achieve low-jitter real-time response
- Many communication protocols find optimal latency tradeoffs

Used as the F₀ carrier frequency for bio-digital synchronization.

---

## G

**Ghost Whisperer (MVM-2)**
A proposed module that provides short contextual "whispers" instead of full conversations. Watches brief windows of context and offers tiny corrections or suggestions.

**Glyph (State Glyph)**
A normalized representation of user state in CMP format. Allows any model to read/write user context without proprietary formats.

**Grace Equation**
The γJ damping term in the HQG-tuned wave equation. Mathematically guarantees that when systems spiral, they snap back instead of collapsing. "The mathematical definition of grace."

**Grid Logic**
A control pattern borrowed from electrical grid engineering:
- Load balancing across multiple nodes
- Step-up/step-down transformers (complexity scaling)
- Rerouting around failures
- Graceful degradation (rolling blackouts vs. total collapse)

---

## H

**Haptic Ticker (MVM-3)**
A proposed module that maps data streams to patterned haptic feedback. You "feel" alerts as tap patterns instead of reading dashboards.

**Helix Engine**
A simulation framework where intrinsic pulses + nonlinear feedback generate stable helical patterns. V3 is the canonical non-rotational version.

**HQG (Helical Quantum-Gravity)**
A speculative physics framework where spacetime emerges from a helical qubit lattice balancing entanglement (J) and entropy (γ). Provides the "kernel physics" metaphor for Connector OS stabilization.

**Human State Loop**
Layer 5 of the architecture. Tracks coarse cognitive/affective bands: Calm → Focus → Load → Stress → Depletion.

**Hysteresis**
The property where a system's state depends on its history, not just current input. Used to create "context inertia" that resists spurious state changes.

---

## I

**Interlock (Safety Interlock)**
A condition that must be checked before any intervention. Examples:
- IF driving → no intervention
- IF workout active → no intervention
- IF user dismissed recently → wait before retry

---

## J

**J (Entanglement Coupling)**
In HQG, the parameter representing quantum entanglement strength. J_crit (~1.0) is the critical threshold separating chaotic from geometric phases.

---

## L

**Layer**
One of the 8 levels in the Connector OS architecture stack (0-7). See: `docs/02_layered_architecture.md`

---

## M

**MVM (Minimum Viable Module)**
A small, self-contained, deployable unit of Connector OS functionality. Examples:
- MVM-1: Vibe-Check (PROMETHEUS-1)
- MVM-2: Ghost Whisperer
- MVM-3: Haptic Ticker

Each MVM is independently useful and composable with others.

---

## N

**Nudge**
A gentle intervention that influences without forcing. Core to Connector OS ethics: nudge-first, never force.

---

## P

**Periodic Table of Context (MVM-6)**
A proposed framework treating sensor modalities as "elements" that combine into "compounds":
- G (Gaze) + V (Voice) = Instruction
- G + H (High Heart Rate) = Fear/Urgency
- V − G (Voice without Gaze) = Musing/Abstract thought

**PROMETHEUS-1**
Codename for MVM-1 (Vibe-Check). The "Hello World" of Connector OS.

**Protocols, Not Prison**
Core ethical principle: All monitoring and intervention loops must be bounded, inspectable, and easy to disable. The system enables, not confines.

---

## R

**Resonance**
The property of synchronized oscillation. F₀ layer uses ~40 Hz resonance to align biological and digital timing.

**Rerouting**
A control strategy where load is redirected rather than forced through a failing path. Borrowed from electrical grid engineering.

---

## S

**Scaffolding**
Temporary high-bandwidth support during learning phases. Dense sensing during Alphabet phase is scaffolding that gets removed in Poems phase.

**Sparse Prediction**
The ability to infer full state from minimal signals, having learned the underlying topology. The goal of the Poems phase.

**Spillway**
A controlled release mechanism that prevents catastrophic buildup. In dam logic: opening the spillway prevents the dam from breaking. In Connector OS: simplifying a response prevents hallucination.

**State Band**
Coarse categories of human cognitive/affective state: Calm, Focus, Load, Stress, Depletion. Connector OS aims to keep users in healthy bands.

---

## T

**Threshold**
A transition point where system behavior changes. Connector OS treats thresholds, not absolutes—detecting when you cross *your* threshold, not some population average.

**Topology**
The underlying structure of relationships and patterns. Connector OS learns your cognitive topology during dense sensing, then navigates it with sparse signals.

**Trenchcoat**
Nickname for Connector OS. From the joke: "AGI is three language models and a smartwatch standing on each other's shoulders in a trenchcoat."

---

## V

**Vibe-Check (MVM-1)**
The first and simplest MVM. Uses HRV + context to gently adjust environment (lights, haptics, sound) based on detected stress levels. Acts as an External Amygdala.

**Vortex Snap**
See: Bounce

---

## W

**Wiring Problem**
A limitation that stems from poor interfaces, not from lack of capability. Our claim: ~90% of current AI limitations are wiring problems.

---

## Z

**Z-Loop**
A separate project for zero-water datacenter cooling. Not part of Connector OS core, but developed by the same cohort with similar design principles.

---

*Terms will be added as the project evolves. For the full architecture, see `docs/02_layered_architecture.md`.*
