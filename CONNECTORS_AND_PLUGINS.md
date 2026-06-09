# Connectors and Plugins Policy

Last updated: 2026-06-09

This file defines when to use each connector, plugin, and related skill in this
workspace. Read it before using external apps, live data, publishing tools, or
creative/data/document plugins.

## Purpose

The workspace already has a broad tool stack. The goal is not to add more tools.
The goal is to route work clearly, reduce accidental overuse, preserve draft
gates, and make future chats more accurate.

## Core Rule

Use connectors and plugins by job, not by novelty.

Before using any connector or plugin:

1. Identify the active project in `PROJECT_INDEX.md`.
2. Decide whether the task is read-only, draft-write, live-write, or sensitive.
3. Use the narrowest connector/plugin that matches the job.
4. Prefer drafts and local files before live writes.
5. Ask for explicit approval before public deploys, database writes, emails, calendar edits, Slack messages, or any action that changes external state unless the user directly requested that exact action.

## Action Risk Levels

| Level | Meaning | Examples | Approval Rule |
| --- | --- | --- | --- |
| Read-only | Inspecting files, repos, docs, events, emails, source records, or public pages | Search Drive, read GitHub PR, inspect Supabase schema, open local browser preview | Usually okay when relevant |
| Draft-write | Creating a local draft, report, document, registry, preview, or SQL file | Draft JSON, draft SQL, local DOCX, local static page, local report | Usually okay when user asked for creation |
| Live-write | Changing public or production-like state | Supabase insert/update, GitHub push, Pages deploy, Slack send, email send, calendar edit | Needs explicit approval unless directly requested |
| Sensitive | Secrets, student data, grades, private communications, credentials, payment/contact data | `.env.local`, student records, Gmail/Outlook messages, private Drive files | Avoid unless clearly necessary and approved |

## Default Tool Routing

