# MP4 Part B — MP5 Handoff

## Final design summary
A MiniClaw gripper using a **Grashof crank-rocker** four-bar per side (32/10/32/20 mm,
38 mm finger), mirrored, driven by a **12:1 compound spur train** with a 1:1 sync pair
that counter-rotates the two sides. Total jaw opening ~41.9 mm; transmission angle stays
81.5°–105.3° across the full stroke.

## What's prototype-ready
- Four-bar kinematics: stroke, transmission angle, envelope fit, no interference — all verified.
- Drive-train ratio and synchronization: N=12:1, 1:1 sync, coupling check passes.

## What's not ready
- Joint tolerance / friction (ideal-joint model only).
- Jaw-arm and housing stiffness; 3D envelope stack-up (2 mm width margin is tight).
- Gear tooth strength and backlash at m=1 mm.

## What I'll demonstrate in MP5
- Dynamic CAD/sim of the full open→close cycle (motion artifact already built: `motion/four_bar_sweep.gif`), **or** a physical print if joint tolerances check out in a test coupon.
- The triangulation story: hand calc + sim + AI loop agreeing on the kinematics, and the honest trust ledger of what still gates a working print.

## Open question for MP5
Whether printed pin-joint clearance degrades the verified transmission angle enough to
matter — this is the first thing to test on a coupon before committing to a full print.
