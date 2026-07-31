---
layout: default
title: "Rust Just Deleted Your Build Step (Vite 8 Is 30x Faster)"
permalink: /rust-just-deleted-your-build-step-vite-8-is-30x/
date: 2026-07-31
---

# Rust Just Deleted Your Build Step (Vite 8 Is 30x Faster)

Every figure, version, date and named API this video puts on screen, chased to a primary
source. Worked from the `TEXT:` lines of each beat, so nothing that appears in the picture
is missing from this list.

Checked July 2026.

## The claim in the title

**Rolldown is 10x to 30x faster than Rollup, and the gap widens as the project grows.**
Stated by VoidZero in the Rolldown 1.0 announcement: "Rolldown is 10x-30x faster than
Rollup (the gap widens as project size grows)".
<https://voidzero.dev/posts/announcing-rolldown-1-0>

The same range is carried in the Vite 8 release announcement, which describes builds "up to
10-30x faster".
<https://vite.dev/blog/announcing-vite8>

On screen at: `03-the-number` (10x, 30x), `27-why-a-range` (the 1x to 30x scale).

**It is a range rather than a figure, and the video says so.** Both sources tie the
multiplier to project size, which is why `27-why-a-range` draws a scale with a band across
it rather than a single number, and why `40-the-normal-project` settles the dial well short
of thirty.

## Versions and dates

**Vite 8.0, released 12 March 2026, ships Rolldown as its single bundler.** "Vite 8 ships
with Rolldown as its single, unified, Rust-based bundler."
<https://vite.dev/blog/announcing-vite8>

**Rolldown 1.0 stable, released 7 May 2026.**
<https://voidzero.dev/posts/announcing-rolldown-1-0>

**`rolldown-vite` is the opt in package that came first**, and the Vite 8 migration guide
still names it as the intermediate step for anyone not ready to move.
<https://vite.dev/guide/migration>

On screen at: `02-rolldown-lands` (Rolldown 1.0), `04-title` and `12-vite8-default`
(Vite 8), `11-rolldown-vite` (the package, and both dates).

## What Vite used to run, and what it runs now

**Vite previously used two bundlers: esbuild in development and Rollup for production
builds.** "esbuild for speed during development, and Rollup for optimized production
builds", handling "fast compilation during development" and "production bundling, chunking,
and optimization" respectively.
<https://vite.dev/blog/announcing-vite8>

On screen at: `06-two-bundlers`, `07-the-seam`, `08-enter-rolldown`, `16-one-pipeline`.

## The Oxc toolchain

**Oxc is a collection of JavaScript tools written in Rust, and the components named on
screen all exist:** parser, resolver, transformer and minifier (alongside a linter, a
formatter and a TypeScript runner that this video does not name).
<https://oxc.rs/>

**Rolldown is written in Rust and uses Oxc for the language work.** "Rolldown is written in
Rust and leverages Oxc to handle the language work like parsing and minification."
<https://voidzero.dev/posts/announcing-rolldown-1-0>

On screen at: `09-oxc-stack` (parser, resolver, transformer, minifier, Oxc),
`22-native-minify` and `35-minify` (the Oxc mark on the minify stage),
`02-rolldown-lands` (written in Rust).

## Full Bundle Mode

**Full Bundle Mode bundles modules during development, and the release notes give three
figures: 3x faster dev server startup, 40% faster full reloads and 10x fewer network
requests.**
<https://vite.dev/blog/announcing-vite8>

On screen at: `14-full-bundle-mode` (10x fewer network requests), `15-waterfall` (the
waterfall the request reduction removes).

Only the request figure is put on screen. The other two are in the release notes and the
script may state them; they are not drawn, so nothing in the picture depends on them.

## Plugin compatibility

**Rolldown implements the same plugin API as Rollup, and most existing Vite plugins work
unchanged.** "Most existing Vite plugins work out of the box with Vite 8" and "Rolldown
supports the same plugin API as Rollup and Vite."
<https://vite.dev/blog/announcing-vite8>

