# MP4 Part B — Centaur Log (solo)


**Loop 1 — Linkage selection.** Asked the AI to put my chosen four-bar against the two
variants I'd sketched, on the same axes (stroke, μ, bbox). It tabulated them; I cut the
34/14/30/18 variant for the 58° μ-dip near open and the 32/10/32/16 variant for lower
μ-margin. Kept the original.

**Loop 2 — Drive-train architecture.** Asked which architecture fits 2–3 thumb turns to
a 75° sweep with two synced sides. Considered worm vs compound spur; chose compound spur
+ 1:1 sync because it prints cleaner and self-locking isn't needed for a hand-driven wheel.

**Loop 3 — Reduction sizing.** Asked the AI to size stages to N=12. It proposed 4:1 then
3:1 (12/48, 16/48). I checked the center distances (30/32 mm) against the housing footprint
and accepted them.

**Loop 4 — Coupling check (asked the AI to find my blind spot).** Instead of asking it to
design, I asked "what am I missing in assuming the reduction doesn't affect the linkage?"
It confirmed N only maps thumb turns to the same 75° sweep, so μ stays 81.5–105.3° — and
flagged that the 2-turn/3-turn extremes widen the sweep, which I then checked stays in band.

**Loop 5 — Trust-assessment review.** Asked the AI to review my per-subsystem table for a
hidden assumption. It caught that I'd marked the housing "ready" on envelope fit alone while
the 2 mm margin hadn't been checked in 3D — I downgraded housing to "No" and added the
3D stack-up as a known unknown.

*(Transcript screenshots committed under `evidence/`.)*
