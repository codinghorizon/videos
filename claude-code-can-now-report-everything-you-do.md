---
layout: default
title: "It Runs On Your Laptop And Your Employer Can Read It"
permalink: /claude-code-can-now-report-everything-you-do/
date: 2026-08-13
---

# It Runs On Your Laptop And Your Employer Can Read It

Every figure, endpoint, retention period and coverage claim the finished shots put on
screen, chased to a primary source. Anthropic's own documentation is the primary source
for all of it, because the subject is a feature of that product and the wording of the
documentation is itself the thing under discussion.

Checked 2026-08-12.

## The change itself

**The Compliance API now covers Cowork and Claude Code.** Announced 11 August 2026:
coverage extends to "Cowork across the desktop app, web, and mobile, as well as Claude
Code in the CLI and desktop app", and it is included with the Compliance API using an
existing Compliance Access Key, with no separate integration to build.

- https://claude.com/blog/compliance-api-cowork-and-claude-code

**Local sessions on a user's own machine are in scope.** The documentation states that the
content endpoints serve, among other things, "local session transcripts, from Cowork and
Claude Code sessions that run on users' machines while they are signed in with their
Claude Enterprise account".

This is the sentence beat 032 quotes on screen, and it is the load-bearing claim of the
whole video.

- https://platform.claude.com/docs/en/manage-claude/compliance-api

**Which Claude Code surfaces.** "Cowork sessions that run on a user's machine in Claude
Desktop, and Claude Code sessions in the terminal, in Claude Desktop, or in an IDE
extension, are captured while the user is signed in with their Claude Enterprise account."

- https://platform.claude.com/docs/en/manage-claude/compliance-faq

**It is in beta.** "The local and remote session endpoints are in beta."

- https://platform.claude.com/docs/en/manage-claude/compliance-faq

## Who the feature is for

**Security, legal and compliance teams.** The documentation's own framing: the Compliance
API gives Claude Enterprise and Claude Console customers programmatic access to their
organization's Activity Feed, and "Security, legal, and compliance teams use it to audit
activity, retrieve or delete content, and feed events into downstream tooling."

This is the source for beat 016, and for the video's claim that this is a governance
feature rather than anything aimed at individual developers.

- https://platform.claude.com/docs/en/manage-claude/compliance-api

**Access is scoped and keyed.** The session endpoints require a Compliance Access Key
carrying `read:compliance_user_data`. A regular Claude API key does not authenticate
against `/v1/compliance/*` at all, and an Admin API key reaches the Activity Feed only.

- https://platform.claude.com/docs/en/manage-claude/compliance-faq

## The endpoints on screen

Beats 016 and 017 render real endpoint paths. They are:

- `GET /v1/compliance/apps/sessions/local` — list local sessions
- `GET /v1/compliance/apps/sessions/local/{session_id}` — one session's metadata
- `GET /v1/compliance/apps/sessions/local/{session_id}/messages` — the transcript

Source: https://platform.claude.com/docs/en/manage-claude/compliance-content-data

## What a transcript contains

Beat 017 puts the block types on screen and beat 020 lists what flows. From the coverage
table for local sessions:

| On screen | What the documentation says |
| --- | --- |
| User prompts | Yes, returned as `text` blocks |
| Assistant responses | Yes, text output only |
| Tool calls and results | Yes; `tool_use` inputs and `tool_result` text, **truncated to 10,000 bytes per block by default**, up to about 1 MiB per block on request |
| File contents and names | Yes; text Claude reads through tools appears in the transcript, subject to the same truncation. File names appear in tool-call inputs and outputs |
| Artifacts | Yes; generated content appears inside tool-call inputs |
| Skills | Yes; skill content appears when the client sends it as message content |
| Session metadata | Owner (`user.id` and email address), organization, workspace, `product_surface` and `created_at` |

And what is **not** in it, which the video is careful not to overstate: thinking blocks,
tool definitions, token usage, cost and latency, and host or device metadata such as
terminal type and workspace paths. Images, PDFs and other binary content appear only as
placeholder `text` blocks; raw file bytes are never returned.

- https://platform.claude.com/docs/en/manage-claude/compliance-faq

## Retention

**Six years by default.** Beat 018 puts this figure on screen. For local sessions, the
retention row reads "6 years by default, or your organization's custom conversation
retention period, when a finite one is set; held by Anthropic". The Activity Feed
separately retains 6 years of organization activity.

- https://platform.claude.com/docs/en/manage-claude/compliance-faq

## The boundaries, which beat 033 states

**Capture happens at the API, not on the device.** "Local sessions are captured as their
requests reach the Claude API, so nothing is installed on the device, and on-device
activity that never reaches the API is not captured."

This matters, and the video says it: the mechanism is not an agent watching a machine.

**What is not captured at all:**

- Claude Code sessions authenticated with a Claude Console API key
- Claude Code sessions run through Amazon Bedrock, Google Cloud or Microsoft Foundry
- Claude Code on the web
- Any local session data at all, for organizations with HIPAA readiness enabled
- Sessions for which zero data retention is in effect

Organizations using customer-managed encryption keys see local session metadata but no
transcript content.

- https://platform.claude.com/docs/en/manage-claude/compliance-faq

## Comparison the video gestures at

The video says a company can already govern its other tools. The documentation makes the
narrower, checkable version of that point itself, comparing the Compliance API with
OpenTelemetry logging: OTEL streams per-event telemetry to a collector the organization
runs, while the Compliance API returns retained per-session transcripts from Anthropic on
request.

- https://platform.claude.com/docs/en/manage-claude/compliance-faq
- https://code.claude.com/docs/en/monitoring-usage

## Not checked

- **That banks, healthcare companies and government contractors "need records".** The
  video states this as a general fact about regulated industries. It is uncontroversial
  and it is not traced here to any specific regulation, because no specific one is named
  on screen or in the narration.
- **That developers will route around a badly rolled out tool**, and the downstream claims
  about personal accounts and pasting into web chats. This is the video's argument about
  likely behaviour, not a measured finding, and no study is cited for it.
- **The governance status of Slack, Microsoft 365, Google Workspace, GitHub and email**
  inside any particular company. The video uses these as familiar examples of tools whose
  workplace status a developer already assumes; the specifics vary by organization and
  none is sourced.
- **Whether any given employer has enabled the Compliance API.** Enablement is per
  organization, and nothing here establishes how widely it has been turned on.