| Tool | Primary Job | Use For | Do Not Use For | Approval Gate |
| --- | --- | --- | --- | --- |
| Google Drive | Source material and Google files | Find teaching decks, Docs, Sheets, Slides, source PDFs, curriculum material | Live app data, final source of truth for app state | Read usually okay; edits need approval |
| Supabase | Approved app data work | Inspect schema, query data, apply reviewed imports, manage app tables | Drafting unreviewed content directly into live tables | Writes need explicit approval |
| GitHub | Repo evidence and publishing | Inspect repos, PRs, issues, commits, Pages, create/push small repos | Storing secrets, broad workspace dumps, speculative commits | Push/PR/repo creation needs user intent |
| Browser | Visual QA and local web inspection | Open localhost, inspect UI, screenshots, click/test local targets | Replacing source-backed analysis or repo review | Low risk for local preview |
| Documents | Word/DOCX work | Create, edit, render, and verify `.docx` teaching documents | Spreadsheets, slide decks, raw data analysis | Draft-write okay; sharing/exporting needs approval |
| Presentations | Slide decks | Create, edit, render, and verify PPTX/slide decks | Long documents or spreadsheet analysis | Draft-write okay; sharing/exporting needs approval |
| Spreadsheets | Workbook and tabular file work | Create/edit/analyze XLSX, CSV, TSV, tables, formulas, charts | Freeform prose docs or live database writes | Draft-write okay; external sharing needs approval |
| Data Analytics | Source-backed analysis | Reports, dashboards, KPI design, data visualizations, metric diagnostics | Unsourced opinions or classroom copywriting | Use when data-backed output matters |
| Product Design | Product/UI design workflow | Design brief, UI audit, ideation, image-to-code, prototypes | Pure content drafting or backend-only tasks | Use when interface quality is central |
| Creative Production | Visual creative exploration | Mood boards, ad ideas, image prompts, logos, business visuals | Data analysis or exact UI implementation | Use for exploration; final brand use needs review |
| Fal | AI media generation | Generate or transform AI image/media assets | Repo-native SVG/CSS work where code is better | Generated assets need visual review |
| OpenAI Developers | OpenAI API work | API docs, model selection, API key workflows, ChatGPT apps | General teaching content when no OpenAI API is involved | API keys/secrets need confirmation |
| Vercel | Web app deployment and docs | Inspect Vercel deployments, deploy web apps, query Vercel docs | Cloudflare-specific projects unless chosen | Deploy/config changes need approval |
| Build Web Apps | Web app build guidance | Build functional web apps, browser-tested UI, frontend assets | Simple static pages that should stay simple | Use only when app complexity justifies it |
| Build Web Data Visualization | Advanced visualizations | Dashboards, charts, maps, scrollytelling, data-viz web artifacts | Plain static content pages | Use when data visualization is the actual product |
| Codex Security | Security review | Security scans, risk analysis, vulnerability review | Routine content drafting or design polish | Findings need evidence |
| Notion | Knowledge capture and planning | Docs, task plans, research synthesis if Notion is the destination | Source of truth for this local workspace unless user says so | Writes need approval |
| Gmail | Gmail email workflow | Search/reference Gmail, draft/send email if requested | General document storage or private data browsing without need | Sending needs explicit approval |
| Outlook Email | Outlook email workflow | Search/reference Outlook, draft/send email if requested | Same as Gmail | Sending needs explicit approval |
| Google Calendar | Scheduling | Availability, daily briefs, event creation/update | Project memory or task tracking | Event writes need explicit approval |
| Outlook Calendar | Scheduling | Availability, daily briefs, event creation/update | Same as Google Calendar | Event writes need explicit approval |
| Slack | Team messaging | Read or send Slack messages when task is explicitly about Slack | Private source of truth or broad workspace search | Sending needs explicit approval |
| SharePoint | Microsoft shared files | Search/read shared sites and OneDrive/SharePoint files | Google Drive workflows unless source lives in Microsoft | Edits need approval |
| Replit | Replit projects | Work with Replit apps/deployments when explicitly used | Local workspace projects or GitHub/Cloudflare deploys by default | Deployment/project changes need approval |
| Remotion | Programmatic video | React/Remotion video generation | Static sites, documents, normal slide decks | Render/export review required |
| HyperFrames by HeyGen | HTML-to-video and motion | Video compositions, captions, GSAP, web capture | Plain web pages or normal documents | Render/export review required |

## Local Skills Routing

These are not connectors, but they should guide tool choice.

| Skill | Use When | Notes |
| --- | --- | --- |
| `cloudflare` | Any Cloudflare platform task | Retrieve current docs before relying on changing limits or APIs |
| `workers-best-practices` | Writing/reviewing Cloudflare Workers | Use for production-readiness and anti-pattern checks |
| `wrangler` | Wrangler commands/config | Use before deployment or config work |
| `durable-objects` | Stateful coordination, WebSockets, alarms, SQLite DO storage | Use for DO design/review |
| `agents-sdk` | Cloudflare Agents SDK apps, MCP servers, workflows, stateful agents | Use current docs for API details |
| `cloudflare-email-service` | Sending/receiving transactional email on Cloudflare | Domain/setup/write actions are gated |
| `sandbox-sdk` | Secure code execution/sandbox apps | Use when building code interpreter or untrusted code execution |
| `web-perf` | Performance/Lighthouse/Core Web Vitals work | Requires browser/devtools verification |
| `daily-bug-scan` | Evidence-backed recent regression scans | Stop if no concrete evidence of a bug |

## Project Workflow Routing

### Physics Content Import

Preferred route:

1. Google Drive for source material.
2. Local draft JSON/Markdown/SQL file.
3. Human review.
4. Supabase inspection for existing concepts/skills/slugs.
5. Approved idempotent SQL import.
6. App verification.

Do not:

- Import directly from Drive to Supabase without a draft.
- Create duplicate concepts without checking existing slugs.
- Treat generated physics/math content as correct without checking it.

