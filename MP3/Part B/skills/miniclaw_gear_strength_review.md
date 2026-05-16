name: miniclaw-gear-strength-review

description: >

Review a printed spur or helical gear intended for the MiniClaw drive

train against ACME's PLA gear standards before the part is committed

to a print run. Use this when a teammate proposes a gear geometry,

asks "is this gear strong enough", or hands over a SolidWorks

Toolbox gear without having checked it against ACME's prior printed-

gear failures. Not for aluminum or off-the-shelf gears.Skill: MiniClaw Printed Gear Strength ReviewWhen to use this skillUse this skill any time someone proposes a printed gear that will end

up in a MiniClaw drive train and asks for a review, sanity check, or

"is this strong enough" answer. Specific triggers:

A teammate pastes a SolidWorks gear screenshot or Toolbox callout

asking whether the geometry is "okay to print"

Anyone proposes a face width, module, or tooth count for a MiniClaw

drive gear

Anyone references the WidgetBot 2.0 test program or the

Hiwonder BigClaw teardown as a justification for a gear choice

(both are easy to misapply — see "What to flag")

Before committing a gear to a print run on ACME's Prusa MK4S shop

When a Lewis bending calculation is being applied to a printed PLA

gear without an interlayer-strength correction

Do NOT use this skill for aluminum, brass, or off-the-shelf gears —

the failure mode and the design rules are different. For DFM checks

unrelated to gear strength (wall thickness, supports, dimensional

tolerance), use the DFM skill instead.Workflow

Identify the gear's role. Drive gear (sees full torque), idler

(lighter loading), or hand-cranked (essentially no fatigue

loading)? The acceptable safety factor differs. Per

ACME-ENG-001, a SF ≥ 2.0 against the interlayer working

stress is required for any gear in the production drive train.



Consult the gear standard. Call the query\_miniclaw\_rag tool

and pull ACME-ENG-001 (Gear Design Guidelines). Confirm

module, tooth count, pressure angle, and face width are all

inside the documented limits. The minimum-teeth rule at module

0.8 is 16 teeth to avoid undercutting.



Apply the scaling rule for face width. Per ACME-ENG-001:

minimum face width = 3 × module (a hard floor only), production

recommendation = 4-6 × module. For module 0.8: 2.4 mm floor,

3.2-4.8 mm production range. Anything at 3 × module needs an

explicit reason and a tighter Lewis check.



Run the Lewis check against interlayer stress, not bulk

tensile. Compute tooth-root bending stress with the Lewis

form factor for the tooth count. Compare against the 28 MPa

interlayer working stress allowable (from ACME-MFG-002), not

against the \~50-60 MPa bulk tensile strength. Apply the 1.67

perpendicular-loading factor from ACME-ENG-001 if the tooth

sees off-axis loading.



Cross-check against WidgetBot 2.0 empirical data. Per

ACME-MFG-003, the WidgetBot program tested module 1.0 gears

and found premature failures at 3 × module face width even at

low loads, 4 × module as the practical minimum, and 6 × module

gave \~40% better cycle life than 4 × module. Translate to the

module you're reviewing and flag anything below the empirically

safe band.



Verify print orientation is specified. Gears must print

flat (teeth in-plane) so the interlayer-strength argument

holds. If the drawing or print queue note doesn't specify this,

that's a release-blocking gap.



Summarize. PASS / FLAG / FAIL per check, then one verdict

line: "release-ready", "release after edits", or "recompute".

What to flag

Face width below 3 × module. Hard fail by ACME-ENG-001.

Cite the standard, name the minimum, and propose a specific value

in the production band.



Face width at exactly 3 × module without an explicit reason.

The WidgetBot 2.0 data (ACME-MFG-003) shows premature failure

at 3 × module even at low loads, so the standard's floor and the

empirical floor disagree — design above the empirical floor unless

there's a hard packaging reason and a tighter analysis backing it.



Lewis check applied against bulk PLA tensile. Common error.

PLA's interlayer strength is roughly half the bulk tensile, and

the failure mode at the tooth root is delamination between layers,

not classical tooth-root fracture. Always check against the

ACME-MFG-002 interlayer allowable.



Citing the BigClaw teardown to justify a printed-gear choice.

Per ACME-VND-002, the BigClaw is all-aluminum — its teardown

does not transfer to printed-gear design. The pin-diameter

guidance for printed assemblies lives in ACME-MFG-004, not the

teardown notes.



Print orientation missing from the drawing. A gear designed

to print on-edge will fail in interlayer mode regardless of how

the math looks on paper.



Module below 0.8 on a drive gear. The print shop's tooth-tip

resolution at module < 0.8 is not consistently above the FilaTech

PolyPro shrinkage tolerance per ACME-MFG-001. Idler gears can

go smaller; drive gears should not.

What NOT to do

Do not approve a drive gear based only on the Lewis bending

check passing. Lewis bending is necessary but not sufficient

for printed PLA gears — the tooth root may pass on stress and

still fail by delamination if the face width is narrow or the

print orientation is wrong. The interlayer-stress check and the

WidgetBot-band check both have to pass too.



Do not extrapolate WidgetBot 2.0 face-width numbers

proportionally to other modules without saying so. The

WidgetBot data is at module 1.0. Scaling the 4 mm / 6 mm numbers

to module 0.8 by ratio is reasonable as a first check, but

call out that it's an extrapolation and that the empirical safe

band has not been confirmed at module 0.8 specifically.



Do not recommend supports as a fix for a bad print orientation.

ACME's print shop runs 500-unit batches and supports cost real

cycle time. If a gear needs supports, the geometry is wrong, not

the orientation.



Do not silently substitute aluminum-gear references (BigClaw

teardown, off-the-shelf gear catalogs) for printed-PLA design

decisions. They're different failure regimes.

Output formatNumbered list of findings, most critical first. For each: (1) what

you saw in the design, (2) which ACME document the constraint comes

from with the doc ID, (3) the corrected value or the specific

recompute the engineer needs to run. End with one verdict line:

"release-ready", "release after edits", or "recompute".

