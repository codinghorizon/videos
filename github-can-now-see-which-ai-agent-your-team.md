---
layout: default
title: "GitHub Just Made The AI Coding War Impossible To Fake"
permalink: /github-can-now-see-which-ai-agent-your-team/
date: 2026-08-13
---

# GitHub Just Made The AI Coding War Impossible To Fake

Every figure, field name and capability the finished picture puts on screen, chased to a
primary source. GitHub's own documentation and changelog are the primary sources for what
the metrics report; where a claim could not be found stated there, it is listed under
**Not checked** rather than drawn.

## Copilot usage metrics exist at organization and enterprise level

Copilot usage metrics reached general availability on **27 February 2026**, after a public
preview that opened in October 2025. The offering covers a usage dashboard (code completion
activity, IDE usage, model and language breakdown) and a code generation dashboard (lines
suggested, added and deleted), at **enterprise and organization granularity**, through both
dashboards and APIs.

- https://github.blog/changelog/2026-02-27-copilot-metrics-is-now-generally-available/
- https://github.com/orgs/community/discussions/177273

## Active users

The dashboard reports **IDE daily active users**, "unique users who interacted with Copilot
each day", and **IDE weekly active users**, "unique users active over a 7-day rolling
window". It also reports a **code completions acceptance rate**, "percentage of suggestions
accepted".

- https://docs.github.com/en/copilot/reference/copilot-usage-metrics/interpret-copilot-metrics

## Chat modes: ask, edit, plan and agent

**Requests per chat mode** breaks interactions down by mode: **Ask, Edit, Plan or Agent**.
In the underlying data these appear in `totals_by_model_feature` as `chat_panel_ask_mode`,
`chat_panel_edit_mode`, `chat_panel_plan_mode` and `chat_panel_agent_mode`.

- https://docs.github.com/en/copilot/reference/copilot-usage-metrics/interpret-copilot-metrics
- https://docs.github.com/en/copilot/reference/copilot-usage-metrics/copilot-usage-metrics

## Model usage, and model usage per chat mode

**Model usage per day** "shows which AI models power Copilot Chat activity", and **model
usage per chat mode** "breaks down model usage by chat mode (Ask, Edit, Plan, Agent)". The
`model` dimension carries specific model identifiers plus `auto`, `unknown` and `others`.

One limit, stated by GitHub itself: model usage charts "currently represent chat activity
only. Completions data is not included in model breakdowns." So model usage is not a
complete picture of which model wrote the code that landed.

- https://docs.github.com/en/copilot/reference/copilot-usage-metrics/interpret-copilot-metrics
- https://docs.github.com/en/copilot/reference/copilot-usage-metrics/copilot-usage-metrics

## Code generation, accepted code, lines added and lines deleted

Lines of code metrics quantify "the lines it suggested, added, or deleted across
completions, chat, and agent features". The fields are:

| Field | What it holds |
| --- | --- |
| `loc_suggested_to_add_sum` | Lines of code Copilot suggested to add |
| `loc_suggested_to_delete_sum` | Lines of code Copilot suggested to delete |
| `loc_added_sum` | Lines of code actually added to the editor |
| `loc_deleted_sum` | Lines of code deleted from the editor |

- https://docs.github.com/en/copilot/reference/copilot-usage-metrics/lines-of-code-metrics

## Agent activity is measured differently from completions

Agent work is not counted the same way, and GitHub says why: "Copilot agent does not follow
a 'suggest then accept' flow." Agents plan and execute multi-step tasks, editing multiple
files without an explicit acceptance.

So agent file edits are counted as `loc_added_sum` and `loc_deleted_sum` under the
`agent_edit` feature bucket, and are **not** included in the suggested metrics. On a
multi-file operation, "each file edit contributes to total added and deleted lines, even if
triggered by one prompt".

The dashboard separately reports **agent adoption**, "percentage of active users who used
Copilot agent".

