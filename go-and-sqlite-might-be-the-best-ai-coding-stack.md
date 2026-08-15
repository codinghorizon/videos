---
layout: default
title: "The Least Fashionable Stack Writes The Best AI Code"
permalink: /go-and-sqlite-might-be-the-best-ai-coding-stack/
date: 2026-08-15
---

# The Least Fashionable Stack Writes The Best AI Code

Every factual claim the finished picture puts on screen, chased to a primary source. Worked
from the `TEXT:` lines in BEATS.md, so nothing that renders as words or figures is missed.

Anything the video asserts that could not be chased to a primary source is listed under
**Not checked** at the bottom, and is not drawn on screen as a figure.

---

## SQLite is one file, and there is no server behind it

Beats 007, 008, 045, 046, 048, 061, 066, 089 draw `app.db` as a single object the app reads
and writes directly, with no service beside it.

> "SQLite is an in-process library that implements a self-contained, serverless,
> zero-configuration, transactional SQL database engine."

> "A complete SQL database with multiple tables, indices, triggers, and views, is contained
> in a single disk file. The database file format is cross-platform — you can freely copy a
> database between 32-bit and 64-bit systems or between big-endian and little-endian
> architectures."

> "Unlike most other SQL databases, SQLite does not have a separate server process. SQLite
> reads and writes directly to ordinary disk files."

- https://www.sqlite.org/about.html

And on what "serverless" means here, which is what beat 046 draws as a direct wire rather
than a negotiated connection:

> "With SQLite, the process that wants to access the database reads and writes directly
> from the database files on disk. There is no intermediary server process."

> "The database engine runs within the same process, thread, and address space as the
> application. There is no message passing or network activity."

- https://www.sqlite.org/serverless.html

## One writer at a time, and unlimited readers

Beat 071 draws six writers with exactly one writing and the rest waiting. That is the
documented concurrency model, not a dramatisation.

> "SQLite supports an unlimited number of simultaneous readers, but it will only allow one
> writer at any instant in time."

> "If many threads and/or processes need to write the database at the same instant (and they
> cannot queue up and take turns) then it is best to select a database engine that supports
> that capability, which always means a client/server database engine."

- https://www.sqlite.org/whentouse.html

## Where SQLite is the wrong default

Beats 071 and 073 concede high traffic, many concurrent writers and globally distributed
products. The same page is explicit about it, and about the reverse:

> "If the website is write-intensive or is so busy that it requires multiple servers, then
> consider using an enterprise-class client/server database engine instead of SQLite."

> "Is the data separated from the application by a network? → choose client/server"

> "For device-local storage with low writer concurrency and less than a terabyte of content,
> SQLite is almost always a better solution."

- https://www.sqlite.org/whentouse.html

## A temporary database per test

Beat 045 shows a test opening `":memory:"`, and the claim that a test can have a fresh
database cheaply.

> The special filename `":memory:"` creates an in-memory database, and "the database ceases
> to exist as soon as the database connection is closed." "Every :memory: database is
> distinct from every other."

- https://www.sqlite.org/inmemorydb.html

## gofmt is one canonical format, not a preference

Beats 006 and 021 show a misaligned Go file being rewritten and stamped `gofmt`, captioned
as canonical rather than chosen.

The Go blog post introducing `go fmt` lists as a benefit of gofmt'd code that it is

> "uncontroversial: never have a debate about spacing or brace position ever again!"

and describes gofmt's output as "the canonical style", with editor and version-control hooks
shipped in the Go repository to keep code in it. Published 23 January 2013.

- https://go.dev/blog/gofmt

## The Go compiler refuses to build code with an unused import

Beat 022 shows `go build` failing on an unused `"fmt"` import and exiting non-zero. That is
the documented behaviour, and the documented reason for it:

> "The presence of an unused variable may indicate a bug, while unused imports just slow
> down compilation, an effect that can become substantial as a program accumulates code and
> programmers over time. For these reasons, Go refuses to compile programs with unused
> variables or imports, trading short-term convenience for long-term build speed and program
> clarity."

The FAQ also notes there is no flag to downgrade it, because "the Go compiler does not
report warnings, only errors that prevent compilation."

- https://go.dev/doc/faq (Implementation → "Can I stop these complaints about my unused
  variable/import?")

## Fast builds were a design goal, not a side effect

Beats 029, 034 and 035 rest on the compile-and-test loop being quick.

> "Finally, working with Go is intended to be fast: it should take at most a few seconds to
> build a large executable on a single computer."

and on why that is achievable:

> "There are no forward declarations and no header files; everything is declared exactly
> once."

- https://go.dev/doc/faq (Origins → "Why did you create a new language?", Design → "What are
  the guiding principles in the design?")

## A Go build is one statically linked binary

Beats 009, 061, 062, 066, 068 and 089 draw `./app` as a single object you can copy and run.

> "The linker in the gc toolchain creates statically-linked binaries by default. All Go
> binaries therefore include the Go runtime, along with the run-time type information
> necessary to support dynamic type checks, reflection, and even panic-time stack traces."

- https://go.dev/doc/faq (Implementation → "Why is my trivial program such a large binary?")

---

## Not checked

- **"If feedback takes ten seconds… if feedback takes ten minutes"** (beats 032, 033). These
  are the argument's own illustration of a fast and a slow loop, not measured build times,
  and the clocks on screen are drawn to those two figures rather than to any benchmark. No
  compile-time or test-time measurement is claimed anywhere in the video.
- **The query-log burst in beat 053.** The count printed is derived from the rows drawn in
  the log beside it, as an illustration of a lazy relation turning one query into many. It is
  not a measurement of any particular ORM, and no ORM is named in that shot.
- **The seed files marked "last touched 2 years ago"** (beat 042) and the environment
  failures listed in beat 043 are invented examples of a familiar situation, not a report on
  any real repository.
- **"Six ways to write it"** (beat 018) and the six hidden ORM layers (beat 052) are
  illustrative sets chosen to make the point, not exhaustive or measured lists.
- **The relative comparison in beat 036** (a weaker model with a fast loop finishing before a
  stronger model in a slow project) is the script's claim about how feedback and capability
  trade off. No benchmark comparing two named models under two build speeds was found, and
  none is shown: the lanes are unlabelled by model and carry no figures.
- **"Most software is boring"** (beats 075 to 078). The share of software that is internal,
  small and unglamorous is asserted rather than measured, and the band on screen is drawn as
  a proportion with no percentage printed on it.
