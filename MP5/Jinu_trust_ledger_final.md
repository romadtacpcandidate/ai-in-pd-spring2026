# MP5 — Final Trust Ledger (updated post-Part B)


| What I trust | What still needs checking before a working print |
|---|---|
| Transmission angle 81.5°–105.3° across the full 75° sweep — hand calc (3 pts) + sim. No singularity risk. | Ideal-revolute-joint model: printed pin clearance (0.1 mm post-print) and friction unmodeled; could degrade effective μ/stroke. |
| Single-side displacement 20.9 mm → ~41.9 mm total jaw, monotonic — hand calc and sim agree to <0.1 mm. | Input range 100°–175° depends on the N=12 reduction; verified for N=12, re-check if N changes. |
| No link intersects another — 5.18 mm min clearance (interference sweep). | Symmetry holds only if the sync pair counter-rotates exactly — verified in ratio (1:1), not in a built assembly. |
| Fits the 46×55 mm half-envelope, 2.02 mm min wall clearance; Grashof crank-rocker, drivable. | The 2 mm width margin is tight — not yet confirmed in 3D with wall thickness + pin heads + mirror overlap. |
| Drive train: N=12:1, 1:1 sync, coupling check passes (reduction keeps μ in band). | Gear teeth at m=1.0 mm (root fillet ~0.38 mm) — print a test gear first; m=1.25 fallback. Tooth strength/backlash unverified. |
| Motion artifact confirms a smooth, bind-free open→close cycle (sim + GIF). | Part count is 27 vs. the <15 target — needs the gear/housing merges named in DFM. |

## Bottom line
Kinematics and drive-train ratio are prototype-ready and triangulated. Mechanical
robustness (joint tolerance, gear strength, 3D envelope, part count) is explicitly
not yet verified and is what I'd resolve before committing to a full print.
