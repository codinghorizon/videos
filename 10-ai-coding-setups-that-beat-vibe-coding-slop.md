---
layout: default
title: "10 Things Separate Real AI Coding From Vibe Slop"
permalink: /10-ai-coding-setups-that-beat-vibe-coding-slop/
date: 2026-08-15
---

# 10 Things Separate Real AI Coding From Vibe Slop

Everything this video states as fact, chased to a primary source. The video makes no
statistical claims, so what needed checking is the other kind: that each of the ten setups
describes something that actually exists and works the way it is described, and that every
command, config key and figure the shots put on screen is real.

Anything a shot draws that is illustrative rather than factual is listed under
**Illustrative, not claimed** at the bottom, so it is clear which is which.


## The ten setups

### 10. Start with a failing test

The video says the agent can be pointed at one failing test and told to make it pass
without breaking the others, and that it should run the smallest relevant test command
rather than the whole suite.

Vitest documents filtering a run down to a single file, a single test name, or a single
line:

> `vitest basic/foo.test.ts:10` — "Vitest will run the test that contains line 10. This
> requires the full filename (relative or absolute)."

and recommends the narrow form explicitly: "always pass a file path alongside your filter
so Vitest only loads the files you care about."

- Vitest, Filtering — https://vitest.dev/guide/filtering


### 9. Make it write the spec first

The claim here is procedural rather than technical: that agreeing a short spec before any
file changes moves the uncertain part of a task into the open. The mechanism the video
draws — a written procedure the agent produces and a human approves before code is
written — is the same one the tooling documents under skills and project instructions,
below.


### 8. One agent builds, one agent reviews

The video says this can be done with two different models, two agent sessions, or one tool
with a review mode. All three exist. Claude Code ships a bundled `/code-review` skill, and
sub-agents can be run with their own tool sets and their own system prompts, which is what
makes the reviewer a genuinely separate job rather than the same session being asked twice.

- Claude Code, commands reference — https://code.claude.com/docs/en/commands
- Claude Code, skills (bundled skills including `/code-review`) — https://code.claude.com/docs/en/skills


### 7. Send a cheap model in as a scout

The video says a workflow can use a cheaper or local model for exploration and hand the
decision to a stronger one, and that this needs a setup that lets you switch model
providers. Claude Code documents third-party inference through Amazon Bedrock, Google
Cloud's Agent Platform and Microsoft Foundry, selected by environment variable, as well as
routing through a gateway or proxy:

> "Cloud provider credentials, when `CLAUDE_CODE_USE_BEDROCK`, `CLAUDE_CODE_USE_VERTEX`, or
> `CLAUDE_CODE_USE_FOUNDRY` is set."

- Claude Code, authentication and provider selection — https://code.claude.com/docs/en/iam
- Claude Code, LLM gateway — https://code.claude.com/docs/en/llm-gateway


### 6. Lock the commands it can run

This is the setup the video describes most concretely, and it is a real configuration
surface. Permissions are expressed as `allow`, `ask` and `deny` rules, with `allow`
running without a prompt, `ask` prompting first and `deny` blocking entirely. Bash rules
take the form `Bash(command pattern)` and support `*`:

```json
{
  "permissions": {
    "allow": ["Bash(npm run lint)", "Bash(npm run test *)", "Read(~/.zshrc)"],
    "deny":  ["Bash(curl *)", "Read(./.env)", "Read(./.env.*)", "Read(./secrets/**)"]
  }
}
```

So "run tests, run type checks, run formatting, allow, and never run destructive database
commands" is not a metaphor for a policy: it is the shape of the file.

- Claude Code, settings and permissions — https://code.claude.com/docs/en/settings

The video also says agents can now connect to browsers, terminals, cloud environments,
GitHub, Slack, Gmail, calendars and MCP servers, and that every connection is a
capability and every capability a risk. MCP is the open protocol those connections are
made over. Servers expose three primitives:

> "**Resources**: Context and data ... **Prompts**: Templated messages and workflows for
> users ... **Tools**: Functions for the AI model to execute"

and the specification is explicit that tools are arbitrary code execution and need consent:

> "Tools represent arbitrary code execution and must be treated with appropriate caution."
> "Hosts must obtain explicit user consent before invoking any tool."

Pre-built servers exist for Google Drive, Slack, GitHub, Git, Postgres and Puppeteer among
others, which is where the specific list in the video comes from.

- Model Context Protocol, specification 2025-06-18 — https://modelcontextprotocol.io/specification/2025-06-18
- Anthropic, Introducing the Model Context Protocol — https://www.anthropic.com/news/model-context-protocol


### 5. Give every agent its own worktree

The video says a worktree setup gives each agent its own copy of the repo on its own
branch, and that this is what stops parallel agents editing the same files. That is what
the feature is:

