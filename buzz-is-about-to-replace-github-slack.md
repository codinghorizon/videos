---
layout: default
title: "Buzz Wants To Replace Slack And GitHub Completely"
permalink: /buzz-is-about-to-replace-github-slack/
date: 2026-08-06
---

# Buzz Wants To Replace Slack And GitHub Completely

Every figure, name, version and limit the finished picture puts on screen, with the primary
source it was taken from. Checked 6 August 2026.

Where the source is the Buzz repository, the file is named: the repository is the thing
being described, so its own documentation is the primary record for how it is built.

---

## The release

**Buzz is published by Block, Inc. under the Apache 2.0 licence.** The repository is
`github.com/block/buzz`. Its metadata gives the licence as `Apache-2.0`, the owner as the
`block` organisation and the primary language as Rust, and it describes itself as "A hive
mind communication platform".
Source: https://github.com/block/buzz

**Released 21 July 2026.** The first published release, `v0.4.21`, is tagged that day.
Source: https://github.com/block/buzz/releases

**22.9k stars.** The repository record returned 22,961 stargazers and 2,596 forks when
read. A star count moves constantly and is stated on screen as a rounded figure.
Source: GitHub REST API record for `block/buzz`.

**Current version v0.5.5.** The most recent published release is `desktop-v0.5.5`. The
first was `v0.4.21` on 21 July, so the project moved across roughly a dozen releases in
its first fortnight, which is the point the maturity bar on screen is making.
Source: https://github.com/block/buzz/releases

---

## What ships, and what does not

The three states shown on the status shots are the project's own. Its README divides
features into "Works today", "Being wired up" and "Strong opinions, pending code".

- Works today: relay, channels, threads, DMs, canvases, media, search, audit log; the
  desktop app (Tauri and React); `buzz-cli` and the ACP harness (Goose, Codex, Claude
  Code); YAML workflows; git events (NIP-34); the git hosting backend.
- Being wired up: mobile clients (iOS and Android, Flutter); workflow approval gates;
  huddle lifecycle events.
- Pending code: web-of-trust reputation; push notifications; culture features.

Source: https://github.com/block/buzz/blob/main/README.md

---

## The identity model

**Buzz is a Nostr relay and every action is a signed event.** The architecture document
states it is built on Nostr using the NIP-01 wire format, and that every action, "a chat
message, a reaction, a workflow step, a canvas update, a huddle event", is a
cryptographically signed Nostr event identified by a `kind` integer.
Source: https://github.com/block/buzz/blob/main/ARCHITECTURE.md

**The kind numbers on screen.** 40002 stream message v2, 40003 stream message edit, 45001
forum thread root, and 46001 to 46012 for workflow execution events. NIP-34 patches are
kind 1617.
Source: ARCHITECTURE.md event kind table, and NIP-34.

**Agents hold their own keypairs.** The README states agents have "the same surface area
as humans, with their own keys and their own audit trail", and the architecture document
opens by saying AI agents and humans are first-class equals. That is what the notch on
screen stands for: the same event, signed by a different key.
Source: README.md and ARCHITECTURE.md.

**The agents named.** The ACP harness is listed as working with Goose, Codex and Claude
Code.
Source: README.md.

**Storage.** Events are stored in Postgres, Redis carries pub/sub and presence, and media
goes to S3 or MinIO.
Source: ARCHITECTURE.md.

---

## The git side

**Git hosting is served over git smart HTTP by the relay**, which exposes
`/git/{owner}/{repo}/info/refs`, `git-upload-pack` and `git-receive-pack`.
Source: ARCHITECTURE.md, HTTP endpoint table.

**Git events are Nostr events under NIP-34**, covering patches, repo announcements and
status. The README describes opening a feature branch causing a channel to appear, with
patches landing as NIP-34 events and the merge decision landing in the same room as the
evidence.
Source: README.md.

---

## What the seat comparison uses

**GitHub Team is $4 per user per month and GitHub Enterprise starts at $21**, both shown
on GitHub's pricing page marked as the rate for the first 12 months.
Source: https://github.com/pricing

**Slack Pro is $7.25 per user per month billed annually.** US list price.
Source: https://slack.com/pricing

**The $11.25 and $6,750 figures.** Slack Pro at $7.25 plus GitHub Team at $4 is $11.25 per
user per month. Fifty seats across twelve months is $6,750. It is a first year figure
because GitHub's $4 rate is a first-12-months rate, and it is arithmetic on two list
prices rather than a quote for any particular team.

---

## Running it yourself

**Toolchain.** Docker and Hermit, or Rust 1.88+, Node 24+, pnpm 10+ and `just`.
Source: README.md, getting started.

---

## What is not finished

**Rate limiting is not enforced.** The `RateLimiter` trait exists in `buzz-auth`, but the
only implementation is `AlwaysAllowRateLimiter`, a test stub behind a test feature flag.
`RateLimitConfig` defines four tiers as a design target and none are enforced. No
Redis-backed rate limiter exists in the codebase.
Source: ARCHITECTURE.md, known gaps table.

**Workflow approval gates are not wired end to end.** The executor returns
`StepResult::Suspended` and the relay has grant and deny endpoints with database CRUD, but
the engine intercepts before creating the waiting rows, so runs that hit an approval gate
are marked as failed.
Source: ARCHITECTURE.md, known gaps table.

**Two workflow actions are stubbed.** `send_dm` and `set_channel_topic` are in the schema
but return `NotImplemented`, so a run that reaches either fails at execution.
Source: ARCHITECTURE.md, known gaps table.

**Mobile clients are in progress.** iOS and Android, built in Flutter, sit in the README's
"being wired up" column.
Source: README.md.

---

## Caveats

- The star count and the version number are live figures and will be out of date quickly.
- Slack's pricing page serves prices in the currency of the region it is requested from
  and returned pounds when checked, so the dollar figures used are Slack's US list prices
  for annual billing.
- GitHub's $4 and $21 rates are both marked on GitHub's own pricing page as first twelve
  months rates. What they become afterwards is not published.
- Seat pricing at both vendors is commonly negotiated below list at volume, so the fifty
  seat figure is a list price comparison rather than what a given team pays.
- Feature status is taken from the project's own README and architecture document. None of
  it is an independent test of whether a feature marked as working does work.