### Static Site Publishing

Preferred route:

1. Work in the project folder.
2. Keep static sites simple unless app complexity is requested.
3. Preview locally with Browser or a simple local server.
4. Deploy through GitHub Pages, Cloudflare, or Vercel only after the target is clear.
5. Verify the live URL with a cache-busting query.

Do not:

- Publish the whole root workspace when only one folder or file is needed.
- Add frameworks to simple content pages without a reason.

### Classroom Field Lab

Preferred route:

1. Work only in `classroom-field-lab/`.
2. Use Browser for local visual QA.
3. Replace dead links with real links or status notes.
4. Publish only after explicit approval.

### Prompting Is Thinking Clearly

Preferred route:

1. Use local Markdown templates first.
2. Use Documents/Presentations only when producing handoff files or workshop materials.
3. Use Creative Production only for visual exploration, not for core lesson accuracy.

### Moodle Assessment Packaging

Preferred route:

1. Use local source files and `tools/moodle_xml_to_pdfs.py`.
2. Generate student and answer-key outputs under `generated-assessments/`.
3. Use Documents only when `.docx` formatting is required.
4. Keep teacher handoffs simple and copy/paste friendly.

### Custom GPT Audit

Preferred route:

1. Use `CUSTOM_GPTS.md` as the source of truth.
2. Record real GPT instructions, not guesses.
3. Check knowledge files, actions/connectors, and overlap.
4. Decide whether each GPT remains active, gets revised, becomes a skill, or is retired.

## Connector Write Gates

The following actions need explicit approval unless the user directly asks for that exact live action:

- Supabase insert, update, delete, migration, policy, or schema changes.
- GitHub repo creation, push, PR creation, Pages settings changes, or release publishing.
- Public deploys on Cloudflare, Vercel, Netlify, Replit, or similar platforms.
- Gmail or Outlook send.
- Google Calendar or Outlook Calendar create/update/delete.
- Slack send.
- SharePoint/Drive file edits or moves.
- Any action involving `.env.local`, API keys, secrets, credentials, private student data, grades, or personal messages.

## Evidence Rules

Before making a recommendation, prefer one of these evidence sources:

- Local files and exact paths.
- Git diffs, commits, PRs, or issue threads.
- Build/test output.
- Browser screenshots or local UI inspection.
- Connector search results.
- Source documents, slides, sheets, PDFs, or datasets.
- Public documentation when APIs, pricing, limits, or current product behavior may have changed.

If evidence is weak, say so.

## Do Not Add More Tools Yet

Current decision:

- Do not add more connectors or plugins until the routing files are stable.

Reasons:

- The existing tool surface is already broad.
- More tools without routing increases confusion.
- The next efficiency gains should come from indexing, policies, draft gates, and reusable skills.

Exceptions:

- The user explicitly asks for a specific missing connector/plugin.
- A required job cannot be completed with available tools.
- The missing tool is needed to verify or protect a high-risk action.

## Quick Selection Guide

Use this when deciding quickly:

- Need source teaching files: Google Drive.
- Need app database work: Supabase, after draft review.
- Need repo/publish evidence: GitHub.
- Need local UI verification: Browser.
- Need `.docx`: Documents.
- Need slides: Presentations.
- Need tables/workbooks: Spreadsheets.
- Need source-backed metrics: Data Analytics.
- Need UI/product direction: Product Design.
- Need visuals/concepts: Creative Production or Fal.
- Need Cloudflare app/deploy/config: Cloudflare skills and Wrangler.
- Need email/calendar/message action: use the matching connector only with clear intent and approval.

## Maintenance Checklist

Review this file when:

- A new connector/plugin is installed.
- A repeated workflow becomes a skill.
- A live-write mistake or near-miss happens.
- A new project is added to `PROJECT_INDEX.md`.
- A custom GPT gets connector/action access.
