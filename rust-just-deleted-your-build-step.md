---
layout: default
title: "Rust Just Deleted Your Build Step (Vite 8 Is 30x Faster)"
permalink: /rust-just-deleted-your-build-step/
---

# Rust Just Deleted Your Build Step (Vite 8 Is 30x Faster)

Every figure quoted in this video, with where it comes from and how it was read.
Sources are listed in the order the video reaches them.

---

## Vite used two bundlers before version 8

Vite ran esbuild for development and Rollup for production builds. The Vite team
describes the arrangement, and its cost, in their own words: the split produced
"separate transformation pipelines, different plugin systems and a growing amount
of glue code to keep bundling behavior aligned between development and production."

esbuild is written in Go. Rollup is written in JavaScript. The reason esbuild was
not used for production output is that its code splitting was incomplete and its
plugin surface did not cover what Rollup plugins could do, which is why the two
tools were used for different jobs rather than one replacing the other.

Source: Vite 8 beta announcement, vite.dev
https://vite.dev/blog/announcing-vite8-beta

---

## Vite 8 shipped on 12 March 2026

Vite 8.0 stable replaced the dual bundler architecture with Rolldown, a single
bundler written in Rust. Rolldown became the bundler for every Vite user rather
than an opt in preview.

The same release added an integrated devtools option, built in tsconfig `paths`
support, `emitDecoratorMetadata` support, WebAssembly SSR support via `.wasm?init`,
and browser console forwarding to the dev server. Node.js requirements were
unchanged from Vite 7 at Node 20.19+ and 22.12+.

Source: Vite 8.0 announcement, vite.dev
https://vite.dev/blog/announcing-vite8

---

## Rolldown 1.0 reached stable on 7 May 2026

The project timeline, as published by VoidZero:

| Date | Milestone |
| --- | --- |
| April 2024 | First public release, 0.10.1 |
| December 2024 | 1.0.0 beta 1 |
| May 2025 | rolldown-vite technical preview |
| December 2025 | Vite 8 beta with Rolldown |
| January 2026 | Rolldown 1.0 RC |
| March 2026 | Vite 8 stable |
| May 2026 | Rolldown 1.0 stable |

At 1.0 the API is locked under semantic versioning: option names, types and plugin
hook signatures stay backward compatible within `^1.0.0`, excluding features
explicitly marked experimental.

Around 200 people contributed to Rolldown. Vite core has over 1,200 contributors.

Source: Rolldown 1.0 announcement, VoidZero
https://voidzero.dev/posts/announcing-rolldown-1-0

---

## The benchmark: 19,000 modules

This is the headline timing quoted in the video, and it is the published benchmark
rather than a figure produced for this piece.

The benchmark bundles 19,000 modules, made up of 10,000 React JSX components and
9,000 iconify JavaScript files, with minification and source maps enabled.

| Tool | Time |
| --- | --- |
| Rolldown | 1.61s |
| esbuild | 1.70s |
| rspack | 4.07s |
| Rollup + esbuild | 40.10s |

40.10 divided by 1.61 is 24.9, which is where the "twenty five times" figure in the
video comes from. The "10 to 30 times faster than Rollup" range quoted by both the
Vite and Rolldown teams is a range across project sizes rather than a single
measurement, and the published position is that the gap widens as projects scale.

Note that "Rollup + esbuild" is the correct comparison for a Vite user, because that
pairing is what Vite 7 actually ran.

Sources: Rolldown benchmarks, rolldown.rs
https://rolldown.rs/
https://github.com/rolldown/benchmarks

---

## Real world build times

These are reported by the teams running the builds, not synthetic benchmarks.

| Team | Result |
| --- | --- |
| Linear | 46 seconds down to 6 seconds |
| Beehiiv | build time cut by 64% |
| Ramp | build time cut by 57% |
| Mercedes Benz io | build time down by up to 38% |
| Framer | 67% reduction in chunks |

The Framer figure is a different kind of win from the others. It is a reduction in
the number of output chunks, attributable to chunking behaviour rather than to raw
bundling speed.

Two further reports referenced in press coverage of the release: one team reporting
a build going from 4 minutes to 30 seconds, and another reporting 12 minutes to
2 minutes on a codebase of roughly one million lines.

Sources:
Vite 8.0 announcement, vite.dev
https://vite.dev/blog/announcing-vite8
Rolldown 1.0 announcement, VoidZero
https://voidzero.dev/posts/announcing-rolldown-1-0
Vite 8 coverage, InfoQ, May 2026
https://www.infoq.com/news/2026/05/vite-v8-rust/

---

## Why it is faster than a straight Rust rewrite would explain

Rolldown uses Oxc, a Rust toolchain also led by VoidZero, for parsing, transforming
and minifying. The relevant architectural points:

- One shared representation across parse, transform and minify, so source is not
  parsed, printed back to text and reparsed between stages as it was when two
  separate tools each owned part of the pipeline.
- Parsing is parallelised across cores. JavaScript based tooling is effectively
  limited to a single thread for this work.
- Oxc's semantic analysis feeds tree shaking, which the Vite team cite directly:
  "we can leverage Oxc's semantic analysis to perform better tree-shaking in
  Rolldown."

