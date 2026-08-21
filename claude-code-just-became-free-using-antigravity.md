---
layout: default
title: "Stop Paying Claude Code Prices Use Antigravity Now"
permalink: /claude-code-just-became-free-using-antigravity/
date: 2026-08-21
---

# Stop Paying Claude Code Prices Use Antigravity Now

{% raw %}
Sources for every figure, price, quote and product claim this video puts on screen.
Checked 2026-08-21.

## Google Antigravity, the free individual plan

The plan is listed publicly as **Individual, $0/month**. The same plan card lists
**Unlimited Tab completions**, **Unlimited Command requests**, and **Basic weekly rate
limits**.

Agent model access on that free plan is listed as **Gemini 3.5 Flash, Gemini 3.1 Pro,
Gemini 3 Flash, Claude Sonnet & Opus 4.6, gpt-oss-120b**. That is the source for the
claim that the model list holds Gemini, Claude and GPT OSS, and for the claim that
Claude is in the free tier rather than only in a paid one.

Source: https://antigravity.google/pricing

## The rate limits, and the capacity wording

The plans documentation describes the free tier as **"Meaningful quota, refreshed
weekly"** with a **"Weekly rate limit"**, against Google AI Pro's **"High, generous
quota, refreshed every five hours until weekly limit reached"** and Google AI Ultra's
**"The highest, most generous quota, refreshed every five hours"** plus **"Access to
third-party models"**.

The capacity line the video quotes is verbatim from the same page:

> The baseline rate limits are primarily determined to the degree we have capacity, and
> exist to prevent abuse.

The page also states that usage limits are subject to modification to manage system
capacity, and that additional credits can be purchased by Pro and Ultra subscribers but
not on the free plan. That is the basis for the video saying the higher plans get more
generous limits and credit pools while the free plan does not.

Source: https://antigravity.google/docs/plans

## The two surfaces, and the artifacts

Antigravity is described as having two surfaces rather than a chat sidebar: an **Editor
View**, with tab completions, inline commands and an agent in the side panel, and an
**Agent Manager**, an agent-first surface for spawning and overseeing several agents
across workspaces at once.

The artifact types named in the launch post are **task lists, implementation plans,
walkthroughs, screenshots and browser recordings**. The video names task lists,
implementation plans, screenshots and browser recordings, all four of which appear on
that list.

A browser recording is documented as a step-by-step recording of the agent working
through a UI, which the developer watches to verify the result rather than running the
app themselves. That is the basis for the video's claim about moving the review surface
from logs to artifacts.

Sources:
- https://antigravity.google/blog/introducing-google-antigravity
- https://antigravity.google/docs/artifacts
- https://antigravity.google/docs/ide/browser-recordings/

## The Claude price ladder

The three figures the video reads out as the prices developers have been trained to
accept are Anthropic's own consumer tiers:

| Plan | Price | Claude Code |
| --- | --- | --- |
| Free | $0 | not included |
| Pro | $20/month billed monthly ($17/month billed annually) | included |
| Max 5x | $100/month | included |
| Max 20x | $200/month | included |

Claude Code is listed as a Pro feature and above, and is not part of the free Claude
tier. That is what makes the comparison in this video a real one: the terminal product
has no free tier of its own.

Source: https://claude.com/pricing

## What is deliberately not claimed

The video is explicit that Anthropic's Claude Code did not itself become free, and that
what changed is that Claude models are reachable inside a free Google workspace. Nothing
here supports a stronger claim than that, and the script does not make one.

## Not verified

- **How the free tier's weekly quota behaves in practice.** Google publishes the shape
  of the limit ("meaningful quota, refreshed weekly") and says it is set to the degree
  they have capacity, but publishes no number of prompts, tokens or agent runs. The
  video therefore says limits exist and are real without putting a figure on screen.
- **Whether the free plan's model list stays as published.** The same documentation says
  usage limits are subject to modification, and the model list has already changed once
  since launch, when it was Claude Sonnet 4.5 rather than Sonnet and Opus 4.6.
{% endraw %}
