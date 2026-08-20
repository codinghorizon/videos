---
layout: default
title: "Mojo Just Made Python AI Look Painfully Slow Now"
permalink: /mojo-is-the-new-ai-programming-language/
date: 2026-08-20
---

# Mojo Just Made Python AI Look Painfully Slow Now

{% raw %}
Sources for every figure, date, version and capability the video states on screen.

## The 1.0 release

**Mojo 1.0 was released on 11 August 2026**, as part of the Modular 26.5 release.

- Modular, "Modular 26.5: Mojo 1.0 is here!" — https://www.modular.com/blog/modular-26-5-mojo-1-0-is-here

The stability promise is scoped rather than absolute. Modular states that 1.0's "primary
goal is to provide a stable foundation developers can build on", that during the 1.x
timeframe "changes should primarily be additive, giving developers confidence that the
language will not continually shift beneath them", and that "breaking changes may still be
made, but will be managed with care, following the standards of how mature languages
(e.g. C++) evolve over time."

- Modular, "Modular 26.5: Mojo 1.0 is here!" — https://www.modular.com/blog/modular-26-5-mojo-1-0-is-here

Mojo was first introduced in 2023, so 1.0 arrives roughly three years after the language
was announced.

- Mojo, "Mojo (programming language)" — https://en.wikipedia.org/wiki/Mojo_(programming_language)

## Installation through normal Python tooling

Mojo installs with the standard Python package tooling. The release post gives the install
command as:

    uv pip install --upgrade mojo

- Modular, "Modular 26.5: Mojo 1.0 is here!" — https://www.modular.com/blog/modular-26-5-mojo-1-0-is-here

## MLIR and the compiler

Mojo is built on MLIR rather than compiling straight to LLVM IR. The official vision page
states that "Mojo is powered by a novel compiler framework, historically code-named KGEN
(for 'kernel generator'). KGEN is built using MLIR Core and forms the backbone of Mojo's
metaprogramming capabilities."

- Mojo vision — https://mojolang.org/docs/vision/

MLIR itself is described by the LLVM project as a compiler framework for building
domain-specific compilers, used across AI accelerators, CPUs, hardware design and more.

- MLIR, "Users of MLIR" — https://mlir.llvm.org/users/

## Heterogeneous hardware

The claim that Mojo is designed for heterogeneous hardware is the official framing, not a
summary of it. The vision page states that "the available hardware is increasingly
heterogeneous. The compute spans datacenters and client devices that are filled with chips
from different vendors", that "Mojo is already able to target CPUs and GPUs from different
vendors, making it the first language built for the AI era", and that the goal is support
for "CPUs, GPUs, custom accelerators, ASICs, and more."

- Mojo vision — https://mojolang.org/docs/vision/

The specific GPU vendors Mojo targets are NVIDIA, AMD and Apple silicon.

- Modular skills, `mojo-gpu-fundamentals` — https://github.com/modular/skills

## The Python relationship

The vision page states that "Mojo adopts Python's syntax and should feel familiar to Python
developers — Python is not only one of the most popular programming languages in the world,
but it's also the dominant language in AI."

- Mojo vision — https://mojolang.org/docs/vision/

Interop runs in both directions and both are documented as first class:

- Calling Python from Mojo — https://mojolang.org/docs/manual/python/python-from-mojo/
- Calling Mojo from Python — https://mojolang.org/docs/manual/python/mojo-from-python/
- Python types in Mojo — https://mojolang.org/docs/manual/python/types/

## The systems level features the video names

Every feature named on screen is documented in the Mojo manual:

- Types — https://mojolang.org/docs/manual/types/
- Structs — https://mojolang.org/docs/manual/structs/
- Traits — https://mojolang.org/docs/manual/traits/
- Parameterization — https://mojolang.org/docs/manual/parameters/
- Compile time evaluation — https://mojolang.org/docs/manual/metaprogramming/comptime-evaluation/
- Parameterized declarations and generics — https://mojolang.org/docs/manual/generics/

Traits define shared behaviour that structs conform to, and are checked at compile time so
generic code can require capabilities such as `Movable` or `Comparable`.

- Mojo manual, Traits — https://mojolang.org/docs/manual/traits/

`SIMD` is a language level type rather than a library wrapper. It takes the data type and
the vector width as compile time parameters, which is what lets the same source map onto
the SIMD width of whatever hardware it is compiled for.

- Mojo manual, Parameterization — https://mojolang.org/docs/manual/parameters/

Compile time metaprogramming uses the same language as runtime code. The `comptime` keyword
marks a statement or expression to be evaluated at compile time, including compile time
constants, conditionals and loops.

- Mojo, "Intro to metaprogramming" — https://docs.modular.com/mojo/manual/metaprogramming/

## The official AI agent skills

Modular publishes agent skills for Mojo and MAX development, following the Agent Skills
standard. The four the video names exist under exactly those descriptions:

| Skill | What Modular says it does |
| --- | --- |
| `mojo-syntax` | "Corrects pretrained assumptions so your agent writes modern Mojo" |
| `mojo-gpu-fundamentals` | "Adds the patterns for programming NVIDIA, AMD, and Apple silicon GPUs in Mojo" |
| `mojo-python-interop` | "Handles Mojo calling Python and Python calling Mojo, including building Python extension modules" |
| `new-modular-project` | "Creates a new Mojo or MAX project, setting up the `pixi` or `uv` environment" |

- Modular skills repository — https://github.com/modular/skills
- Mojo AI skills — https://mojolang.org/docs/tools/skills

The repository also carries skills for model work rather than language work
(`import-model`, `serve-model`, `debug-model`, `benchmark-model`, `profile-model`,
`eval-model`) and a `closure_migration` skill.

- Modular skills repository — https://github.com/modular/skills

## The Python ecosystem the video names

NumPy, PyTorch, TensorFlow and JAX are the four libraries named as the layer Python sits on
top of. All four are compiled underneath a Python surface, which is the point being made
rather than a claim about any one of them.

- NumPy — https://numpy.org
- PyTorch — https://pytorch.org
- TensorFlow — https://www.tensorflow.org
- JAX — https://docs.jax.dev

## Not verified

- **Whether Mojo is faster than C++ in any given workload.** The video says Mojo runs
  "much closer to C++" and does not put a benchmark number on screen, deliberately: no
  vendor neutral, reproducible benchmark of Mojo against C++ or CUDA across these
  workloads was found, so no figure is shown.
- **Adoption.** No source was found for how many teams have moved production code into
  Mojo, so the video makes no claim about adoption and shows no adoption figure.
- **Whether Mojo will succeed.** The argument that Mojo becomes the standard performance
  layer for Python AI is a prediction, and is framed as one throughout.

## Figures on screen that are illustrative rather than measured

Four shots draw numbers that are **shapes, not measurements**, and each one is labelled on
screen as illustrative so it cannot be read as a finding:

- The inference profile, where one operation takes 81% of self time. It is drawn to show
  what a profile looks like when a single custom operation dominates. No profile of a
  specific real system is being reported.
- The memory split of a loaded model, at 52% weights, 24% KV cache, 19% overhead and 5%
  headroom. Drawn to show that overhead is a real slice, not to report a measured model.
- The per step latencies in the agent trace, and the compounding total across turns. Drawn
  to show that many small steps add up, not to report timings from a specific agent.
- The compounding optimisation factors in the game of details shot. Drawn to show that
  small independent wins multiply, not to claim those specific factors.

No benchmark or vendor claim appears anywhere in the video, deliberately, because none
could be chased to a reproducible primary source.
{% endraw %}