Published Oxc component figures: the parser runs roughly 3 times faster than SWC,
the transformer roughly 40 times faster than Babel, oxlint roughly 50 to 100 times
faster than ESLint, and oxfmt formats up to 30 times faster than Prettier.

Minification is a documented trade off rather than a pure win. Rolldown and Oxc
offer minification on a separate AST over the bundled chunks, which enables more
cross module optimisation and produces smaller bundles, at the cost of some speed
when the minifier is enabled.

Sources:
Vite 8 beta announcement, vite.dev
https://vite.dev/blog/announcing-vite8-beta
Rolldown 1.0 announcement, VoidZero
https://voidzero.dev/posts/announcing-rolldown-1-0

---

## Plugin compatibility

Rolldown implements the same plugin API as Rollup, and Vite 8 retains full plugin
API compatibility with the existing Vite plugin ecosystem. The published position
from both teams is that most existing Vite plugins work out of the box on Vite 8.

"Most" is doing real work in that sentence. Projects depending on Rollup specific
plugins or on esbuild transform hooks are the ones that break, which is why
checking the plugin registry before upgrading is worth the time.

Sources:
Vite 8.0 announcement, vite.dev
https://vite.dev/blog/announcing-vite8
Rolldown 1.0 announcement, VoidZero
https://voidzero.dev/posts/announcing-rolldown-1-0

---

## Vite 8.1 and bundled dev mode, 23 June 2026

Vite's original design served native ES modules in development and did not bundle
at all. That approach degrades on very large applications, because each module is
its own request.

Vite 8.1 shipped experimental Bundled Dev Mode, referred to as Full Bundle Mode
before release. Measured on an application of 10,000 React components, compared
against the unbundled dev server:

- around 15 times faster startup
- around 10 times faster full page reloads
- hot module replacement stays immediate regardless of application size

On Linear's real codebase the reported figures are a 3 times faster cold start,
40% faster full reloads, and 10 times fewer network requests.

It is enabled with the `--experimental-bundle` flag or `experimental.bundledDev: true`
in the Vite config. It is experimental: it focuses on the browser side and on basic
plugins, third party plugins may not work, and some minor features may not behave
optimally.

Vite 8.1 also shipped an experimental chunk import map, which uses import maps to
stop a change in one chunk cascading hash changes through others, improving cache
efficiency. `experimental.renderBuiltUrl` is currently incompatible with it.

The same release added two Lightning CSS features, external CSS file imports and
plugin file dependency registration. The team have stated an intention to change
the default CSS transformer to Lightning CSS, itself written in Rust, in the next
major version. It can be enabled today with `css.transformer: 'lightningcss'`.

Vite 8.1 also added a `caseSensitive` option to `import.meta.glob`, and support for
the WebAssembly ESM integration proposal.

Source: Vite 8.1 announcement, vite.dev
https://vite.dev/blog/announcing-vite8-1

---

## What the upgrade costs

Documented breaking changes and friction points:

- `build.rollupOptions` is renamed to `build.rolldownOptions`.
- CommonJS interop differs from Rollup. Rolldown resolves ambiguous default imports
  from CommonJS modules differently, so a default import from a CJS package can
  arrive as `undefined`. A temporary escape hatch exists in
  `legacy.inconsistentCjsInterop: true`.
- Yarn Plug'n'Play has a documented compatibility problem with Rolldown's native
  Rust resolver, reported as particularly affecting Windows. The Vite team have
  indicated they may not actively support Yarn PnP going forward. The workaround is
  setting `nodeLinker` to `node-modules`, which gives up the disk space and install
  speed benefits that PnP exists to provide.
- `manualChunks` may still work, but Rolldown's chunking behaviour is not identical
  to Rollup's, so hand tuned chunking needs verifying.
- Vite 8 is roughly 15 MB larger to install than Vite 7: about 10 MB for
  lightningcss and about 5 MB for Rolldown.
- `@vitejs/plugin-react` v6 has a smaller install size than its predecessor,
  because it replaced Babel with Oxc.

Sources:
Vite 8.0 announcement, vite.dev
https://vite.dev/blog/announcing-vite8
Vite 8 coverage, InfoQ, May 2026
https://www.infoq.com/news/2026/05/vite-v8-rust/

---

## Where the speedup actually lands, and where it does not

Worth stating plainly, because the headline multiple is easy to over read:

- The large multiples are production and CI build numbers. Cold cache builds show
  the biggest gains. Warm cache results on smaller projects are more modest,
  typically in the range of 2 to 4 times.
- The day to day development loop was already running on esbuild, which was already
  fast. Editing a component and watching HMR fire does not feel dramatically
  different on Vite 8 by itself. Bundled Dev Mode in 8.1 is the change that targets
  the development loop, and it is still experimental.
- The 30 times figure is the top of a published range measured on very large module
  counts. It is a ceiling, not a typical result for a small project.

---

## Scale of the ecosystem affected

Vite is downloaded over 65 million times a week. At the time of the Vite 8.1
announcement, Vite 8 was at 41.6 million weekly downloads, close to Vite 7's total.

Sources:
Vite 8.0 announcement, vite.dev
https://vite.dev/blog/announcing-vite8
Vite 8.1 announcement, vite.dev
https://vite.dev/blog/announcing-vite8-1
