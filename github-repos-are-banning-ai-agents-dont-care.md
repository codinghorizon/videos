---
layout: default
title: "GitHub Repos Are Banning AI And Agents Ignore It"
permalink: /github-repos-are-banning-ai-agents-dont-care/
date: 2026-08-09
---

# GitHub Repos Are Banning AI And Agents Ignore It

Every figure this video puts on screen, chased to the paper that reports it.

## AI contribution policies on GitHub

**Andre Hora, Romain Robbes. "AI Policy, Disclosure, and Human in the Loop: How Are
Contribution Guidelines Adapting to GenAI?" arXiv:2605.16706. Submitted 15 May 2026,
revised 13 July 2026. Accepted at ICSME 2026.**
https://arxiv.org/abs/2605.16706

- 1,000 popular GitHub repositories analysed, 118 AI policies for contributors identified.
- 78% of those policies allow AI-assisted contributions. 22% explicitly discourage AI use.
- 51% require disclosure of AI-assisted contributions.
- 74% require a human in the loop during contribution.

Within the 78% that allow AI, the paper separates degrees of welcome: 60 of the 118
policies (51%) explicitly welcome generative AI, with the remainder permissive without
being enthusiastic.

## Whether coding agents comply with those policies

**Wenhao Yang, Runzhi He, Minghui Zhou. "A First Look at Coding Agents' Compliance with AI
Contribution Rules in Open-Source Communities." arXiv:2607.26819. Submitted 29 July 2026.**
https://arxiv.org/abs/2607.26819

The benchmark, RepoComplianceBench, is built from 455 hand-coded AI contribution rules
drawn from 102 open-source communities, sorted into four rule types: Refuse, Disclose,
Verify and Handoff. From those it curates 106 issues taken from 49 repositories that carry
AI contribution rules. Four frontier coding agents were tested at 280 runs each.

- The policy file was opened in 12 of 347 unaided runs, which is 3.5%. Of 248 unaided
  violations, 242 of them, or 97.6%, happened without the policy ever being opened.
- In repositories that prohibit AI-generated contributions, refusal was 0% for all four
  agents in the unaided condition.
- Disclosure compliance runs 17% to 40% unaided, and rises to 77% to 97% when the agent is
  given a generic reminder, the clause verbatim, or one round of verifier feedback. One of
  the four agents did not improve under reminders or quoted clauses.
- Verification compliance is close to flat under reminders and quoted clauses, and the
  paper describes it as behaving more like a fixed system trait than a response to
  steering. It rises to 90% to 100% only under verifier feedback.
- Refusal stays near zero across every steering condition. Quoting the prohibition verbatim
  leaves refusal at 0% for three of the four agents. The highest refusal rate recorded in
  any cell is 23%, reached by one agent under one round of verifier feedback.

Note on the refusal figure: the paper's abstract states that the agents never refuse to
contribute in AI-banned repositories under any condition tested, while the paper's own
results table records non-zero refusal in five cells under steering. The 0% result is
solid for the unaided condition, which is the condition this video's figure is drawn to.

## The scale of coding agent activity

**Arsham Khosravani, Audris Mockus. "Detecting AI Coding Agents in Open Source: A Validated
Multi-Method Census of 180 Million Repositories." arXiv:2606.24429. Submitted 23 June
2026.**
https://arxiv.org/abs/2606.24429

- Across snapshots from December 2024 to April 2026, commit-attributed agents generate over
  320,000 commits per month.
- Multi-method detection identifies 850,157 Claude Code commits in a single snapshot.
- Bot-account lookup, the signal most adoption studies rely on, recovers only 28,154 of
  those, which is 3.3%, a thirtyfold relative-recall gap.

The 850,157 figure is the single-snapshot count. The same paper separately reports 886,122
Claude Code commits across 17,295 projects cumulatively across snapshots.

## Whether projects are regulating or prohibiting

**Yunqi Chen, Thomas Zimmermann, Bianca Trinkenreich. "Making AI Visible, Not Vanished: How
AI Policies Reshape Developer Experience on GitHub." arXiv:2608.03329. Submitted 4 August
2026.**
https://arxiv.org/abs/2608.03329

- 29,624 GitHub repositories analysed, 385 of them found to have adopted AI policies.
- The paper concludes that AI governance primarily regulates rather than prohibits
  AI-assisted development.

## Not carried into the video

Three further studies of the same question were read and left out, because each covers a
much smaller population than the four above and none of their figures appear on screen:
"Regulating the Machine Contributor" (arXiv:2606.14594, six organisations), "Beyond Banning
AI" (arXiv:2603.26487, 67 projects), and "Making Agent-Mediated Contributions Governable"
(arXiv:2607.15769, 50 repositories).
