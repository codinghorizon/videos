---
layout: default
title: "The Most Boring Stacks Make AI Write The Best Code"
permalink: /10-programming-stacks-that-make-ai-write-better/
date: 2026-08-15
---

# The Most Boring Stacks Make AI Write The Best Code

Every figure, message, command and technical claim the finished picture puts on screen,
chased to a primary source. Worked from the TEXT lines in BEATS.md, so nothing rendered
is missing from this list.

This video is an argument rather than a report: it states no statistics and quotes no
benchmark. What it does put on screen is real compiler output, real attribute names and
real commands, and those are what is verified here. Where a claim is a judgement about
how a tool behaves rather than a documented fact, it is listed under **Not checked**
instead of being dressed up as one.

## Go and SQLite

**`gofmt` produces one standard layout, so formatting is not a choice a repo makes.**
The Go project ships the formatter with the toolchain and states that gofmt formats Go
source to a single canonical style.
Source: https://pkg.go.dev/cmd/gofmt

**A Go build failure names the file, the line, the column and the reason, and stops.**
The rendered message form `./store.go:42:9: cannot use nil (untyped nil value) as int
value in return statement` is the compiler's own shape for assigning an untyped nil to a
type that has no nil value, per the language spec's treatment of nil and the go/types
error text tracked in the Go issue tracker.
Sources: https://go.dev/ref/spec#The_zero_value , https://github.com/golang/go/issues/18268

**SQLite is one file, with the schema and the data inside it.**
Source: https://www.sqlite.org/onefile.html

**SQLite allows unlimited concurrent readers but only one writer at a time, which is
the ceiling drawn in the concurrency shot.** sqlite.org: "SQLite supports an unlimited
number of simultaneous readers, but it will only allow one writer at any instant in
time", and it names a client/server engine as the right choice when many processes must
write at the same instant.
Source: https://www.sqlite.org/whentouse.html

**SQLite suits small tools, internal apps and low to medium traffic sites**, which is the
set of use cases the shot draws around the file. Same page, "Appropriate Uses For SQLite".
Source: https://www.sqlite.org/whentouse.html

## HTMX and server rendered HTML

**`hx-post`, `hx-get`, `hx-swap` and `hx-target` are the real attribute names**, and
`hx-swap="outerHTML"` "replaces the entire target element with the returned content".
Source: https://htmx.org/docs/

**The server responds with HTML rather than JSON, and htmx swaps it into the page.**
htmx docs: "When you are using htmx, on the server side you typically respond with HTML,
not JSON."
Source: https://htmx.org/docs/

## Strict TypeScript

**`"strict": true` is a single compiler option that enables the strict family of checks.**
Source: https://www.typescriptlang.org/tsconfig/#strict

**The three diagnostics rendered in the checker shot are the compiler's own message
templates**, taken from the TypeScript source of truth for diagnostic text:
- `Cannot find name '{0}'.` — 2304
- `Type '{0}' is not assignable to type '{1}'.` — 2322
- `Property '{0}' is missing in type '{1}'.` — 2324
- `Object is possibly 'null'.` — 2531
Source: https://github.com/microsoft/TypeScript/blob/main/src/compiler/diagnosticMessages.json

## Rust

**The borrow checker error rendered on screen is real and carries that code.** The Rust
error index gives E0502 as `cannot borrow *a as mutable because a is also borrowed as
immutable`, which is the wording the shot uses with the variable renamed.
Source: https://doc.rust-lang.org/error_codes/E0502.html

**Unsafe operations have to be written inside an `unsafe` block, so they are named rather
than implicit.**
Source: https://doc.rust-lang.org/reference/unsafe-keyword.html

**Ownership and borrowing are checked at compile time.**
Source: https://doc.rust-lang.org/book/ch04-01-what-is-ownership.html

## Python

**Type hints are standard library syntax**, and `def get_user(id: int) -> User | None:`
is valid annotation form.
Sources: https://docs.python.org/3/library/typing.html , https://peps.python.org/pep-0604/

**The four commands in the boring path shot are the documented invocations of their
tools:** `uv sync`, `pytest -q`, `mypy .`, and Ruff as the linter.
Sources: https://docs.astral.sh/uv/reference/cli/#uv-sync ,
https://docs.pytest.org/en/stable/how-to/usage.html ,
https://mypy.readthedocs.io/en/stable/running_mypy.html ,
https://docs.astral.sh/ruff/

**An `AttributeError` on `NoneType` is a runtime exception, raised when the code runs
rather than when it is written**, which is the point the traceback shot makes.
Source: https://docs.python.org/3/library/exceptions.html#AttributeError

## Astro

**Astro renders to HTML and ships no client JavaScript by default.**
Source: https://docs.astro.build/en/concepts/why-astro/

**Islands are the documented name for the interactive components hydrated individually
on an otherwise static page.**
Source: https://docs.astro.build/en/concepts/islands/

## Django and Rails

**Django's project layout puts models, views, templates, migrations and tests in known
places, and routes in a URL configuration.**
Sources: https://docs.djangoproject.com/en/stable/intro/tutorial01/ ,
https://docs.djangoproject.com/en/stable/topics/http/urls/

**Rails is built on convention over configuration, and states it as a founding
principle.**
Source: https://guides.rubyonrails.org/getting_started.html

**Django ships an authentication system rather than leaving it to each project.**
Source: https://docs.djangoproject.com/en/stable/topics/auth/

## One binary backends

**`go build -o server` produces a single executable.**
Source: https://pkg.go.dev/cmd/go#hdr-Compile_packages_and_dependencies

**Rust's cargo build produces a single binary artifact for a binary crate.**
Source: https://doc.rust-lang.org/cargo/commands/cargo-build.html

**.NET supports publishing a single file executable**, which is why it appears in the
group of runtimes that do this well.
Source: https://learn.microsoft.com/en-us/dotnet/core/deploying/single-file/overview

**Node can be packaged into a single executable application.**
Source: https://nodejs.org/api/single-executable-applications.html

## Schema first APIs

**OpenAPI, GraphQL schemas and protocol buffers are all machine readable interface
definitions**, which is the property the chapter turns on.
Sources: https://spec.openapis.org/oas/latest.html ,
https://spec.graphql.org/October2021/ ,
https://protobuf.dev/programming-guides/proto3/

**A protobuf message declares field names and types explicitly**, so the field shape
rendered crossing the boundary is a real declaration form.
Source: https://protobuf.dev/programming-guides/proto3/

**OpenAPI documents are used to generate clients and validate requests**, which is what
the shot draws falling out of the schema file.
Source: https://spec.openapis.org/oas/latest.html

## Not checked

These are the video's own arguments rather than documented facts, and no primary source
was found for any of them. They are on screen because the narration makes them, not
because they were verified.

- That coding agents produce better results in these stacks than in others. No benchmark
  is cited by the script and none was found that measures agent output quality by stack.
- The two opening repo runs, the good one and the bad one, are illustrations of the
  script's argument rather than a recorded session.
- That agents specifically struggle with Rust at first, and that the compile and fix loop
  produces better final code than a looser language would.
- That framework conventions help agents because the model has seen more of that
  framework. Plausible from how models are trained, but not measured anywhere found.
- That splitting a system into services early costs more in the AI era than it used to.
- The relative speeds shown in the fast feedback panel are drawn as short and equal
  rather than as measured timings, because no measurement backs any specific figure.
- The twelve minutes and three seconds in the feedback race are the script's own figures,
  used to make a point about scale, not readings from a real build.
