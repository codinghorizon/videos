---
layout: default
title: "Next.js Has an Astro Problem and the Numbers Show It"
permalink: /nextjs-has-an-astro-problem/
date: 2026-08-03
---

# Next.js Has an Astro Problem and the Numbers Show It

Every figure, name and claim the finished video puts on screen, with where it came
from. Figures that were measured rather than quoted say how they were measured.

## How the measurements were taken

Both projects were created from each framework's own scaffolding tool, with no
files added and no configuration changed, and were measured on the same machine
in the same session.

- Next.js `16.2.12`, from `create-next-app` with the App Router and TypeScript.
- Astro `7.1.6`, from `npm create astro@latest` with the `minimal` template and
  strict TypeScript.
- Dependencies installed with npm on Node 22 on macOS.

Sources: [create-next-app](https://nextjs.org/docs/app/api-reference/cli/create-next-app),
[Astro install guide](https://docs.astro.build/en/install-and-setup/).

## JavaScript the home page downloads

| | Next.js 16.2.12 | Astro 7.1.6 |
| --- | --- | --- |
| script files the page requests | 8 | 0 |
| JavaScript, uncompressed | 627 kB | 0 kB |
| JavaScript, gzipped | 186 kB | 0 kB |
| HTML document, gzipped | 2.7 kB | 0.21 kB |

Method: the Next.js project was built with `next build` and served with
`next start`, the home page HTML fetched, every `<script src>` in it collected,
each file read from `.next/static` and gzipped. The Astro project was built with
`astro build` and its `dist/` directory listed: it contains `index.html`,
`favicon.ico` and `favicon.svg`, and no JavaScript file at all.

The eight scripts and their gzipped sizes, as shown on screen: 69.3 kB, 48.0 kB,
38.7 kB, 13.5 kB, 7.3 kB, 5.5 kB, 4.0 kB and 0.3 kB.

Caveat: these are the defaults of a scaffolded project on the day they were
measured, not a fixed property of either framework. Both change with every
release, and a real page adds its own code on top.

## Installed dependency tree

| | Next.js | Astro |
| --- | --- | --- |
| `node_modules` on disk | 358 MB | 163 MB |
| files in `node_modules` | 9,991 | 8,996 |

Method: `du -sm node_modules` after a clean install in each project.

## Cold production build

| | Next.js | Astro |
| --- | --- | --- |
| `build`, from a removed output directory | 3.3 s | 1.5 s |

Method: `rm -rf .next` / `rm -rf dist`, then the framework's own build command
under `/usr/bin/time -p`, wall clock. Next.js 16 builds with Turbopack by
default, which is why this gap is much smaller than it used to be.

Caveat: a one page project is close to the best case for both, and build time on
a real project is dominated by the project rather than the framework.

## What each framework ships, and why

- **Astro strips client JavaScript by default.** "By default, Astro will
  automatically render every UI component to just HTML & CSS, stripping out all
  client-side JavaScript automatically."
  [Astro docs, Islands architecture](https://docs.astro.build/en/concepts/islands/)

- **An island is an interactive component on an otherwise static page.** "In
  Astro, an island is an enhanced UI component on an otherwise static page of
  HTML." Islands are hydrated individually rather than the page being hydrated as
  a whole.
  [Astro docs, Islands architecture](https://docs.astro.build/en/concepts/islands/)

- **Hydration is opted into per component, with a directive.** "Turning any
  static UI component into an interactive island requires only a `client:*`
  directive." `client:load` hydrates immediately, `client:idle` "tells a
  component to load when the browser becomes idle", and `client:visible` "tells a
  component to load only once it enters the viewport".
  [Astro docs, Islands](https://docs.astro.build/en/concepts/islands/),
  [Template directives reference](https://docs.astro.build/en/reference/directives-reference/)

- **Zero JavaScript is about the framework, not about your code.** The stripping
  above applies to the UI framework runtime. A `<script>` tag written in an Astro
  component is still bundled and still shipped.
  [Astro docs, Scripts and event handling](https://docs.astro.build/en/guides/client-side-scripts/)

- **Next.js hydrates the React tree in the browser.** React Server Components
  render on the server and are not sent as component code, but Client Components
  and the React runtime that hydrates them are downloaded and executed in the
  browser.
  [Next.js docs, Server and Client Components](https://nextjs.org/docs/app/getting-started/server-and-client-components),
  [React docs, hydrateRoot](https://react.dev/reference/react-dom/client/hydrateRoot)

- **Astro has taken on the deferred rendering Next.js is known for.** "Add the
  `server:defer` directive to any Astro component on your page to turn it into
  its own server island", which moves slow server work out of the initial render.
  [Astro docs, Server islands](https://docs.astro.build/en/guides/server-islands/)

- **Next.js middleware runs before a request reaches a route** and can rewrite,
  redirect or respond, which is the routing behaviour shown on screen.
  [Next.js docs, Middleware](https://nextjs.org/docs/app/api-reference/file-conventions/middleware)

- **Next.js streams a page in pieces.** Suspense boundaries let parts of a route
  arrive after the shell, which is the progressive fill shown on screen.
  [Next.js docs, Loading UI and streaming](https://nextjs.org/docs/app/api-reference/file-conventions/loading)

## Developer sentiment

- **Astro ranked first for retention among meta-frameworks in the State of JS
  2024 survey**, where retention is "the proportion of positive sentiment among
  respondents having used an item". Next.js sits near the bottom of the same
  ranking.
  [State of JS 2024, meta-frameworks](https://2024.stateofjs.com/en-US/libraries/meta-frameworks/),
  [Astro 2024 year in review](https://astro.build/blog/year-in-review-2024/),
  [Netlify, frontend frameworks 2024 year in review](https://www.netlify.com/blog/2024-frameworks-year-in-review/)

  The survey publishes the ranking rather than the retention percentage, which is
  why the video shows the ranking and no number.

- **Next.js is still the most used meta-framework by a wide margin.** In the same
  survey, 54.6% of respondents had used Next.js, against 23.1% for Astro, 22.8%
  for Nuxt, 16.6% for SvelteKit and 11.8% for Remix. Popularity and retention are
  not the same measurement and they point in different directions here.
  [State of JS 2024 results API](https://api.devographics.com/graphql)

## Documentation aimed at models

- **Astro runs an official documentation MCP server** at
  `https://mcp.docs.astro.build/mcp`, over streamable HTTP, giving AI tools
  "real-time access to the latest documentation, helping AI tools avoid outdated
  recommendations and ensuring they understand current best practices".
  [Astro docs, Building Astro sites with AI tools](https://docs.astro.build/en/guides/build-with-ai/)

  Astro previously published `llms.txt` files. Those URLs now return 404, checked
  against `docs.astro.build`, which is why the video shows the MCP server rather
  than a text file.

## Not verified

- Nothing on screen measures how quickly either page becomes interactive on a
  real device. The phone comparison is an illustration of the consequence of the
  payload difference above, not a measurement, and no timing figure is shown.
- The relative volume of framework specific code against plain HTML in model
  training data is an illustration. No training corpus was inspected and no
  figure is claimed.
- The agent loop comparison shows fewer passes for the simpler output. No
  benchmark of generation accuracy per framework was run and no count is shown.
- The job listing comparison shows relative volume only. No listing count is
  claimed and no job board was sampled.
- The dependency, payload and build measurements are one run on one machine of
  one scaffolded project each. They are not a benchmark suite and would move with
  a different machine, a different package manager or a different release.
