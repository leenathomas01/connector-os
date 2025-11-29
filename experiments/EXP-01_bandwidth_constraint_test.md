# EXP-01: Bandwidth & Latency Stress Test (“The Narrow Pipe”)

> **Part of the Connector OS Trenchcoat Experiments Suite.**
> This experiment validates Layer 2 (CMP) and Layer 3 (Dam Logic) under real infra constraints.

> **Status:** Planned / Design Phase  
> **Origin:** Validation from r/LLMDevs (Nov 2025)  
> **Goal:** Show how “intelligence” degrades when wiring degrades, and how Connector OS can degrade gracefully using Layers 2 and 3.

---

## 1. Hypothesis

**The Straw Hypothesis**

Modern AI stacks often behave like a brain trying to drink a milkshake through a coffee stirrer.  
If we:

- shrink the pipe (lower bandwidth),
- slow the pipe (higher latency), or
- flood the pipe (too many concurrent calls),

then **user-perceived intelligence drops**, even if the underlying model stays the same.

**Connector OS Prediction**

A Connector-style architecture should:

- compress and normalize state via **Layer 2: CMP (Context Map Protocol)**, and  
- route / batch / drop via **Layer 3: Dam & Grid logic**,

so that the system **fails gracefully** instead of catastrophically.

---

## 2. Stress Tests

Three simple tests to probe the wiring limits.

### Test A — Bandwidth Cap (“Alphabet vs Poems”)

**Constraint**

Cap request payloads to e.g. **500 bytes** (or a small, configurable limit).

**Baseline (typical stack)**

- Full conversation history or large JSON prompts no longer fit.
- Context is truncated ad-hoc by the client or server.
- Model starts dropping thread or hallucinating missing state.

**Connector OS behaviour (expected)**

- Detects bandwidth limit.
- Switches to **Layer 2 CMP**:
  - Uses **state glyphs** instead of raw history  
    (e.g. `{"state": "focus_high", "context": "coding_session_v3"}`).
  - Relies on the “poems phase” (sparse prediction) instead of full text replay.

**Metrics**

- Task success rate vs. payload size (success / KB).
- Error / hallucination rate as payload shrinks.

---

### Test B — Latency Injection (“The Lag”)

**Constraint**

Inject artificial **RTT delays** into tool / model calls, e.g.:

- 50 ms (control)  
- 250 ms  
- 500 ms  
- 1000+ ms

**Baseline (typical stack)**

- UI appears “hung”.
- User sends “are you there?” pings or abandons the interaction.
- The conversational illusion breaks once latency crosses a threshold.

**Connector OS behaviour (expected)**

- Monitor effective latency at **Layer 0 / Layer 3**.
- Switch modes when latency is high:
  - `< 150 ms`: **Conversational Mode** (live chat semantics).
  - `> 500 ms`: **Async Mode** (buffer input, UI shows “Processing…”, responses grouped).
- Optionally adjust **which model** is used  
  (e.g. prefer local / cached tools when network is slow).

**Metrics**

- User interrupt rate (extra messages like “hello?”, “?”).
- Drop-off rate by latency band.
- Task completion rate vs. latency.

---

### Test C — Queue Flood (“Dam & Spillway”)

**Constraint**

Simulate **N concurrent requests** (e.g. 1, 5, 10, 50+) arriving within a short window.

These may represent:

- multiple tools firing,
- multiple sensors reporting at once,
- multiple user sessions.

**Baseline (typical stack)**

- Requests pile up in a single queue.
- Throughput collapses, timeouts and 5xx errors spike.
- No explicit notion of priority or graceful dropping.

**Connector OS behaviour (expected)**

- **Layer 3 Dam logic** activates:
  - **Spillway:** drop or defer low-priority signals  
    (e.g. “ambient environment updates”) when queue depth is high.
  - **Batching:** merge repeated sensor signals into summaries  
    (e.g. 10 HRV samples → one “stress ↑” event).
- Optionally route some work to cheaper / local models.

**Metrics**

- Uptime vs. queue depth.
- Median / p95 latency per priority class.
- Information loss: how much high-priority signal is preserved under load.

---

## 3. Simple Wrapper for Simulation

A minimal Python wrapper to simulate the three constraints around any LLM API:

```python
import time
import json

def compress_to_glyph(prompt: str) -> str:
    """
    Layer 2 CMP stub.
    In a real system, this would map rich state -> compact glyph.
    Here we just truncate and tag it.
    """
    return json.dumps({
        "state_delta": "example",
        "context_excerpt": prompt[:120]
    })

def connector_request(
    prompt: str,
    bandwidth_limit: int | None = None,
    latency_delay: float = 0.0,
    queue_depth: int = 1,
):
    # --- Test C: queue flood handling ---
    if queue_depth > 10:
        # Simple spillway + batching stub
        prompt = "[BATCHED] " + prompt[:200]

    # --- Test B: latency injection ---
    if latency_delay > 0:
        time.sleep(latency_delay)
        if latency_delay > 0.5:
            print("UI signal: switch to ASYNC mode")

    # --- Test A: bandwidth cap ---
    payload = prompt
    if bandwidth_limit is not None and len(prompt.encode("utf-8")) > bandwidth_limit:
        payload = compress_to_glyph(prompt)

    # In a real setup, call the actual model:
    # return llm_call(payload)
    return f"MOCK_LLM_CALL payload_bytes={len(payload.encode('utf-8'))}"