**Hook filters are evaluated on the Rust side so a JavaScript plugin hook is not called
unless its filter matches.** "Hook filters allow Rolldown to skip unnecessary Rust-to-JS
calls by evaluating filter conditions on the Rust side before invoking your plugin."
<https://rolldown.rs/apis/plugin-api/hook-filters>

On screen at: `10-drop-in` and `42-plugin-api` (the Rollup plugin API),
`20-plugin-bridge` (the cost of crossing between Rust and JavaScript).

**Four Rollup plugin hooks are not available**, named on screen exactly as the migration
guide lists them: `shouldTransformCachedModule`, `resolveImportMeta`, `renderDynamicImport`
and `resolveFileUrl`.
<https://vite.dev/guide/migration>

On screen at: `43-the-gaps`.

## What was removed from the config surface

All from the Vite 8 migration guide. <https://vite.dev/guide/migration>

- The object form of `build.rollupOptions.output.manualChunks` is **removed**. The function
  form is deprecated in favour of Rolldown's `codeSplitting` option.
- Property mangling options, including `mangleProps` and `reserveProps`, are **unsupported**.
- The `'system'` and `'amd'` output formats are **no longer supported**.
- `require` calls for externalised modules are preserved as `require` rather than converted
  to `import`, which changes bundling semantics.
- Native decorator lowering needs a workaround through Babel or SWC.

On screen at: `44-removed-options`, `45-output-shape`.

## What it costs to upgrade

**Vite 8 requires Node.js 20.19 or later, or 22.12 or later, and the install grows by
roughly 15 MB.**
<https://vite.dev/blog/announcing-vite8>

On screen at: `46-the-price`.

## There is no way back to Rollup

**Vite 8 has no configuration flag that reverts the bundler to Rollup.** The migration guide
offers `rolldown-vite` on Vite 7 as an intermediate step for projects that are not ready,
which means the route back is the previous major version rather than a setting.
<https://vite.dev/guide/migration>

On screen at: `49-no-way-back`.

This corrected an earlier version of the shot, which showed a switch throwing between the
two bundlers and said "one line back". No such switch exists.

## Reported build times

**One production build reported in the Vite 8 release notes went from 46 seconds to 6
seconds.** The same notes report a 64% reduction and a 38% reduction on two other
codebases, and the Rolldown 1.0 announcement reports a 57% reduction on a third.
<https://vite.dev/blog/announcing-vite8>
<https://voidzero.dev/posts/announcing-rolldown-1-0>

On screen at: `30-cold-build` (46s and 6s).

These are results published by the projects that ran them, on their own codebases. They are
on screen as one reported result, labelled as such, and not as a figure a viewer should
expect.

## Parallelism

**Rolldown does work in parallel across cores**, including parallel chunk generation, listed
among the performance work in the 1.0 release candidate announcement.
<https://voidzero.dev/posts/announcing-rolldown-rc>

On screen at: `19-parallel`.

## Caveats

- **The 10x to 30x range is the projects' own benchmark claim, not an independent
  measurement.** Nothing here reproduces it. The video says so, and `28-measure-yours` exists
  because of it.
- **The reported build times are self reported** by the teams named in the release notes,
  on codebases nobody outside those teams can inspect.
- **Nothing on screen states a figure for how much smaller the Oxc minifier's output is.**
  That was drawn as a percentage in an earlier version of `35-minify` and removed: output
  size is a property of the bundle rather than of the minifier, and no source states a
  general figure.
- **The mechanisms in "Where the speed comes from" are explanation, not measurement.**
  Parallelism and the Rust to JavaScript hook boundary are documented, cited above. Single
  parse reuse, allocation strategy and resolver behaviour are how bundlers of this kind are
  built rather than claims any of these sources make in those words, and no figure is
  attached to any of them on screen.
- **Plugin compatibility is stated in general terms by the sources and is treated that way
  here.** No individual community plugin is named with a verdict anywhere in the video,
  because no source supports that and a viewer would act on it.
- **The video does not cover source maps**, because the migration guide says nothing about
  them either way.
