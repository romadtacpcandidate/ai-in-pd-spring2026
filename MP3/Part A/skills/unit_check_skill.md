Save this exact content as MP3/Part A/skills/unit_check_skill.md. First character is a dash, last character is a period.

name: unit-check
description: >
Review a piece of engineering text (a calculation walk-through, a memo,
a problem statement) for unit-of-measure errors before the numbers are
used. Triggered when the user asks you to check or verify an
engineering calculation that involves physical quantities with units.
Skill: Engineering Unit Check
When to use this skill
Use this whenever the user shares engineering text that mixes numbers
and units — torque + shaft diameter sizing, beam stress + safety factor,
fastener torque specs, pressure drops, anything where the answer
depends on the units coming out right. Use it even if the user didn't
explicitly ask for a "unit review" — if the message contains a
calculation and units, this skill applies. Don't use it for pure
symbolic algebra (no numbers) or for software questions where the
"units" are bytes or counts.
Steps

List every quantity in the text along with its stated unit. If a
number shows up without a unit, flag that gap first — an unstated
unit is the most common source of error.
Tag each quantity as SI (m, N, Pa, N·m, °C), US customary (in, lbf,
psi, in·lb, °F), or mixed. Mixing inside a single equation is a
red flag.
Check that each quantity's unit matches what the formula expects —
a length where a length goes, a torque where a torque goes, a
stress where a stress goes. A length written where a torque is
expected is a category error, not a typo.
Re-derive the answer with the user's numbers. If the result is off
by a clean conversion factor (~25, ~145, ~4.45, etc.) the unit
handling is the problem.
Report findings in a numbered list, most critical first, with the
correction.

What to flag

Category errors. A length used where a torque belongs, a mass
(kg, lbm) used where a force (N, lbf) is required, a stress (MPa,
psi) used where a pressure is required.
Silent unit swaps. mm written where inches were specified
(off by ~25x), psi written where MPa was specified (off by ~145x),
ft·lb written where in·lb was specified (off by 12x). These slip
past a quick read.
Mixed-system equations. US-unit inputs (in, lbf, psi) producing
a metric-unit output with no conversion factor visible.
Missing units. A bare "12" with no unit attached. State that
the unit is missing — don't guess.
Prefix slips. mm written as m, kPa as Pa, kN as N. Anything off
by 10^3 is almost always a dropped prefix.

What NOT to do

Do NOT silently substitute the unit you think the user meant and
proceed with the calculation. If you have to mentally swap "inches"
for "mm" to make the numbers work, that substitution IS the finding.
Do NOT guess at a missing unit. If the unit isn't stated, say so
and ask. Inventing the user's intent hides the error.
Don't only flag SI errors. US customary units are equally valid;
the issue is consistency inside the equation, not which system the
user picked.

Output format
Numbered list of findings, most critical first. For each: (1) what
phrase from the text, (2) what's wrong with the unit, (3) the
corrected version. End with one line: "units consistent", "unit
issue — correctable", or "category error — recompute".