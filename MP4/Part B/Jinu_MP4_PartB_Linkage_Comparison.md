# MP4 Part B — Linkage Comparison Worksheet

> Solo note: the brief frames this as comparing teammates' Part A designs. Working
> solo, I compare my chosen Part A linkage against two variants I sketched during
> Part A tuning, on the same axes, and justify the pick.

## Candidates (same axes)

| Metric | **Chosen: 32/10/32/20, 38 mm finger** | Variant 1: 34/14/30/18, Lf 42 | Variant 2: 32/10/32/16, Lf 34 |
|---|---|---|---|
| Total jaw opening | 41.9 mm | ~52 mm | ~38 mm |
| Single-side displacement | 20.9 mm | ~26 mm | ~19 mm |
| Input sweep | 75° (100°→175°) | 75° | 75° |
| Transmission angle range | **81.5°–105.3°** | 58°–128° | 70°–118° |
| Min μ margin from singularity | 41.5° | 18° (tight near open) | 30° |
| Motion bounding box | 42 × 37.5 mm | 48 × 41 mm | 40 × 35 mm |
| Fits 46×55 half-envelope | yes (2.0 mm wall margin) | marginal (edges envelope) | yes |
| Grashof type | crank-rocker | crank-rocker | crank-rocker |

## Decision

**Chosen: 32/10/32/20 with a 38 mm finger.**

- **Kept** because the transmission angle stays closest to the ideal 90° (81.5°–105.3°),
  giving the most uniform output force across the whole stroke and the largest margin
  from a singularity.
- **Cut Variant 1** (34/14/30/18): it overshoots the stroke target and its μ dips to
  ~58° near full open — low margin and uneven force exactly where the jaw opens widest.
  It also edges the envelope.
- **Cut Variant 2** (32/10/32/16): meets the stroke target but has a lower μ-minimum
  (70°) and less force margin than the chosen design, with no offsetting benefit.

The chosen linkage is the design verified across all three Part A analyses, so no
re-analysis is required unless the Part B reduction shifts the input range (see the
coupling check in the Gear Pair Design).
