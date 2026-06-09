# MP4 Part B — DFM Checklist (completed)

**Team:** Jinu

> Geometry status: the linkage and drive train are verified as kinematics/plots
> (Part A) plus this drive-train spec. The nominal cross-sections, pin sizes, and
> face widths below are **design decisions I'm assigning now** to make the geometry
> printable — they need to be instantiated in SolidWorks before a real print, and
> are logged as new assumptions in the trust assessment.

Applied geometry: 32/10/32/20 crank-rocker (×2 mirrored), 38 mm finger; 12:1 compound
spur train (m = 1.0 mm), 1:1 sync pair.

---

## 1. Print Orientation

| Part | Orientation | Why | Supports? |
|------|-------------|-----|-----------|
| Linkage links (ground/input/coupler/output) | Flat on bed | Strongest in shear; layer lines perpendicular to in-plane pin loads | No |
| Gear 1, Gear 2 (and all train gears) | Flat on bed | Tooth profile fidelity; no support on tooth flanks | No |
| Jaw arm (integrated into output link) | Flat on bed | Same plane as the link it extends | No |
| Housing (split into 2 shells) | Largest face down | Minimizes support on internal pivot bosses | Yes (minor, internal bosses) |
| Pins | Upright (axis vertical) | Round holes/round pins; never along layer-line direction | No |

**AI assist:** Loop 5 (trust-assessment review) — the AI flagged that printing links
on edge would put layer lines along the pin load path; confirmed flat is correct.

---

## 2. Wall Thickness and Feature Size

| Part | Thinnest wall (mm) | Smallest feature (mm) | Flagged? |
|------|---------------------|------------------------|----------|
| Linkage links (4 mm plate) | 2.0 (web between pin bosses) | 4.0 (pin boss OD) | No |
| Gears | 1.5 (root land) | ~0.38 (root fillet) | **Yes — fillet < 1.0** |
| Housing shell | 2.0 | 4.0 (pivot boss) | No |
| Pins (4 mm OD) | n/a | 4.0 | No |

**Notes:** The gear root fillet (~0.38 mm at m=1.0) is below the ~1 mm comfortable FDM
feature; teeth may print slightly rounded. Mitigation: bump to **m = 1.25 mm** if a test
gear prints mushy, which raises the fillet proportionally.

---

## 3. Pin and Joint Clearances

All four revolute joints (O₂, O₄, A, B) use one pin size.

- **Pin OD (CAD nominal):** 4.00 mm
- **Hole ID (CAD nominal):** 4.30 mm
- **Designed clearance:** 0.30 mm diametral
- **Expected clearance after print** (holes ~0.10 undersize, pins ~0.10 oversize → net ≈ −0.20): **~0.10 mm**
- **Fit class:** sliding
- **Accept?** Yes — 0.10 mm post-print is a free-rotating sliding fit with minimal slop.
  If joints bind, open the hole to 4.40 mm nominal and re-test.

---

## 4. Gear Printability

| Check | Value | Notes |
|-------|-------|-------|
| Module (mm) | 1.0 | At the FDM floor; m=1.25 fallback ready |
| Smallest tooth feature (root fillet) | ~0.38 mm | **Flag — below 1.0 mm** |
| Tooth count (each gear) | 12 / 16 / 40 / 48 | z=12 pinion is **borderline** (threshold is z<12) |
| Face width (mm) | 5.0 | OK (> 3 mm) |
| Print orientation | Flat on bed | Preferred — no flank supports |
| Backlash designed in (mm) | 0.15 | Accounts for FDM over-extrusion |

---

## 5. Overhangs and Bridges

| Feature | Angle / span | Concern? | Mitigation |
|---------|--------------|----------|------------|
| Housing top inner edge over pivot pocket | ~50° overhang | Minor | Chamfer the edge to 45°, or brief support |
| Gear hub-to-web transition | bridge ~3 mm | No | Within 10 mm bridge limit |
| Link pin-boss to web | < 45° | No | Clean |

---

## 6. Assembly Sequence

1. Press/insert pins into the bottom housing shell pivot bosses (O₂, O₄ both sides).
2. Drop the gear train onto its shafts (compound shaft, sync pair), mesh-check by hand.
3. Install input crank links onto the gear-coupled shafts; install coupler links.
4. Install output+finger links onto O₄ pins; verify open→close sweep by hand.
5. Fit the top housing shell; secure with corner screws. Install thumb wheel last.

**Accessibility check:** Yes — pins and gears go in before the top shell, so nothing is
trapped. The only watch item is the sync-pair mesh, which must be set before the top
shell closes (it's not adjustable after).

**Snap-fit engagement:** No snap fits in the design (screwed housing), so PLA brittleness
isn't a deflection concern.

---

## 7. Part Count

| Part | Count |
|------|-------|
| Linkage links (input, coupler, output+finger per side × 2; ground = housing) | 6 |
| Pins | 8 |
| Gears | 6 |
| Jaw arms (integrated into output link) | 0 |
| Housing pieces | 2 |
| Input wheel / knob | 1 |
| Screws (housing) | 4 |
| **Total** | **27** |

**Under target (<15)?** **No — 27.** The drive train (6 gears + their shaft pins) is the
main driver. Merges to explore in MP5: integrate the finger into the output link (already
done), combine the two stage gears onto one printed compound part, reduce the train to a
single spur pair + a separate small reduction if a coarser reduction is acceptable, and
print the housing as one shell with a removable cover plate instead of two full shells.

---

## 8. Print Time and Material Budget

Rough Bambu Studio estimate on the planned geometry (0.2 mm layer, 15% infill, PLA):

- **Total print time (hours):** ~7
- **Total material (grams):** ~85 g
- **Print bed pieces:** 2 (housing shells + gears on one plate; links + pins + wheel on a second)
- **Notes:** Everything fits a standard 256 mm bed across two prints; gears grouped together
  so they print at one consistent flow setting.

---

## DFM Pass Bottom Line

Not ready for the print queue tomorrow. The three flags I'd address first: (1) the m=1.0 mm
gear teeth — print a single test gear before committing the whole train, with m=1.25 ready;
(2) the 27-part count, nearly double the <15 target, which needs the gear/housing merges
above; (3) the 2 mm envelope width margin from Part A, which has to be re-confirmed once
the housing wall thickness is added in 3D.

---

## AI Use During the DFM Pass

Loop 5 produced the orientation and housing-margin findings (the AI caught that I'd called
the housing "ready" before checking the 3D stack-up). I **rejected** one AI suggestion —
it proposed snap-fit housing closure to drop the screw count, but PLA snap fits at this wall
thickness are brittle and would complicate the assembly/disassembly needed for mesh-setting,
so I kept screws.
