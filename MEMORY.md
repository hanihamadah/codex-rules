# Workspace Memory

Last updated: 2026-06-09

This is the central read-first memory for the `Codex-OpenAI-IOs` workspace.
Every new work session should read this file and `DECISIONS.md` before planning,
editing, deploying, importing data, or making recommendations.

## Read-First Rule

Before any work starts:

1. Read `MEMORY.md`.
2. Read `DECISIONS.md`.
3. Read the target project's own `README.md`, handoff, or review document.
4. Confirm the active project folder before making edits.
5. Treat live writes, database imports, deploys, and connector actions as gated actions that need explicit approval unless the user has clearly asked for them.

## Workspace Purpose

This workspace is a multi-project teaching, physics, AI-literacy, and publishing workbench. It is not one single application. The main work families are:

- Physics learning tools, simulations, revision trainers, and portfolio pages.
- Classroom Field Lab, a public teacher portfolio and AI-in-teaching field notebook.
- Prompting Is Thinking Clearly, an AI literacy and classroom prompting project.
- Moodle and assessment packaging workflows.
- Content drafts for Physics Mastery Engine imports.
- Generated teaching documents and handoff artifacts.

## Current Project Map

### Physics Learning Tools

Root paths:

- `README.md`
- `index.html`
- `Physics Learning Tools/index.html`
- `Distance and Displacement Sim/`
- `Enhanced Pulley System/`
- `physics-final-exam-prep/`
- `momentum adaptive trainer/`
- `aus-phy001-preparatory-physics/`

Known live hub:

- `https://physics-learning-tools.hani-hamadeh.workers.dev/`

Use this family for public-facing physics tools, simulations, revision support, and lightweight static sites.

### Classroom Field Lab

Root path:

- `classroom-field-lab/`

Important files:

- `classroom-field-lab/README.md`
- `classroom-field-lab/classroom-field-lab-complete-site-review.md`
- `handoff.md`
- `handoffs/june1_handoff.md`

Use this for the public teacher portfolio, field notes, AI workflow explanation, project cards, and classroom-tool presentation.

Known pattern:

- Keep edits scoped to `classroom-field-lab/`.
- Published cards should link to real destinations.
- Unpublished cards should use status notes instead of dead placeholder links.
- Local preview has previously used `python3 -m http.server 4173` from `classroom-field-lab/`.

### Prompting Is Thinking Clearly

Root path:

- `Prompting-Is-Thinking-Clearly/`

Important files:

- `Prompting-Is-Thinking-Clearly/README.md`
- `Prompting-Is-Thinking-Clearly/00_Project-Brief/project-overview.md`
- `Prompting-Is-Thinking-Clearly/00_Project-Brief/episode-template.md`
- `Prompting-Is-Thinking-Clearly/08_Website/index.html`
- `Prompting-Is-Thinking-Clearly/08_Website/episodes.json`

Use this for classroom AI literacy content. Keep it practical, teacher-friendly, student-friendly, and simple. Avoid overcomplication, corporate AI language, and prompt-engineering jargon.

### Moodle and Assessment Packaging

Root paths:

- `tools/`
- `generated-assessments/`

Important file:

- `tools/moodle_xml_to_pdfs.py`

Known pattern:

- Moodle XML exports can be converted into a student questions PDF and a separate answer-key PDF.
- Teacher-facing handoffs should use one copy/paste prompt plus one plain WhatsApp-style explanation when useful.
- Generated outputs belong under `generated-assessments/`.

### Physics Mastery Engine

Important note:

- Current ongoing Physics Mastery Engine work should route to `/Users/Administrator1/Developer/physics-mastery-engine`, not this iCloud workspace.

Mandatory read-first files in that repo:

- `AGENTS.md`
- `WORKING_MEMORY.md`
- `PROJECT_INDEX.md`
- `README.md`

Preserve the stored sequence there:

1. Workspace access and repo verification.
2. Trust hardening for auth, student data, attempt persistence, and dashboard behavior.
3. Content import pipeline.
4. Content-gap filling only when converted into Mastery Engine concepts, skills, and problems.
5. Secondary distribution polish for the Physics Learning Tools hub.
6. Standalone simulations only when embedded, linked for remediation, or used as source material.

