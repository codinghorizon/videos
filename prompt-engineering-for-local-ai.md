---
layout: default
title: "Local AI Prompts: The Mistake Making Models Dumb"
permalink: /prompt-engineering-for-local-ai/
date: 2026-08-17
---

# Local AI Prompts: The Mistake Making Models Dumb

{% raw %}
Every figure, name, command and behavioural claim the finished shots put on screen, chased
to a primary source. Worked from the `TEXT:` lines in BEATS.md.

This video is a technique piece rather than a news piece, so it asserts very few numbers.
That is deliberate and it is also why this file is short: where the picture originally drew
a figure the script never claims, the figure was taken off the screen rather than sourced
after the fact. What is left below is either a verifiable fact about a real tool, a
published research finding the script's argument rests on, or a rhetorical figure the
narration itself supplies.

## Tools and commands shown on screen

**Ollama, and the three commands in beat 020.**
`ollama pull qwen3:8b` and `ollama run qwen3:8b` are the documented commands for the Qwen3
8B model in Ollama's own library, and `qwen3:8b` is a real published tag.
- https://ollama.com/library/qwen3:8b
- https://ollama.com/library/qwen3:8b-q4_K_M

**Q4_K_M, shown on the model die in beats 002, 006 and 009.**
A real GGUF quantisation type, not an invented label. Ollama publishes `qwen3:8b-q4_K_M`
with quantisation `Q4_K_M`, 8.19B parameters and a 5.2GB download, which is what the shots
mean by a small model that has been quantised hard.
- https://ollama.com/library/qwen3:8b-q4_K_M

**LM Studio, named in beat 002.** A real local model runner, and one of the two the script
names by name. Its mark is drawn from the simple-icons geometry the channel's logo kit
carries, not approximated.
- https://lmstudio.ai/

**ChatGPT has no mark on screen, and that is on purpose.** simple-icons no longer ships an
`openai` icon, and `scripts/gen-short-logos.mjs` reports it as unavailable. Rather than
approximate a logo this audience knows by sight, beat 002 sets ChatGPT as type and gives
the mark only to Claude, which the script also names.

**`ECONNREFUSED 127.0.0.1:5432` in the log window, beat 084.**
5432 is PostgreSQL's registered default port, so the log line reads as a real database
connection failure rather than a placeholder.
- https://www.postgresql.org/docs/current/runtime-config-connection.html

**`"zod": "^3.23.8"` in the package file, beat 149.** A real published version of zod.
- https://www.npmjs.com/package/zod

**`tsc --noEmit`, `vitest`, `rg`, `npm test`, `git`, `glob`, `grep`** — all real commands,
used in the shots exactly as they behave.

## Research the script's argument rests on

**"A smaller context model may simply lose the middle" (beats 084 and 086).**
This is a documented finding, not a folk claim. Liu et al. measured model performance as
the position of the relevant information moved through the input context and found
performance is highest when it sits at the beginning or the end and degrades significantly
when the model has to use information in the middle of a long context — including on models
explicitly built for long contexts.
- Nelson F. Liu, Kevin Lin, John Hewitt, Ashwin Paranjape, Michele Bevilacqua, Fabio
  Petroni, Percy Liang, "Lost in the Middle: How Language Models Use Long Contexts",
  *Transactions of the Association for Computational Linguistics*, vol. 12 (2024),
  pp. 157–173. https://aclanthology.org/2024.tacl-1.9/ · https://arxiv.org/abs/2307.03172

**"It follows the most recent sentence, not the most important one" (beats 028, 119, 120).**
The same paper's primacy and recency result covers the position effect, and Zhao et al.
separately identify a recency bias in which models favour answers appearing near the end of
the prompt.
- Liu et al. 2024, above.
- Zihao Zhao, Eric Wallace, Shi Feng, Dan Klein, Sameer Singh, "Calibrate Before Use:
  Improving Few-Shot Performance of Language Models", *Proceedings of the 38th
  International Conference on Machine Learning* (ICML 2021).
  https://proceedings.mlr.press/v139/zhao21c/zhao21c.pdf

**"It starts calling everything high severity because that is the pattern it sees"
(beats 072 and 073).** Zhao et al. name this majority label bias: the model is biased
toward answers that appear frequently in the prompt's examples. That is precisely the
failure the two beats draw, where three high-severity examples pull unrelated issues to
high.
- Zhao et al. 2021, above.

## Figures the narration itself supplies

**"900 word prompt template" (beat 013).** The script says this line, and the counter on
screen counts to the same figure. It is the writer's rhetorical figure for a bloated
template rather than a measurement of a specific published prompt, and the shot does not
present it as one.

## Not checked

- The demo repository in beats 033, 084, 096 and 141 (`214 files`, `38 route handlers`,
  the failing auth test, the patch) is a constructed scenario, not a real project. The
  commands and file shapes are real; the repository is not.
- The example configuration in beat 006 (`16 GB, no GPU`, `8k tokens`) is one plausible
  local setup offered as an example of what "what you actually have" means. It is not a
  measurement, and no specific machine is claimed.
- The script's central claims are matters of technique and judgement rather than fact:
  that smaller local models drift, accept impossible tasks, and pay uncertainty with
  invention; that pipelines beat single prompts locally; that contracts expose failure.
  These are the author's argument from practice. Where published research supports one, it
  is cited above; the rest are not the sort of claim a primary source settles.
{% endraw %}
