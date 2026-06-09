# Workspace Decisions

Last updated: 2026-06-09

This file records durable decisions for the `Codex-OpenAI-IOs` workspace.
Read it before starting any work.

## Decision 1: `MEMORY.md` and `DECISIONS.md` Are Mandatory Read-First Files

Decision:

- Every work session in this workspace must read `MEMORY.md` and `DECISIONS.md` before planning or editing.

Why:

- The workspace contains multiple unrelated projects.
- Without a read-first layer, agents waste time rediscovering context and may edit the wrong target.
- The user wants durable project memory in plain Markdown.

Implication:

- Do not start by assuming the current directory is the project.
- Identify the active project folder first.

## Decision 2: Add `AGENTS.md` as the Enforcement Pointer

Decision:

- Add a root `AGENTS.md` that tells future Codex agents to read `MEMORY.md` and `DECISIONS.md` first.

Why:

- `MEMORY.md` and `DECISIONS.md` are useful only if future agents are told to read them.

Implication:

- `AGENTS.md` becomes the first instruction file for this workspace.

## Decision 3: This Workspace Is a Multi-Project Workbench

Decision:

- Treat this repository as a workbench containing several projects, not as one app.

Why:

- The root contains static tools, portfolio pages, AI literacy content, generated assessments, scripts, build outputs, and drafts.

Implication:

- Edits must be scoped to the project folder requested by the user.
- Handoffs should name exact folders and files.

## Decision 4: Physics Mastery Engine Uses Its Dedicated Repo

Decision:

- For Physics Mastery Engine work, route to `/Users/Administrator1/Developer/physics-mastery-engine`.

Why:

- That repo has the current read-first project state and verified workflow.
- The iCloud workspace has historically caused access and state confusion for that project.

Implication:

- Before Physics Mastery Engine work, read that repo's `AGENTS.md`, `WORKING_MEMORY.md`, `PROJECT_INDEX.md`, and `README.md`.

## Decision 5: Draft Gates Come Before Live Writes

Decision:

- For production-like content, use draft artifacts before live writes.

Why:

- This preserves reviewability and accuracy, especially for Supabase imports, public deploys, and classroom-facing materials.

Implication:

- Prefer `Google Drive/source -> draft file -> review -> approved import/deploy`.
- Do not write to Supabase or deploy publicly unless the user explicitly approves or directly asks for that action.

## Decision 6: Custom GPTs Need a Local Registry

Decision:

- Custom GPTs created by the user must be exported or summarized in a local registry before they can be audited or routed reliably.

Why:

- No local custom-GPT specs were found during the audit.
- GPTs that only exist inside ChatGPT UI are invisible to workspace-level review.

Implication:

- Create `CUSTOM_GPTS.md` next.
- Record each GPT's purpose, instructions, knowledge files, actions, connector access, and accuracy checks.

## Decision 7: Connectors and Plugins Should Be Routed by Job

Decision:

- Use connectors and plugins according to defined jobs, not because they are available.

Why:

- The enabled plugin surface is broad.
- More tools can reduce accuracy if their roles are unclear.

Implication:

- Google Drive is for source material.
- Supabase is for approved app data changes.
- GitHub is for repo evidence and publishing.
- Browser is for local preview and UI QA.
- Documents, Presentations, and Spreadsheets are for their matching file types.
- Data Analytics is for source-backed quantitative work.
- Product Design and Creative Production are for design and visual exploration.
- Cloudflare/Vercel are for deployment and infrastructure.
- Other connectors are situational.

## Decision 8: Do Not Open or Expose Secrets

Decision:

- Do not open `.env.local` unless the user explicitly requests secret handling and it is necessary.

Why:

- `.env.local` exists in the root workspace.
- Secret files can contaminate chat, commits, and logs.

Implication:

- Treat `.env.local` as sensitive.
- Add secret patterns to `.gitignore` in a future hygiene pass.

## Decision 9: Simple Static Projects Stay Simple

Decision:

- For static/content projects, default to simple HTML/CSS/JS and minimal starter files unless the user asks for a fuller app.

Why:

- The user has explicitly preferred not overengineering this kind of work.
- Several projects are publishable static pages.

Implication:

- Do not add frameworks, build steps, databases, or complex deployment unless there is a clear need.

## Decision 10: Evidence Beats Generic Advice

Decision:

- Recommendations should be tied to concrete evidence.

Why:

- The user prefers grounded recommendations from files, diffs, tests, screenshots, PRs, connector results, and generated artifacts.

Implication:

- If evidence is weak, say so.
- Avoid broad productivity advice that is not anchored to this workspace.

## Decision 11: Turn Repeated Workflows Into Skills

Decision:

- Repeated workflows should become named skills or documented procedures.

Why:

- The existing `daily-bug-scan` skill shows that encoded workflows improve consistency.
- Teaching/content workflows repeat often enough to benefit from the same treatment.

Implication:

- Candidate future skills:
  - `physics-content-import`
  - `moodle-assessment-packaging`
  - `static-site-publish`
  - `teacher-handoff`
  - `prompt-library-production`

## Decision 12: `.gitignore` Needs a Hygiene Pass

Decision:

- `.gitignore` should be expanded.

Why:

- It currently only ignores `.DS_Store`.
- The workspace contains generated files and dependency folders that should not become accidental commit candidates.

Implication:

- Future hygiene pass should cover:
  - `.env`
  - `.env.*`
  - `node_modules/`
  - `dist/`
  - `test-results/`
  - `*.tsbuildinfo`

## Decision 13: Keep Handoffs Close to Work

Decision:

- Important project decisions, status, and next steps should be saved near the project, and also summarized in central memory when they affect future routing.

Why:

- Local handoffs are useful during a project.
- Central memory is useful when choosing which project or workflow to start with.

Implication:

- Use project-level `README.md`, review docs, and handoff files for details.
- Use `MEMORY.md` and `DECISIONS.md` for cross-project routing and durable decisions.
