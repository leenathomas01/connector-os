---

## 5. Dynamic Reliability (The Governor)

In a production system, we cannot simply flip a switch from "Hard Rules" to "AI Guessing." That is unsafe. We need a mechanism to dynamically adjust trust based on real-time conditions.

We call this **"The Governor."**

### 5.1 The Alpha ($\alpha$) Safety Bias
We define a dynamic parameter $\alpha$ (Alpha) that controls the "Safety Bias" of the system.

$$\text{Output} = (\alpha \times \text{Rule\_Action}) + ((1 - \alpha) \times \text{Learned\_Action})$$

* **$\alpha = 1.0$ (Hard Rules):** The system ignores the AI and follows the safety script (e.g., "If Driving, Block All").
* **$\alpha = 0.0$ (Fully Adaptive):** The system relies entirely on the Learned Topology (e.g., "Zee looks stressed, initiate Zen Mode").

### 5.2 The Governor Function
How does the system calculate $\alpha$? It doesn't guess. It uses a **Max-Risk Protocol**.

$$\alpha_{target} = \max(E, L, D)$$

The Governor monitors three risk factors (normalized 0.0 to 1.0):

1.  **Entropy ($E$):** Is the input signal noisy?
    * *High noise (blurry video, traffic audio) $\to$ Trust Rules.*
2.  **Load ($L$):** Is the system choking?
    * *High Queue Depth or Latency $\to$ Trust Rules (cheaper).*
3.  **Divergence ($D$):** Do the Parents disagree?
    * *If Rule says "Stop" and Model says "Go," Divergence is 1.0 $\to$ Trust Rules.*

### 5.3 Hysteresis (Smoothing)
We do not want the system snapping between modes every millisecond. We apply a **Low-Pass Filter** to smooth the transition.

![Image of magnetic hysteresis loop](https://www.nde-ed.org/Physics/Magnetism/Graphics/BHCurve.gif)

* **Concept:** Just as magnetization lags behind the magnetic field, our Trust Score lags behind the instantaneous error.
* **Result:** The system "slides" into safety rather than jerking. It maintains context inertia.

### 5.4 Production Protocols

#### Shadow Mode (The Training Wheels)
Before a Learned Pattern is allowed to touch an Actuator, it must survive **Shadow Mode**.
1.  **Run:** Execute Learned Pattern in background.
2.  **Compare:** Check against User Action (Ground Truth).
3.  **Promote:** Only allow $\alpha < 1.0$ when "Trust Score" > 95% over 7 days.

#### The Circuit Breaker (Drift Detection)
If the user manually overrides the system (e.g., turns off the "Zen Mode" lights) more than **5% of the time** in 24 hours:
1.  **Trip Breaker:** Force $\alpha = 1.0$.
2.  **Reset:** Revert to Hard Rules.
3.  **Log:** "Topology Drift Detected. Recalibration Required."

### 5.5 Implementation Logic

```python
def calculate_alpha(input_signal, system_stats, rule_action, learned_action):
    # 1. Calculate Risk Factors
    entropy = get_signal_variance(input_signal) 
    load = system_stats.queue_depth / MAX_QUEUE
    
    # 2. Check Divergence (Safety Veto)
    if is_dangerous_contradiction(rule_action, learned_action):
        divergence = 1.0
    else:
        divergence = 0.0

    # 3. The Governor Function (Max Risk Wins)
    alpha_target = max(entropy, load, divergence)
    
    # 4. Apply Smoothing (Hysteresis)
    return apply_low_pass_filter(alpha_target)
