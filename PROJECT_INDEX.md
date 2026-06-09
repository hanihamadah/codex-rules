# Workspace Project Index

Last updated: 2026-06-09

This is the central project index for the `Codex-OpenAI-IOs` workspace. Read it
after `MEMORY.md` and `DECISIONS.md`, before choosing files to edit.

## How To Use This Index

1. Identify the user's target project from the table below.
2. Confirm the source folder before editing.
3. Read the project README, handoff, or review document listed for that project.
4. Use the verification command or check listed before saying work is complete.
5. Treat live deploys, database imports, and connector writes as gated actions.

## Status Legend

- Live: public URL is known and should be verified before claiming current state.
- Draft: source exists but needs review, completion, or publishing.
- Internal: useful workflow or generated asset, not a public site.
- Gated: can affect live data, public deploys, or production-like state.
- Needs index: useful project exists but needs fuller documentation.

## Project Inventory

| Project | Status | Source Folder | Known URL | Deploy Target | Verification | Next Useful Action |
| --- | --- | --- | --- | --- | --- | --- |
| Codex Rules | Live | `AGENTS.md`, `MEMORY.md`, `DECISIONS.md`, `PROJECT_INDEX.md` | `https://github.com/hanihamadah/codex-rules` | GitHub repo `hanihamadah/codex-rules` | `git status --short`; confirm files in repo | Keep central rule files synced after each durable decision |
| Physics Learning Tools Hub | Live | `index.html`; `Physics Learning Tools/index.html` | `https://physics-learning-tools.hani-hamadeh.workers.dev/` | Cloudflare Workers/Pages style public hub | Open the URL and verify all tool cards | Reconcile duplicate root and folder hub files; keep links current |
| Classroom Field Lab | Draft | `classroom-field-lab/` | Local preview only unless deployed | Suggested Cloudflare Pages project `classroom-field-lab` | From `classroom-field-lab/`: `python3 -m http.server 4173` | Review current visual state, then publish only after approval |
| Distance and Displacement Simulation | Live | `Distance and Displacement Sim/` | `https://hanihamadah.github.io/distance-displacement-simulation/` | GitHub Pages | Open `Distance and Displacement Sim/index.html` or live URL | Add worksheet/remediation links only if useful for the hub |
| Enhanced Pulley System | Live | `Enhanced Pulley System/` | `https://hanihamadah.github.io/enhanced-pulley-system/` | GitHub Pages repo `hanihamadah/enhanced-pulley-system` | Open live URL with a cache-busting query before trusting updates | Keep as a single-file static deploy unless scope changes |
| Final Exam Mastery Trainer | Live | `physics-final-exam-prep/` | `https://physics-final-exam-prep.hani-hamadeh.workers.dev/` | Cloudflare public tool | Open `physics-final-exam-prep/index.html` and live URL | Keep official; add worksheet questions later if requested |
| Momentum and Impulse Mastery Trainer | Live, deploy target needs reconciliation | `momentum adaptive trainer/` | `https://momentum-impulse-mastery-trainer.hani-hamadeh.workers.dev/` | Live URL is Cloudflare; folder also has `netlify.toml` | Open `momentum adaptive trainer/index.html` and live URL | Clarify whether Cloudflare or Netlify is the source deploy path |
| AUS PHY001 Preparatory Physics | Live | `aus-phy001-preparatory-physics/` | `https://aus-phy001-preparatory-physics.hani-hamadeh.workers.dev/` | Cloudflare public tool | Open `aus-phy001-preparatory-physics/index.html` and live URL | Add Week 4 using the existing teacher/template panel pattern |
| Prompting Is Thinking Clearly | Draft | `Prompting-Is-Thinking-Clearly/` | None recorded | Static site, GitHub Pages or Cloudflare TBD | Open `Prompting-Is-Thinking-Clearly/08_Website/index.html` | Produce the first three episodes using the existing template |
| Moodle Assessment Packaging | Internal | `tools/`; `generated-assessments/` | Not public | Local document/PDF generation | Run the converter on a known Moodle XML export and compare PDFs | Create a reusable `moodle-assessment-packaging` skill |
| AI Assistants for Teachers Workshop | Internal | `AI_Assistants_for_Teachers_Workshop.docx`; `AI_Assistants_for_Teachers_Workshop_with_Leadership.docx`; `tools/build_ai_teachers_workshop_doc.py` | Not public | Generated DOCX artifacts | Render or inspect the DOCX before sharing | Add a short project note describing audience, version, and source script |
| Physics Mastery Content Drafts | Gated | `content-drafts/` | Supabase/app state, not direct public files | Supabase import after review only | Review JSON/SQL, check live slugs, confirm idempotence | Turn the import pattern into `physics-content-import` skill |
| Physics Mastery Engine | Gated, external repo | `/Users/Administrator1/Developer/physics-mastery-engine` | App URL not recorded here | Dedicated repo and app deploy pipeline | In that repo: read `AGENTS.md`, `WORKING_MEMORY.md`, `PROJECT_INDEX.md`, `README.md`; then run project checks | Do not work from this iCloud workspace; route to the dedicated repo |
| Custom GPT Registry | Missing | `CUSTOM_GPTS.md` not created yet | Not applicable | Local registry first | Confirm each GPT has purpose, instructions, files, actions, limits | Next item: create `CUSTOM_GPTS.md` |
| Connector and Plugin Policy | Missing | `CONNECTORS_AND_PLUGINS.md` not created yet | Not applicable | Local policy first | Confirm each connector has a job and safety boundary | Create after `CUSTOM_GPTS.md` |

## Project-Specific Read-First Files

### Root Workspace

- `AGENTS.md`
- `MEMORY.md`
- `DECISIONS.md`
- `PROJECT_INDEX.md`
- `README.md`

### Classroom Field Lab

- `classroom-field-lab/README.md`
- `classroom-field-lab/classroom-field-lab-complete-site-review.md`
- `handoff.md`
- `handoffs/june1_handoff.md`

### Prompting Is Thinking Clearly

- `Prompting-Is-Thinking-Clearly/README.md`
- `Prompting-Is-Thinking-Clearly/00_Project-Brief/project-overview.md`
- `Prompting-Is-Thinking-Clearly/00_Project-Brief/episode-template.md`

### Physics Mastery Engine

Use the dedicated repo:

- `/Users/Administrator1/Developer/physics-mastery-engine/AGENTS.md`
- `/Users/Administrator1/Developer/physics-mastery-engine/WORKING_MEMORY.md`
- `/Users/Administrator1/Developer/physics-mastery-engine/PROJECT_INDEX.md`
- `/Users/Administrator1/Developer/physics-mastery-engine/README.md`

## Verification Notes

- Do not claim a public URL is current unless it has been opened or checked in the current session.
- For static sites, opening the local `index.html` may be enough for basic review; use a local server when relative asset behavior matters.
- For `classroom-field-lab/`, the known local server command is `python3 -m http.server 4173` from inside that folder.
- For GitHub Pages updates, use a cache-busted URL after deployment before calling the update verified.
- For database imports, review a draft first, inspect existing slugs, and use idempotent SQL where possible.
- Do not open `.env.local`.

## Current One-By-One Fix Sequence

1. Create this `PROJECT_INDEX.md`. Status: done.
2. Create `CUSTOM_GPTS.md`.
3. Create `CONNECTORS_AND_PLUGINS.md`.
4. Expand `.gitignore` hygiene.
5. Turn repeated workflows into skills.
6. Preserve draft gates in the relevant workflow files.
7. Avoid adding more tools until routing and verification are stable.
