# Custom GPT Registry

Last updated: 2026-06-09

This file is the central registry for user-created custom GPTs. Read it before
asking Codex, ChatGPT, or a connector to rely on a custom GPT.

## Purpose

Custom GPTs are useful only when their role, instructions, files, actions, and
limits are visible. This registry prevents hidden overlap, stale instructions,
unsafe connector use, and unclear routing between GPTs, Codex, plugins, and
manual teacher judgment.

## Current Audit Status

No exported custom-GPT instructions are recorded in this workspace yet.

Because the GPTs are not yet documented here, they cannot be fully audited for:

- Purpose overlap.
- Instruction quality.
- Knowledge-file freshness.
- Action or connector permissions.
- Accuracy risks.
- Whether Codex should use them, ignore them, or replace them with a local workflow.

## Mandatory Rule

Do not invent or summarize a custom GPT from memory. Add a GPT to this registry
only from one of these sources:

- The GPT Builder instructions copied by the user.
- A user-provided screenshot or export of the GPT configuration.
- A user-provided plain-language description, clearly marked as incomplete.
- A repository or document that contains the GPT's real instructions.

If the GPT is incomplete, mark its status as `Needs export`.

## Registry Summary

| GPT Name | Status | Primary Job | Owner/Use Context | Knowledge Files | Actions/Connectors | Codex Routing | Next Audit Action |
| --- | --- | --- | --- | --- | --- | --- | --- |
| No GPTs recorded yet | Needs export | Unknown | Unknown | Unknown | Unknown | Do not route work to this GPT yet | Paste/export GPT details into the template below |

## Status Labels

- Active: ready to use and reviewed.
- Draft: instructions exist but still need testing or cleanup.
- Needs export: known GPT exists, but its actual configuration is not recorded here.
- Retired: do not use except for historical reference.
- Replaced: use a newer GPT, Codex workflow, skill, or plugin instead.

## Risk Labels

Use one or more of these labels in each GPT record:

- Low risk: drafting, brainstorming, formatting, or low-stakes teaching support.
- Medium risk: classroom-facing material, public content, generated assessments, or workflow recommendations.
- High risk: student data, grades, credentials, live database writes, public deploys, or connector actions.
- Accuracy sensitive: physics/math, exam preparation, source-backed claims, policy, or anything requiring verification.
- Permission sensitive: uses Drive, Gmail, Calendar, Supabase, GitHub, Slack, SharePoint, or external actions.

## Routing Labels

Use one or more:

- Teacher content.
- Physics problem generation.
- Misconception diagnosis.
- Assessment packaging.
- AI literacy.
- Public portfolio/content.
- Coding/prototyping.
- Data/reporting.
- Connector workflow.
- Image/creative production.

## GPT Record Template

Copy this section for each GPT.

### GPT Name

Status:

Risk labels:

Routing labels:

Owner/use context:

Last reviewed:

#### Primary Job

What this GPT is for:

What this GPT is not for:

#### User-Facing Description

Paste the GPT description shown to users:

```text

```

#### Instructions

Paste the full GPT Builder instructions:

```text

```

#### Knowledge Files

List every attached file, its purpose, and freshness.

| File | Purpose | Date/version | Source | Freshness Risk | Keep/Update/Remove |
| --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |

#### Actions and Connectors

List every action, connector, or capability the GPT can use.

| Action/Connector | Purpose | Data It Can Access | Write Access? | Approval Needed? | Risk Notes |
| --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |

#### Output Contract

Expected output format:

Required checks before final answer:

Things it must cite or show:

Things it must never claim without verification:

#### Safety Boundaries

What it should never do:

Sensitive data rules:

Student data rules:

Live-write rules:

#### Codex Routing

Use this GPT instead of Codex when:

Use Codex instead of this GPT when:

Use a connector/plugin instead when:

Use teacher judgment/manual review when:

#### Accuracy Checks

Minimum checks before trusting output:

- [ ] The task is inside the GPT's stated purpose.
- [ ] Attached knowledge files are current enough.
- [ ] Any factual or technical claims are verified when needed.
- [ ] Math/physics answers are checked independently.
- [ ] Connector or action writes are gated by explicit approval.
- [ ] Output matches the required classroom/audience context.

#### Test Prompts

Use these to check whether the GPT behaves correctly.

1. 
2. 
3. 

#### Audit Notes

Known strengths:

Known weaknesses:

Overlaps with other GPTs/tools:

Decision:

Next action:

## Intake Checklist For A New GPT

Before marking a GPT `Active`, complete this checklist:

- [ ] Name and purpose are clear.
- [ ] Full instructions are recorded.
- [ ] Knowledge files are listed.
- [ ] Actions/connectors are listed.
- [ ] Write-capable actions are explicitly marked.
- [ ] The GPT has a clear "should not do" boundary.
- [ ] Codex routing is clear.
- [ ] Accuracy checks are practical.
- [ ] At least three test prompts are recorded.
- [ ] The GPT does not duplicate an existing GPT without a reason.

## Audit Questions

Use these questions when reviewing all custom GPTs together:

1. Which GPTs solve the same problem?
2. Which GPTs are only prompts and could become Markdown templates instead?
3. Which GPTs need connector permissions removed?
4. Which GPTs need fresher knowledge files?
5. Which GPTs should be replaced by a Codex skill or project workflow?
6. Which GPTs are safe for low-stakes drafting only?
7. Which GPTs need a human approval gate before use?

## Next Step

Paste or export the first custom GPT configuration into the template above, then
audit it before adding the next one.
