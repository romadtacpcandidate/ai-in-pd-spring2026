# MP5 — Final Presentation (README)

**Team:** Jinu
**Presenting:** [Tue Jun 2 / Thu Jun 4 — fill in]

## Tools used across MP1–MP5
- Python (NumPy/Matplotlib) — closed-form four-bar solver, all analyses & plots
- Interactive HTML/JS simulator — live demo (same closed-form physics)
- SolidWorks — integration CAD (optional secondary demo)
- AI host + MP3 MCP stack — design synthesis, review loops, live tool call
- Bambu Studio — DFM print estimates

## Repo contents
- `slides.pdf` — the deck (present from this)
- `slides.pptx` — editable source
- `demo/miniclaw_sim.html` — interactive live demo (open in any browser)
- `demo/four_bar_sweep_fallback.gif` — recorded sweep, secondary fallback
- `trust_ledger_final.md` — updated post-Part B
- `MP5_Pillar_Narrative_Worksheet.md` — the story spine
- `MP5_Self_Assessment.md` — pre-flight checklist
- `final_design/` — CAD/sim, drawings/screenshots, parts list, assembly notes

## Demo plan
**Primary (it moves):** open `demo/miniclaw_sim.html` in the browser. Drag the slider so
both jaws mirror open→close. Point out the live transmission-angle badge staying in band
and the jaw readout reaching 41.9 mm. Self-contained — no internet, no CAD dependency.

**Fallbacks:** a screen recording of the simulator (record one and drop it in `demo/`), and
`demo/four_bar_sweep_fallback.gif`.

**Live MCP/tool call (required):** ask the stack a real design question back-to-back with the
sim — e.g. "given m=1.0 mm, z=12 pinion, what's the root fillet radius and is it printable on
a 0.4 mm nozzle?" Keep it short and deterministic. **Record a backup run** in `demo/` in case
the server is down — the brief grades on whether a call *runs*.

## Demo instructions (for the room)
1. Open `demo/miniclaw_sim.html`; drag the slider through the full sweep (or hit Play).
2. Run the MCP/tool call from the host; show the call and the returned answer.
3. If either fails: play the recorded simulator video and the recorded tool-call run.
