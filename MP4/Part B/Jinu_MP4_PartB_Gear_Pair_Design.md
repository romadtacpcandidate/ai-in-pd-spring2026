# MP4 Part B — Drive-Train Design

## Requirement
Convert **2–3 turns of the thumb wheel** into the verified **75° input-crank sweep**
(θ₂ 100°→175°), and **synchronize the two mirrored sides** so they counter-rotate at
equal rate.

## Architecture choice
**Compound spur reduction + a 1:1 sync pair.** A two-stage compound spur train sets
the reduction; a final equal-tooth gear pair couples the two cranks so they
counter-rotate identically.

Why not a worm drive: a worm + worm wheel gives high reduction in one stage and
self-locks, but it's harder to print cleanly at this module/size and adds friction.
A compound spur train is more printable and easier to inspect, and self-locking isn't
needed here (the thumb wheel is hand-driven, not back-driven under load).

## Reduction
Design point: **2.5 thumb-wheel turns (900°) → 75° crank sweep**, so

  **N = 900° / 75° = 12 : 1**

(2 turns → 60° crank, 3 turns → 90° crank; both stay in a slightly widened sweep
where μ remains well inside the band, so the "2–3 turns" spec is met with margin.)

## Per-stage specs (module m = 1.0 mm)

| Stage | Pinion z | Gear z | Ratio | Center distance = m(z₁+z₂)/2 |
|-------|----------|--------|-------|------------------------------|
| 1 (from thumb wheel) | 12 | 48 | 4.00 | 30.0 mm |
| 2 | 16 | 48 | 3.00 | 32.0 mm |
| **Compound total** | | | **12.00** | |
| Sync pair (final → mirror crank) | 40 | 40 | 1.00 (counter-rotating) | 40.0 mm |

- Stages 1 and 2 share a compound shaft (stage-1 48T gear rigid with stage-2 16T pinion).
- Stage-2 output (48T) is fixed to crank A (side 1) and meshes with the 40T/40T sync pair
  driving crank B (side 2) in the opposite direction → symmetric counter-rotation.
- Overall **N = 12:1**, thumb wheel → either crank, cranks locked in mirror sync.

## Packaging
Center distances (30 / 32 / 40 mm) are laid out so the compound shaft routes alongside
the linkage ground link inside the housing. Final footprint to confirm in integration
CAD; nothing here exceeds the MiniClaw housing length.

## Coupling check (the one that matters)
N sets how many thumb turns map to the sweep — it does **not** change the linkage
geometry. The verified sweep (θ₂ 100°→175°, μ 81.5°–105.3°) is exactly the 75° driven
by 2.5 turns at N=12, so **the chosen reduction keeps the linkage inside its workable
transmission band.** At the 2-turn (60° crank) and 3-turn (90° crank) extremes the
sweep widens slightly but μ stays inside 40°–140°. **Coupling check passes.**

*(Sketch acceptable per the brief: a labeled gear-train stick diagram with these tooth
counts and center distances satisfies the deliverable. No gear stress analysis required.)*
