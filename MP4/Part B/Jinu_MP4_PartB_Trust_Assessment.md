# MP4 Part B — Per-Subsystem Trust Assessment

The central evaluation artifact. Each subsystem: what is verified, what is unverified,
what would have to be true for it to print and work. Prototype-readiness flagged.

| Subsystem | Verified | Unverified | Must be true to print & work | Ready? |
|---|---|---|---|---|
| **Four-bar linkage** | Kinematics, μ-band 81.5–105.3°, stroke 41.9 mm, envelope fit, no link crossing (Part A, three analyses + hand calc). | Joint clearance/friction, grip force at tip. | Printed pins hold tolerance; assembly stays on the open branch. | **Yes** (kinematically) |
| **Drive train** | Reduction N=12:1, sync ratio 1:1, coupling check (band preserved). | Tooth bending strength, backlash, lost motion over 75°. | m=1 teeth print clean; backlash < lost-motion budget. | **Partial** |
| **Jaw arms** | Geometry inherited from output link. | Stiffness, contact face, grip surface. | Arms don't deflect under grip load. | **No** |
| **Housing** | Envelope fit (Part A bbox, 2 mm wall margin). | Mounting stiffness, bearing/pivot seats, 3D stack-up. | Pivots stay located under load; 2 mm margin survives 3D. | **No** |
| **Input (thumb) wheel** | Turn-count → sweep mapping (2.5 turns → 75°). | Knurl/grip ergonomics, drive torque. | User torque < what the train transmits without slipping. | **Partial** |
| **Pin/joint system** | Nominal revolute geometry. | Clearance fit, wear, friction. | 0.2–0.3 mm printed clearance gives free rotation, no slop. | **No** |

## Known unknowns (explicit)
- **Symmetry assumption** holds only if the sync pair counter-rotates exactly — verified
  in ratio (1:1) but not yet in a built assembly.
- **Input-angle range (100°–175°)** depends on the reduction; verified for N=12 but would
  need re-checking if N changes.
- **Ideal-joint model** underlies every kinematic claim; real printed clearance/friction
  is unmodeled.

## Prototype-readiness summary
Kinematics and drive-train ratio are prototype-ready. Mechanical robustness (joint
tolerance, arm/housing stiffness, gear strength) is not yet verified and gates a print.
