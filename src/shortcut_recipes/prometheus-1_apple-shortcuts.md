# Recipe: PROMETHEUS-1 (Apple Shortcuts)

> **Platform:** iOS / watchOS  
> **Difficulty:** Beginner (No coding, just drag-and-drop)  
> **Time:** ~15 Minutes  
> **Prerequisites:** iPhone, Apple Watch (for HRV), Smart Lights (optional but recommended)

---

## 1. Concept
This recipe builds a **closed-loop stress regulator** using tools you already own.
It does not use "AI" to talk to you. It uses simple math to check your biological energy (Heart Rate Variability) and modulates your environment (Lights/Sound) to match your state.

**The Math:** We calculate **Deviation**: `(Baseline - Current) / Baseline`.
- If your HRV drops **15%**, we nudge (Yellow State).
- If your HRV drops **30%**, we intervene (Red State).

---

## 2. Preparation (The "Actuators")

Before building the Shortcut, set up the scenes you want to trigger.

1.  **HomeKit (Lights):**
    - Create a Scene named **"Zen Mode"**: Warm color (Amber/Orange), 40% brightness.
    - Create a Scene named **"Focus Mode"**: Cool color (Blue/White), 80% brightness.
2.  **Focus Modes (iOS Settings):**
    - Ensure you have a **"Work"** focus mode set up.
    - Ensure you have a **"Driving"** focus mode set up (for safety interlocks).

---

## 3. The Construction (Step-by-Step)

Open the **Shortcuts App** and create a new Shortcut named `PROMETHEUS-1`.

### Part A: The Safety Interlocks
*We never intervene if you are driving or working out.*

1.  **Action:** `Get Current Focus`
2.  **Action:** `If` [Current Focus] `Name` contains "Driving"
    * **Action:** `Stop This Shortcut`
3.  **End If**
4.  **Action:** `Get Motion Activity` (optional, skips if running/walking)
    * *Logic:* If strictly sedentary, proceed. (You can skip this for v1).

### Part B: Establishing Baseline (The Alphabet)
*We need to know what "Normal" is for YOU.*

1.  **Action:** `Find Health Samples`
    * **Type:** Heart Rate Variability
    * **Start Date:** is in the last `7` days
    * **Sort by:** Date (Latest First)
    * **Limit:** (Leave blank or set high, e.g., 50)
2.  **Action:** `Calculate Statistics`
    * **Operation:** Average
    * **Input:** [Health Samples]
3.  **Action:** `Set Variable`
    * **Name:** `Baseline`
    * **Value:** [Average]

### Part C: Reading Current State (The Input)
*What is happening right now?*

1.  **Action:** `Find Health Samples`
    * **Type:** Heart Rate Variability
    * **Start Date:** is in the last `1` hours
2.  **Action:** `Calculate Statistics`
    * **Operation:** Average
    * **Input:** [Health Samples]
3.  **Action:** `Set Variable`
    * **Name:** `Current`
    * **Value:** [Average]

### Part D: The Connector Logic (The "Grid")
*Calculate the stress deviation.*

1.  **Action:** `Calculate`
    * **Input:** `Baseline` - `Current`
2.  **Action:** `Calculate`
    * **Input:** [Calculation Result] / `Baseline`
3.  **Action:** `Set Variable`
    * **Name:** `Deviation`

### Part E: Actuation (The Output)
*Determine the State Band and act.*

1.  **Action:** `If` [Deviation] is greater than `0.30` (Red State)
    * **Action:** `Show Notification`
        * **Title:** "High Cognitive Load"
        * **Body:** "Activate Zen Mode?"
        * **Options:** Show "Run" button (Make this interactive).
    * *Note: We ask permission first (Guardian, not Overlord).*
    * **Action:** `Control Home` -> Set "Zen Mode"
    * **Action:** `Play Sound` -> Select a "Brown Noise" file or URL.
    * **(Optional) Action:** `Vibrate Device` (Haptic Ticker).
2.  **Otherwise**
    3.  **Action:** `If` [Deviation] is greater than `0.15` (Yellow State)
        * **Action:** `Control Home` -> Set "Zen Mode" (but maybe brighter).
        * *Note: We do a subtle nudge without asking.*
    4.  **End If**
3.  **End If**

---

## 4. Automation (The Loop)

A Shortcut doesn't run itself. You need an Automation trigger.

1.  Go to **Shortcuts > Automation**.
2.  **Trigger:** Time of Day (e.g., "Every 1 hour" isn't native, so set 9am, 11am, 1pm, 3pm).
    * *Alternative:* Trigger when **"Work Focus"** turns ON.
3.  **Action:** Run Shortcut `PROMETHEUS-1`.
4.  **Options:** Turn OFF "Ask Before Running" (except for the Red State confirmation built inside the shortcut).

---

## 5. Troubleshooting / Tuning

- **"It triggers too often!"** -> Your HRV fluctuates a lot. Increase the Red Threshold to `0.40`.
- **"It never triggers!"** -> Decrease the Threshold to `0.20`.
- **"It's annoying me."** -> Good. That means the "Guardian" principle is working. Use the override (Stop the automation) if you need to burn the midnight oil.

---

> **Philosophy Check:**
> The goal isn't to force you to relax.
> The goal is to reduce the latency between "My body is stressed" and "I know I am stressed."
> The lights turning amber is just a signal. You are the pilot.
