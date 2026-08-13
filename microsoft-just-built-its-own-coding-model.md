---
layout: default
title: "Microsoft Doesn't Need OpenAI To Win AI Coding"
permalink: /microsoft-just-built-its-own-coding-model/
date: 2026-08-13
---

# Microsoft Doesn't Need OpenAI To Win AI Coding

Every figure, date and claim the finished picture puts on screen, chased to a primary
source. Where a number appears in a shot, the shot is named beside it.

---

## The model, and that it is Microsoft's own

**MAI-Code-1-Flash is a coding model built by Microsoft AI and shipped into GitHub
Copilot on 2 June 2026.**
Shots: `004-mai-code-1-flash`, `005-not-just-a-picker`, `078-treat-it-like-a-signal`.

- Microsoft AI, "Introducing MAI-Code-1-Flash", 2 June 2026 (updated 8 June 2026).
  https://microsoft.ai/news/introducingmai-code-1-flash/
- GitHub Changelog, "MAI-Code-1-Flash is now available for GitHub Copilot", 2 June 2026.
  https://github.blog/changelog/2026-06-02-mai-code-1-flash-is-now-available-for-github-copilot/

**It was trained without distillation from other companies' models.** Microsoft's wording
is that it was "trained from the ground up on clean, traceable and enterprise-grade data,
without distillation from third-party models". This is the basis for the video's claim
that it is a genuinely first-party model rather than a rebadged one.

- Microsoft AI, as above.

## Where it runs, and that the picker is not the only route to it

**It is offered in the model picker and under the default auto picker.**
Shots: `049-will-it-stop-external`, `056-the-auto-picker`, `081-let-microsoft-decide`.

This is the single most load-bearing source in the video. The argument that a default can
route work to a model nobody explicitly chose is not an inference here; Microsoft states
that the model is available "in model picker and under default auto picker".

- Microsoft AI, "Introducing MAI-Code-1-Flash".
  https://microsoft.ai/news/introducingmai-code-1-flash/

**Rollout by plan.** At launch it began rolling out to Copilot Free, Student, Pro, Pro+ and
Max, starting with a limited set of users in Visual Studio Code and expanding gradually.
Copilot Business and Copilot Enterprise reached general availability on 26 June 2026,
billed at provider list pricing under usage-based billing, and administrators must enable
the MAI-Code-1-Flash policy before their users can select it.

- GitHub Changelog, 2 June 2026 (Free, Student, Pro, Pro+, Max; editor's note of 5 June
  adds Student). https://github.blog/changelog/2026-06-02-mai-code-1-flash-is-now-available-for-github-copilot/
- GitHub Changelog, "MAI-Code-1-Flash for Copilot Business and Copilot Enterprise",
  26 June 2026. https://github.blog/changelog/2026-06-26-mai-code-1-flash-for-copilot-business-and-copilot-enterprise/

**Surfaces.** By 18 June 2026 it was available on Copilot CLI, the Copilot cloud agent, the
GitHub Copilot app, Copilot Chat on GitHub, Visual Studio, GitHub Mobile, JetBrains IDEs,
Eclipse and Xcode, in addition to Visual Studio Code.
Shot: `024-surface-integration`.

- GitHub Changelog, "MAI-Code-1-Flash available on more Copilot surfaces", 18 June 2026.
  https://github.blog/changelog/2026-06-18-mai-code-1-flash-available-on-more-copilot-surfaces/

## The benchmark figures on screen

**SWE-Bench Pro: 51.2% against Claude Haiku 4.5's 35.2%.**
Shot: `010-stay-to-the-end`. These are the only two benchmark numbers the video renders,
and they are drawn as bars with the figures counting up beside them.

**Token efficiency: up to 60% fewer tokens on SWE-Bench Verified**, described by Microsoft
as "solving harder problems with up to 60% fewer tokens". This is what the video's cost
argument rests on when it says a first-party model can be tuned for the product's own
usage pattern.
Shot: `032-route-cheap-reserve-expensive` (as the reason the cheap route is viable).

Microsoft additionally reports higher pass rates on all four coding evaluations it ran
(SWE-Bench Pro, SWE-Bench Verified, SWE-Bench Multilingual, Terminal Bench 2), and margins
of +28.9 points on IF Bench and +14.5 points on Advanced IF for instruction following.

- Microsoft AI, "Introducing MAI-Code-1-Flash".
  https://microsoft.ai/news/introducingmai-code-1-flash/

All of these are Microsoft's own published evaluations of its own model against one named
competitor. They are cited here as what Microsoft claims, which is what the video treats
them as, and they are not independently reproduced.

## The surface area Microsoft already owns

Shots: `014-owns-everything`, `044-becoming-the-stack`, `047-the-boring-superpower`.

- **GitHub.** Acquired by Microsoft, completed 26 October 2018.
  https://news.microsoft.com/2018/06/04/microsoft-to-acquire-github-for-7-5-billion/
- **Visual Studio Code.** Developed by Microsoft; the repository is `microsoft/vscode`.
  https://github.com/microsoft/vscode
- **TypeScript.** Designed and maintained by Microsoft; the repository is
  `microsoft/TypeScript`. https://github.com/microsoft/TypeScript
- **Azure.** Microsoft's own cloud. https://azure.microsoft.com/

## Copilot as a product surface rather than a model wrapper

Shots: `023-not-a-model-wrapper`, `024-surface-integration`, `025-surface-controls`.

The video lists editor integration, repository context, code review, agents, organization
controls, usage metrics, billing and enterprise deployment. Each of these is a documented
GitHub Copilot feature rather than a characterisation.

- GitHub Copilot features and plans. https://github.com/features/copilot
- GitHub Copilot documentation, including organization and enterprise policy management,
  usage metrics and billing. https://docs.github.com/en/copilot

## Microsoft and OpenAI

Shots: `039-the-third-reason`, `040-if-they-change`.

The video's claim is narrow: that the two companies remain deeply linked, and that
Microsoft would prefer its most important AI products not to depend entirely on another
company's roadmap. Microsoft and OpenAI announced a restructured partnership in October
2025, which Microsoft describes as continuing while giving each side more independence.

- Microsoft, "The next chapter of the Microsoft–OpenAI partnership", 28 October 2025.
  https://blogs.microsoft.com/blog/2025/10/28/the-next-chapter-of-the-microsoft-openai-partnership/

## The competitors named on screen

Shots: `045-cursor-and-claude-code`, `046-openai-and-google`.

The video characterises what each competes on rather than stating figures about any of
them, and no number is rendered for any competitor.

- Cursor. https://cursor.com/
- Claude Code. https://www.anthropic.com/claude-code
- OpenAI developer platform. https://platform.openai.com/
- Google AI for developers. https://ai.google.dev/

---

### Not checked

- Microsoft's benchmark results are Microsoft's own, published by Microsoft, comparing its
  model against one competitor it selected. No independent reproduction of SWE-Bench Pro
  51.2%, the 35.2% comparison figure or the 60% token reduction was found.
- No parameter count, active parameter count, context window or list price is stated in
  Microsoft's own announcement or in GitHub's changelogs. Figures for these circulate in
  secondary coverage; none could be traced to a primary source, so none of them appears
  anywhere in the video.
- The claim that a default auto picker will in practice route the majority of everyday
  Copilot work to Microsoft's own model is an argument the video makes, not a published
  fact. Microsoft confirms the model is in the auto picker; it publishes no routing share.
- No usage figure, developer count or adoption number is claimed on screen at any point.