- https://docs.github.com/en/copilot/reference/copilot-usage-metrics/lines-of-code-metrics
- https://docs.github.com/en/copilot/reference/copilot-usage-metrics/interpret-copilot-metrics

## The surfaces: IDE chat, IDE agent, code review, CLI and cloud agent

Each surface is a distinct per-user field:

| Field | What it holds |
| --- | --- |
| `used_chat` | Whether the user used IDE chat that day |
| `used_agent` | Whether the user used agent mode in the IDE that day. Does not include Copilot code review activity |
| `used_cli` | Whether the user used Copilot CLI that day |
| `used_copilot_cloud_agent` | Whether the user used Copilot cloud agent that day (`used_copilot_coding_agent` is retained for backward compatibility) |
| `used_copilot_code_review_active` | Whether the user actively engaged with Copilot code review that day |
| `used_copilot_code_review_passive` | Whether the user had Copilot automatically assigned to review their pull request that day, without actively engaging |

`used_agent` and `used_copilot_cloud_agent` being separate fields is what makes IDE agent
mode distinguishable from cloud agent activity.

- https://docs.github.com/en/copilot/reference/copilot-usage-metrics/copilot-usage-metrics

## Activity attributed to individual users

User-level reporting is explicit: "User-level: Analyze individual Copilot usage for a
specific day to support enablement and identify where teams may need training or better
documentation." Per-user data is available as NDJSON downloads and through REST API
endpoints, and on 28 July 2026 individual Copilot app activity was also "attributed to users
in the enterprise-user and organization-user reports".

- https://github.blog/changelog/2026-02-27-copilot-metrics-is-now-generally-available/
- https://github.com/orgs/community/discussions/177273
- https://github.blog/changelog/2026-07-28-github-copilot-app-usage-metrics-now-expand-across-report-rollups/

## Surfaces are compared against each other

The July 2026 rollup expansion states that Copilot app coding activity "is now broken out in
the feature, model, and language rollups alongside every other Copilot surface", so a team
can "compare the Copilot app against the IDE, chat, code review, and coding agent surfaces
using the same fields you already consume".

- https://github.blog/changelog/2026-07-28-github-copilot-app-usage-metrics-now-expand-across-report-rollups/

## Code review and pull request activity

The code review surface covers pull request creation, review, merge and suggestion activity,
including activity performed by Copilot cloud agent and Copilot code review. This is what
connects Copilot activity to the delivery artifacts a team already uses: pull requests,
reviews and checks.

- https://docs.github.com/en/copilot/reference/copilot-usage-metrics/copilot-usage-metrics

## Pull requests merged per user, as an outcome measure

GitHub does publish one measure that reaches past adoption toward impact: an **adoption
multiplier**, which compares engaged against passive users on "pull requests merged per user
per month" and on time to merge pull requests. It is the closest thing in the dashboard to
an outcome rather than an activity count.

- https://docs.github.com/en/copilot/reference/copilot-usage-metrics/interpret-copilot-metrics

## Not checked

- **"Agent contribution as a share of lines changed" is not a named chart or field.** What
  GitHub documents is `loc_added_sum` and `loc_deleted_sum` under the `agent_edit` feature
  bucket, and a separate agent adoption percentage of active users. A share of lines changed
  is derivable from those totals, but GitHub does not publish it as a reported figure, so
  the picture shows the documented fields rather than a share statistic.
- **"Alice used agents 400 times this month. Bob only used them twice."** This is an
  invented example illustrating what a per-user ranking would look like, not a figure from
  any organization's data. It is marked as illustrative on screen.
- **"20 minutes"** as the length of time a tool has to impress a developer is a rhetorical
  figure, not a measured retention window, and no source is claimed for it.
- **Whether measurement changes developer or vendor behaviour** is an argument about what
  follows from these metrics existing, not a documented effect. No study is cited for it and
  none is implied on screen.
- **The competitive claims about specific tools** (which is more integrated, which feels
  smarter, which is catching up) are the opinions the video opens by describing. They are
  drawn as opinions, unmeasured and unattributed, which is the point being made about them.
