# MP5 — Slide Outline (content for slides.pdf)

~13 slides, 15 min. Each slide = one idea. Speaker notes in italics.

**1 — Title.** MiniClaw Gripper: Design, Verification, and What I Learned to Distrust.
Name, course, date. *One line: "A force-efficient four-bar gripper, verified three ways."*

**2 — The brief (Goal & Direction).** Scale BigClaw (0–86 mm) → MiniClaw (~40 mm jaw), fit
46×55 mm half-envelope. *Design driver I chose: force efficiency (μ near 90°), not just stroke.*

**3 — The design.** Grashof crank-rocker, 32/10/32/20 + 38 mm finger, mirrored. Show
`plot1_trajectory.png`. *One side designed; other mirrors; total jaw = 2× single side.*

**4 — Position analysis.** Show `plot2_displacement.png`. 0 → 41.9 mm total jaw, monotonic.

**5 — Transmission angle.** Show `plot3_transmission.png`. 81.5°–105.3°, never leaves the band.
*This is the slide that explains why I picked this geometry.*

**6 — Interference & motion.** Play the motion GIF; 5.18 mm link clearance, 2.02 mm wall margin.

**7 — Triangulation (Evaluation & Trust).** Hand calc + sim + AI agree to <0.1 mm.
*If they'd disagreed, I trust the hand calc — closed form is exact.*

**8 — THE WRONG-AI MOMENT.** First AI sweep: 40 mm jaw BUT μ → 58° near open. Passed the
naive band check; failed the intent. I caught it, added a μ penalty, re-ran → 32/10/32/20.
*Tell it directly. This is the highest-value slide in the deck.*

**9 — Drive train (Tools & Integration).** Compound spur, N=12:1, 1:1 sync, coupling check
passes. Stick-diagram sketch. *Reduction keeps μ in band — that's the one-line check that matters.*

**10 — DFM reality.** Honest flags: m=1.0 teeth, 27 parts vs <15 target, tight 2 mm margin.
*The honest cut earns more than a polished pretend.*

**11 — Final trust ledger.** Two columns: verified vs. what gates a print. *I can tell you
exactly what I trust and exactly what I don't.*

**12 — LIVE DEMO.** Interactive browser simulator (drag-slider, mirrored jaws, live μ + jaw
readouts) + one live MCP/tool call on a real question. (Screen recording + GIF fallback ready.)

**13 — The durable lesson.** The tools will be replaced; the skill that transfers is knowing
what a "good" answer has to satisfy and auditing the AI against the constraint it skipped.
*Close on the wrong-AI lesson — it's the thing the room learns most from.*
