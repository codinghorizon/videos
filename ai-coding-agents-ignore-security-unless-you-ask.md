---
layout: default
title: "Your AI Coding Agent Is Quietly Skipping Security"
permalink: /ai-coding-agents-ignore-security-unless-you-ask/
date: 2026-08-13
---

# Your AI Coding Agent Is Quietly Skipping Security

Every figure and named claim the finished picture puts on screen, chased to a primary
source. Anything that could not be found is listed at the bottom rather than softened.

## The benchmark figure on screen

**61% of agent written solutions were functionally correct; 10.5% were secure.**

SWE-agent paired with Claude 4 Sonnet, measured on SUSVIBES, a benchmark of 200 feature
request software engineering tasks drawn from real open source projects, each chosen
because human programmers had produced a vulnerable implementation of it.

> "Although 61% of the solutions from SWE-Agent with Claude 4 Sonnet are functionally
> correct, only 10.5% are secure."

Songwen Zhao, Danqing Wang, Kexun Zhang, Jiaxuan Luo, Zhuo Li, Lei Li,
*Is Vibe Coding Safe? Benchmarking Vulnerability of Agent-Generated Code in Real-World
Tasks*, arXiv:2512.03262. https://arxiv.org/abs/2512.03262

The same paper reports that adding vulnerability hints to the feature request did not
mitigate the security problems it found. That is a real limit on how far a single added
sentence goes, and it is why the figure above is on screen and no figure for the SOC 2
result is.

## The gap between functional and secure code generation

The picture asserts, without a number, that models are further from secure code than they
are from working code, and that a green test suite does not speak to safety.

- Yanlin Wang et al., *RealSec-bench: A Benchmark for Evaluating Secure Code Generation in
  Real-World Repositories*, arXiv:2601.22706 (30 January 2026).
  https://arxiv.org/abs/2601.22706 — 105 instances across 19 CWE types, some with up to 34
  hop inter-procedural dependencies. Reports "the gap between functional and secure code
  generation in current LLMs", that retrieval augmented generation improves functional
  correctness while giving "negligible benefits to security", and that explicitly prompting
  models with **general** security guidelines "often leads to compilation failures, harming
  functional correctness without reliably preventing vulnerabilities".
- *SecCodeBench-V2 Technical Report*, arXiv:2602.15485. https://arxiv.org/abs/2602.15485 —
  98 generation and fix scenarios covering 22 CWE categories across five languages, used
  here only as corroboration that secure code generation is measured separately from
  functional correctness.

## The named compliance frameworks

SOC 2, HIPAA, PCI DSS and OWASP appear on screen as badges. They are named as examples of
requirements a team might already be held to, and no claim is made about any of them beyond
their existence, so nothing there needs a figure.

## The code on screen

Every code fragment in the video is written for the video to illustrate the failure being
described (account enumeration in a login response, an unscoped invoice lookup, a secret
written to a log line, an admin route with no role check). None of it is quoted from a real
codebase and none of it is attributed to one.

## Not checked

- **The SOC 2 style compliance experiment the video opens on.** The claim that Claude models
  asked to build applications meeting SOC 2 style security controls complied somewhere
  between roughly half the time and most of the time on a neutral prompt, and improved
  dramatically when the prompt named the requirement, could not be traced to a primary
  source. Anthropic's published research, their trust centre and arXiv were all searched.
  The picture therefore prints no figure for it: the beats that cover it draw the shape of
  the result in the hedged language the claim itself uses, and the axis is labelled "roughly
  half the time → most of the time" rather than with percentages.
- **Whether one added sentence generalises.** The two benchmarks above both tested general
  security hints on real repositories and found little benefit, which is a different setup
  from naming a specific compliance frame on a fresh build. Neither result confirms nor
  refutes the video's claim, and no study testing the video's exact setup was found.