> "A git repository can support multiple working trees, allowing you to check out more than
> one branch at a time. With `git worktree add` a new working tree is associated with the
> repository, along with additional metadata that differentiates that working tree from
> others in the same repository."

> "The new worktree is linked to the current repository, sharing everything except
> per-worktree files such as `HEAD`, `index`, etc."

The isolation is enforced rather than conventional. Git refuses by default to check the
same branch out twice:

> "By default, `add` refuses to create a new worktree when *<commit-ish>* is a branch name
> and is already checked out by another worktree"

The syntax on screen, `git worktree add <path> <branch>`, is the documented form
(`git worktree add [<options>] <path> [<commit-ish>]`).

- Git, git-worktree — https://git-scm.com/docs/git-worktree


### 4. Turn your procedures into tools

The video says repeated instructions should become reusable docs, skills, commands or
project instructions that the agent pulls when the task needs them, and warns against one
giant instruction document. The documentation makes both halves of that argument in its own
words:

> "Create a skill when you keep pasting the same instructions, checklist, or multi-step
> procedure into chat, or when a section of CLAUDE.md has grown into a procedure rather than
> a fact."

> "Unlike CLAUDE.md content, a skill's body loads only when it's used, so long reference
> material costs almost nothing until you need it."

That last sentence is the mechanism behind "the right instruction at the right time beats a
huge instruction all the time": a procedure held behind a trigger costs context only when it
fires, whereas one large always-loaded document costs it on every turn.

- Claude Code, skills — https://code.claude.com/docs/en/skills


### 3. Make it look at what it built

The video says agents are getting better at using browsers, screenshots and computer
control, and that a verification setup runs the app, opens the page, screenshots it, checks
viewport widths, interacts, and confirms the visible result.

The computer use tool provides exactly that: "screenshot capabilities and mouse/keyboard
control for autonomous desktop interaction", with screenshot capture described as "See
what's currently displayed on screen". It is a beta feature behind the
`computer-use-2025-11-24` beta header on current models.

Browser-specific tooling does the same job through the browser rather than the desktop. The
official Chrome DevTools MCP server "lets your coding agent control and inspect a live
Chrome browser for automation, debugging, and performance analysis", including
`take_screenshot`, `take_snapshot`, and changing viewport dimensions to test responsive
layouts. Playwright's MCP server likewise captures screenshots and resizes the viewport at
runtime.

The three widths on screen are Tailwind's own documented default breakpoints — `sm` 640px,
`md` 768px, `lg` 1024px — rather than numbers picked for the shot.

- Anthropic, Computer use tool — https://platform.claude.com/docs/en/agents-and-tools/tool-use/computer-use-tool
- Chrome DevTools MCP — https://github.com/ChromeDevTools/chrome-devtools-mcp
- Tailwind CSS, Responsive design — https://tailwindcss.com/docs/responsive-design


### 2. Dependencies have to ask first

The video says an agent must use existing code unless it asks, and that a package has to be
justified on what problem it solves, whether one is already installed, its licence, its
size, whether it is maintained, whether it runs in the environment, and whether it creates a
security or supply chain concern.

The enforcement half of this is the same permissions surface as setup six: an install
command can be moved from `allow` to `ask`, so the agent stops and requests approval rather
than adding a dependency mid-task.

- Claude Code, settings and permissions — https://code.claude.com/docs/en/settings


### 1. Shape every task like a pull request

The video says the best setup makes every task look like a good pull request: small scope,
clear reason, limited files, tests included, checks run, risk explained, and no surprise
dependencies, unrelated cleanup or mystery refactors. The shape being described is the
ordinary GitHub review surface — a branch, a pull request with a description, review, status
checks and a merge — and the argument is that aligning the agent's output with it is what
makes the change reviewable.

- GitHub, About pull requests — https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests


## Illustrative, not claimed

These appear on screen inside depicted editors, terminals and diagrams. They are set
dressing showing what a surface looks like, not figures about the world, and none of them
is asserted by the narration.

- The failing assertion, the passing and failing test counts, and the diff line counts shown
  inside the mock editor and terminal.
- The duplicate component filenames, the decorative auth function and the empty tests
  directory in the opening.
- The search hit count in the scout chapter's terminal.
- The dependency graph sizes in the chapter on packages.
- The named tools appearing as marks in the connections shot are the real products the
  script names; the diagram of what connects to what is illustrative.


## Not checked

- The video's central claim — that these ten setups produce better results than
  unstructured prompting — is an argument from how the mechanisms work, not a measured
  finding. No controlled comparison is cited and none is claimed.
- "Many AI coding disasters are actually planning disasters" is offered as an explanation
  rather than as a measured breakdown of failure causes.
- "AI agents love adding packages" and "often it is laziness" describe a commonly reported
  tendency; no study is cited for how often it happens.
