# MP5 — Pillar Narrative Worksheet (the spine)

> Fill this before building slides so the deck has one spine. Solo submission.

## One-sentence story
"I designed a MiniClaw gripper around a crank-rocker four-bar tuned for force
efficiency, drove it with a 12:1 synchronized gear train, and verified the kinematics
three independent ways — while learning to audit the AI's output against the constraint
it quietly skipped."

## The five pillars, one beat each

| Pillar | The beat (MP1 → MP5) |
|--------|----------------------|
| **Goal & Direction** | Scaled the BigClaw's 0–86 mm down to a ~40 mm MiniClaw target; chose force efficiency (μ near 90°) as the design driver, not just stroke. |
| **Context Management** | Carried the MP1 envelope (92×46×55) and stroke spec through every analysis; the AI was never flying blind on constraints. |
| **Tools & Integration** | Right tool per job — Python closed-form for the floor, sim sweep for motion, AI for synthesis, an interactive browser sim for the live demo, MCP call live. |
| **Centaur Engineering** | Directed the AI, caught its stroke-only optimization, redirected with a μ penalty. Judgment in evidence, not just prompting. |
| **Evaluation & Trust** | Triangulated hand calc + sim + AI to <0.1 mm; honest per-subsystem trust ledger of what's verified vs. what gates a print. |

## The wrong-AI moment (required)
The AI's first parameter sweep returned a linkage (34/14/30/18) that hit the 40 mm jaw
target but let the transmission angle drop to ~58° near full open. It passed a naive
"in the 40–140° band?" check, so it looked acceptable. I caught that it had optimized
stroke in isolation and ignored force-transmission margin, forced a re-run with a μ
penalty, and converged on 32/10/32/20 — μ 81.5–105.3°. **Lesson: the AI will hand you
something that satisfies the letter of the spec while missing the intent; knowing the
real acceptance criteria is the engineer's job.**

## The honest cut (portfolio credibility)
Kept the jaw target at 40 mm and chose the force-efficient linkage over a higher-stroke
one — a deliberate trade of maximum opening for uniform output force and singularity margin.

## What I'm choosing to demonstrate
Interactive browser simulator of the full open→close cycle (primary) — drag-slider, both
jaws mirrored, live transmission-angle and jaw-opening readouts, computing the same verified
closed-form physics. Screen recording + analysis GIF as fallback, plus one live MCP/tool call
on a real design question.
