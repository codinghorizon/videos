---
layout: default
title: "Your AI Coding Bill Is Mostly Files That Did Not Matter"
permalink: /your-ai-agent-is-burning-tokens-on-the-wrong-files/
date: 2026-08-14
---

# Your AI Coding Bill Is Mostly Files That Did Not Matter

Every claim the video makes about how coding agents spend tokens, chased to a primary
source. Checked 14 August 2026.

The video's numbered examples — three candidate files, a five file budget, twenty
unrelated files, thirty files for a one component bug, ten minutes of reading — are the
video's own worked instructions and illustrations rather than measurements of anything.
They are listed under **Not checked** below.

Because the shots draw several of them as concrete meters and counts, which is how an
illustration starts looking like data, the ones that could be misread as measured now
carry the words "an example, not a measurement" on screen: the ten minute timeline, the
thirty file field, the twenty file trace, and the narrowing search field. The five file
budget does not, because it is a rule the script prescribes rather than a figure it
reports.

---

## Reading a file costs money, because input tokens are billed

The whole argument rests on the fact that what an agent *reads* is charged, not only what
it writes. Anthropic's published pricing is per million tokens and is split into input and
output, with input billed on every request that carries it.

- Claude Sonnet 5 is $2 per million input tokens and $10 per million output tokens.
- Claude Opus 5 starts at $5 per million input tokens and $25 per million output tokens.
- Claude Haiku 4.5 starts at $1 per million input tokens and $5 per million output tokens.

Source: Anthropic, *Pricing* — https://platform.claude.com/docs/en/about-claude/pricing

**This is the one price that appears on screen**, twice: once early, beside the file rows
whose cost bars are growing, and once beside the search results being weighed against
whole files. It is the Sonnet 5 input rate, $2 per million, and it is labelled as such and
carries the source. Nothing else in the video states a price.

Prompt caching changes the arithmetic but not the direction: a cache write costs 1.25x the
base input price on the five minute cache and 2x on the one hour cache, and a cache read
costs 0.1x. Re-reading the same large file in a way that misses the cache is charged at the
full input rate.

Source: Anthropic, *Prompt caching* — https://platform.claude.com/docs/en/build-with-claude/prompt-caching

## Old conversation is dragged into every new request

The video says every request carries the ones before it. That is a property of the API
rather than a habit of any particular tool: the Messages API holds no conversation state
server side, so the client resends the whole thread each turn.

> "The Messages API is stateless, which means that you always send the full conversational
> history to the API."

Source: Anthropic, *Using the Messages API* —
https://platform.claude.com/docs/en/build-with-claude/working-with-messages

## The model's own output is fed back in as input

The same mechanism covers the beat about generated text being fed back into the model. The
assistant's previous turns are ordinary entries in the `messages` array on the next
request, so text the model produced is billed as input the next time round, and again on
every turn after that. The `usage` object on each response reports `input_tokens` and
`output_tokens` separately, and the input count grows with the thread.

Source: Anthropic, *Using the Messages API* —
https://platform.claude.com/docs/en/build-with-claude/working-with-messages

## More context is not always more intelligence

The video's closing argument, that extra context can be extra ways to be distracted rather
than extra capability, is Anthropic's own published position on building agents.

> "Context, therefore, must be treated as a finite resource with diminishing marginal
> returns."

> "LLMs have an 'attention budget' that they draw on when parsing large volumes of
> context."

The same piece names the degradation directly: as the number of tokens in the context
window increases, the model's ability to accurately recall information from that context
decreases, a phenomenon it calls context rot, and it reports this emerging across models.

It also recommends the retrieval habit the video argues for, in the same terms: rather than
loading everything up front, agents should maintain lightweight identifiers such as file
paths and use them to load data into context at runtime.

Source: Anthropic, *Effective context engineering for AI agents* —
https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents

## Where information sits in a long context changes whether it is used

Underneath that is a measured result rather than a vendor position. Liu et al. tested
multi document question answering and key value retrieval and found a U shaped curve:
performance is highest when the relevant information is at the very start or the very end
of the input, and drops when the model has to reach for something in the middle, including
on models built for long contexts.

Source: Liu, Lin, Hewitt, Paranjape, Bevilacqua, Petroni, Liang, *Lost in the Middle: How
Language Models Use Long Contexts*, Transactions of the ACL, 2024 —
https://aclanthology.org/2024.tacl-1.9/ (preprint: https://arxiv.org/abs/2307.03172)

## Telling an agent what not to read is a real control, not just a request

The video's second fix is to name the directories the agent must not open. In Claude Code
this is enforced by the tool layer rather than left to the model's discretion: permission
rules take deny entries for reads, and a read deny rule also blocks the edit and write
tools on the paths it matches. Rules accept wildcards and project relative or absolute
paths.

Source: Anthropic, *Claude Code settings* — https://docs.claude.com/en/docs/claude-code/settings

## A project note that says where things live

The video's last fix is a short file that tells the agent where the entry points are and
what is deprecated. Claude Code reads a `CLAUDE.md` in the project as standing instructions
for that repository, which is the mechanism the video is describing.

Source: Anthropic, *Claude Code settings* — https://docs.claude.com/en/docs/claude-code/settings

---

## Not checked

- The file counts and durations used as examples throughout — three candidate files, a five
  file budget, twenty unrelated files, thirty files for a one component bug, ten minutes
  spent reading before the first useful line. These are the video's own illustrations of a
  habit, not figures drawn from a study or a measured run, and nothing on screen presents
  them as data.
- The claim that a clean file access path usually produces a cleaner patch, and a confused
  path a confused one. This is stated as the experience the video is arguing from. No
  published study measuring patch quality against file access patterns was found.
- The claim that a single short project note can save more tokens than switching providers.
  Directionally consistent with the context engineering guidance above, but no benchmark
  comparing the two was found, and none is cited on screen.
- The specific example repository, file names and bug used in the shots are constructed for
  the video. They are not taken from a real project.