### Content Drafts

Root path:

- `content-drafts/`

Important files:

- `content-drafts/inclined-plane-resolution-forces-tentative.json`
- `content-drafts/import-inclined-plane-resolution-forces-approved.sql`

Known pattern:

- Draft content should stay reviewable before any database write.
- The successful architecture is `Google Drive source -> draft artifact -> reviewed import -> Supabase tables -> app`.
- Check live concept and skill slugs before importing to avoid duplicates.
- Use idempotent imports where possible.

## Audit Result Summary

The main audit conclusion was:

The workspace does not need more tools first. It needs stronger routing, indexing, and verification so ChatGPTs, Codex, connectors, plugins, and local files point to the same source of truth.

Strong existing patterns:

- Mature projects often have a README, handoff, or review document.
- Draft gates already exist for content imports.
- Static content projects benefit from simple HTML/CSS and minimal tooling.
- Evidence-backed review is already encoded in the `daily-bug-scan` skill.

Current weaknesses:

- No central registry existed before this file.
- No local registry of user-created custom GPTs was found.
- Connector and plugin usage is broad but not centrally routed by job.
- The root workspace contains many unrelated projects and generated outputs, so agents can confuse the active target.
- `.gitignore` is currently too small for the workspace shape and does not yet cover common generated or secret-bearing files.
- `.env.local` exists and should not be opened or committed.

## Custom GPT Visibility Gap

No local custom-GPT registry or instruction exports were found during the audit.

Until the user exports or records them, custom GPTs cannot be fully audited for:

- Purpose overlap.
- Instruction quality.
- Knowledge-file freshness.
- Connector/action permissions.
- Accuracy risks.
- When to use each GPT instead of Codex or a plugin.

Recommended future file:

- `CUSTOM_GPTS.md`

Suggested fields:

- GPT name.
- Purpose.
- Instructions.
- Knowledge files.
- Actions or connectors.
- What it should never do.
- When to use it.
- When not to use it.
- Accuracy checks.

## Connector and Plugin Routing Memory

Use connectors and plugins by job, not by novelty.

Core useful routing:

- Google Drive: source teaching material, Docs, Slides, Sheets, source references.
- Supabase: approved app data work and reviewed imports only.
- GitHub: repo inspection, publishing, PRs, issues, Pages, and evidence trails.
- Browser: local preview, UI inspection, screenshots, and visual QA.
- Documents: `.docx` teaching documents and verified document generation.
- Presentations: decks and slide artifacts.
- Spreadsheets: CSV/XLSX analysis, workbooks, and tabular teacher resources.
- Data Analytics: source-backed reports, dashboards, KPI analysis, and charts.
- Product Design: product/UI design work, redesign, prototype, and image-to-code.
- Creative Production: campaign visuals, mood boards, ads, logos, and generated creative exploration.
- Cloudflare/Vercel: deployment and web app infrastructure.
- Gmail/Calendar/Notion/Slack/SharePoint/Replit/Remotion/HyperFrames: situational only when the task explicitly needs them.

## Mandatory Safety and Accuracy Rules

- Do not open `.env.local` or expose secrets.
- Do not commit generated or secret-bearing files unless the user explicitly approves and the files are appropriate.
- Do not assume the root workspace is the active app.
- Use exact file paths in handoffs.
- Use concrete evidence from files, diffs, screenshots, tests, connector results, or source artifacts.
- If evidence is weak, say so.
- Keep static/content projects simple unless the user asks for a full app.
- Before live database writes or public deploys, prefer a draft or preview step first.
- For Physics Mastery Engine, use the dedicated repo and its read-first files.

## Immediate Recommended Next Actions

1. Create `CUSTOM_GPTS.md` from exported user-created GPT instructions.
2. Create `CONNECTORS_AND_PLUGINS.md` to formalize tool routing and permissions.
3. Expand `.gitignore` for `.env*`, `node_modules/`, `dist/`, `test-results/`, and TypeScript build info.
4. Convert repeated workflows into skills:
   - `physics-content-import`
   - `moodle-assessment-packaging`
   - `static-site-publish`
   - `teacher-handoff`
   - `prompt-library-production`
5. Keep project-specific handoffs close to the folder they describe.
