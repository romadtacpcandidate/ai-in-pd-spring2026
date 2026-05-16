\# MP3 Part B — Reflection



\## What did you productize?



A printed-gear strength review that used to require an experienced engineer to run by hand — pull up the gear standard, look up the WidgetBot test report, run the Lewis check against the right allowable (interlayer, not bulk), and remember to flag the print-orientation requirement — now runs through the stack as a single prompt. Concretely: in the Checkpoint 1 conversation for my CAD review, I dropped in a SolidWorks gear screenshot with the basic parameters and got back six findings, each cited to a specific ACME doc (`ACME-ENG-001`, `ACME-MFG-002`, `ACME-MFG-003`), the Lewis math computed numerically, and a clean verdict format. The skill (`miniclaw\_gear\_strength\_review.md`) carries the workflow, the MCP server's `query\_miniclaw\_rag` tool pulls the company-specific numbers, and the AI is the conductor. The same prompt without the skill or the MCP would have returned a generic gear-design lecture; with both, it returned actionable findings keyed to ACME's actual practice.



\## Where does your stack break?



The stack breaks when the question contains a false premise that \*sounds\* internally consistent with the corpus. Concrete example from my Q3 query in the conversation export: I asked, "What did the Hiwonder BigClaw teardown reveal about printed gear pin diameters, and how should that inform our MiniClaw design?" The retrieval was clean — the BigClaw teardown chunks came back — but the question contained a false premise. The BigClaw is an all-aluminum gripper with no printed gears; pin-diameter guidance for printed assemblies actually lives in `ACME-MFG-004` (assembly guidelines), not the teardown notes. Claude caught the false premise this time (visible in the chat — "the BigClaw teardown is about aluminum gears, not printed ones... the question contains a false premise"), but the failure mode is real: a more confident-sounding misframing of a question could surface plausible chunks from the wrong document and produce a citation-rich answer that's still wrong. The stack has no built-in defense against premise errors — only the retrieved doc IDs to inspect, and the engineer's judgment about whether those IDs actually answer the question being asked.



\## Trust ledger



\*\*One place the skill helped the AI succeed.\*\* In Checkpoint 1 of the CAD review, my drive gear had 3 mm face width — exactly at the 3 × module floor that `ACME-ENG-001` lists as the hard minimum. Without the skill, an AI would likely have flagged this as a "marginal" pass against the standard. The skill explicitly tells the reviewer to flag "Face width at exactly 3 × module without an explicit reason" as a fail, because the WidgetBot 2.0 empirical data shows premature failure there. Claude did exactly that in its Checkpoint 1 review — finding 1, "Face width is at the absolute floor and below the empirical safe band — FAIL" — citing both the standard and the empirical band, which is the specific tension the skill's "what to flag" section is built around. The skill turned a borderline pass into a clear fail with engineering justification.



\*\*One place the AI did something wrong that the skill didn't catch.\*\* In Checkpoint 2, Claude ran the Lewis check at b = 4.0 mm with the standard Lewis form factor Y ≈ 0.337 (24 teeth, 20° full-depth) and reported σ\_eff ≈ 81 MPa at 0.5 N·m. The math is internally correct but it silently assumes the tooth is a fully-formed full-depth tooth with a clean trochoidal root. My 0.3 mm root fillet may or may not match that assumption — SolidWorks Toolbox generates a parametric fillet that probably doesn't match the trochoidal root shape the Lewis factor expects, and the AI used the textbook Y without flagging that mismatch. The skill's "what NOT to do" section warns against treating Lewis as sufficient when interlayer behavior is in play, but it doesn't catch this specific case — using a published Y for a tooth root that may not actually match the assumed geometry. The fix would be a skill update that requires the reviewer to confirm the actual root profile against the assumed Y, or to use a lower Y as a conservative bound when the profile hasn't been verified. (Logged for the next skill iteration, not retroactively fixed.)

