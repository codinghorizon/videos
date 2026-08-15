---
layout: default
title: "Your Repo Is Making Your Coding Agent Look Stupid"
permalink: /10-repo-patterns-that-make-coding-agents-less-stupid/
date: 2026-08-15
---

# Your Repo Is Making Your Coding Agent Look Stupid

{% raw %}
The video is an argument about how a codebase shapes what a coding agent does, and it
makes no statistical claim: there is no benchmark, no survey and no market figure in it
anywhere. What the shots put on screen instead is tooling that exists, so what needs
checking is that every command, error message, filename and API shown is the real one and
not an approximation of it.

Everything below was reproduced locally on this machine rather than taken from a
description of it, except where a published document is cited.

## The compiler messages

Two TypeScript errors appear on screen verbatim in the typed boundaries chapter. Both were
produced by compiling the exact snippet the shot renders.

```
$ tsc --version
Version 5.8.3

$ tsc --noEmit --strict a.ts
a.ts(4,7): error TS2322: Type 'number' is not assignable to type 'string'.
a.ts(5,6): error TS2345: Argument of type '{ id: string; }' is not assignable to parameter of type 'User'.
  Property 'email' is missing in type '{ id: string; }' but required in type 'User'.
```

- **088-userid-as-a-number** shows `Type 'number' is not assignable to type 'string'.`
  That is the full text of TS2322 as emitted above.
- **089-required-field** shows `Property 'email' is missing in type '{ id: string; }' but
  required in type 'User'.` That is the second line of TS2345 as emitted above.

Source: TypeScript 5.8.3, `tsc --noEmit --strict`.

## The package manager failure

**020-improvising** shows a terminal running the wrong package manager's command in a repo
whose lockfile belongs to another. The error text on screen is npm's own, reproduced
against a manifest with no `test` script:

```
$ npm --version
10.9.2

$ npm test
npm error Missing script: "test"
npm error
npm error To see a list of scripts, run:
npm error   npm run
```

npm 10 prefixes its diagnostics with `npm error`; earlier majors used `npm ERR!`, so the
prefix on screen is version specific and is the current one.

Source: npm 10.9.2.

`pnpm-lock.yaml`, shown in the same beat, is pnpm's lockfile name. Source: pnpm lockfile
documentation, https://pnpm.io/git#lockfiles.

## The filenames and APIs shown

- `it.skip(...)` in **055-bad-test-copied** is the real skip modifier in both Vitest and
  Jest. Source: https://vitest.dev/api/#test-skip and
  https://jestjs.io/docs/api#testskipname-fn.
- `no-floating-promises` in **133-the-repo-pushes-back** is a real lint rule that reports a
  promise left unhandled, not a rule name invented for the shot. Source:
  https://typescript-eslint.io/rules/no-floating-promises/. The count beside it is part of
  the mock-up rather than an observation.
- `schema.prisma` in **104-source-over-output** is Prisma's default schema location, and
  the generated client it is weighed against is the artifact `prisma generate` writes.
  Source: https://www.prisma.io/docs/orm/prisma-schema/overview.
- `AGENTS.md` in **075-cannot-find-them** is a published convention for a single project
  instruction file that coding agents read, rather than a name invented for this video.
  Source: https://agents.md.
- `server-only` in **089-required-field** is a real package used to stop a module intended
  for the server being imported into client code. The shot draws the boundary and does not
  print its error text. Source:
  https://nextjs.org/docs/app/getting-started/server-and-client-components.

## The marks on screen

Every product logo is drawn from real published mark geometry via
`channels/codinghorizon/src/shorts-kit/logos.ts`, which is generated from the simple-icons
package. No mark is redrawn or approximated. The marks used are Claude, Cursor, pnpm, npm,
PostgreSQL, ESLint, Prettier, TypeScript, Rust, Go, Python, JavaScript, GitHub, GitHub
Actions, Vitest, Prisma, GraphQL, Stripe, Qwen and DeepSeek.

Source: simple-icons, https://simpleicons.org.

## What is illustrative rather than measured

The video argues from examples, and the shots build those examples as working mock-ups: a
file tree, a package manifest, a diff, a test run, a pipeline. The specific contents of
those mock-ups are written for the video and are not observations of any real repository.
That includes every filename invented for a scene, every line count in an editor gutter,
the commit total on the history that scrolls past, the hop counts on the two searches, and
the timer that runs before a regeneration wipes an edit. None of them is offered as a
finding, and none is cited on screen as one.

### Not checked

- The claim that the same model behaves measurably better in a well structured repository
  is the video's argument rather than a result it reports, and no controlled comparison is
  cited for it. It is stated as reasoning about how agents read a codebase, not as a
  measurement.
- The relative ranking of the ten patterns is editorial. Nothing establishes that a repo
  which rejects bad code matters more than a discoverable command surface; the countdown is
  a structure for the argument.
{% endraw %}
