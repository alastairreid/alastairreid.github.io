---
title: Rust verification tools (2020)
layout: post
---

![Rust logo]{: style="float: left; width: 10%; padding: 1%"}
The [Rust language] and the Rust community are really interesting if you are
want to build better quality systems software.

- The language is specifically designed to make it easier to build reliable
  software.
- The [Rust book] and the [Cargo tool] actively promote the idea that good
  Rust code includes documentation and tests.
- There is an active [Rust fuzzing] community to improve the state
  of Rust packages and other software.
- There is just one compiler for Rust and it has been
  [reshaped to make it easier to write analysis tools][librarification]
  and there are two clean interfaces (MIR and LLVM-IR) that tools can
  hook into.
  This avoids most of the fragmentation we see in C compilers and
  makes it much easier for the compiler and the analysis tool to
  give the same meaning to a single piece of code.[^reddit]

[^reddit]:
    A [comment on
    Reddit](https://www.reddit.com/r/rust/comments/gfz4gh/rust_verification_tools/)
    suggested that Rust had a problem for not having a full formal spec.
    This led me to think about how it actually had something at least
    as good: a single compiler that gives access to the MIR and LLVM-IR
    representations of your code.

Over the last few months, I have been trying to understand one more part
of the story:
_what is the state of formal verification tools for Rust?_

The clean, principled language design and, in particular, the Rust type system
[fit really well with recent work on formal verification][astrauskas:oopsla:2019].
Academic researchers are showing a lot of interest in Rust and
and it seems that the community should be receptive to the idea of formal verification.

So what tools are out there?
What can you do with them?
Are they complete?
Are they being maintained?
What common standards and benchmarks exist?

*[Update March 2021:
Rust verification tools are in active development.
I'm not going to rewrite this entire article but I will
mention that my team at Google has been working on how to use [KLEE], [SeaHorn] and [Crux-MIR]
to verify Rust - you can get our tools [on github here](https://project-oak.github.io/rust-verification-tools/).
]*

Here is a list of the tools that I know about (more details below):
- Cargo-KLEE:
  [repository][Cargo-KLEE],
  [paper][lindner:indin:2018],
  [paper][lindner:indin:2019]
- CBMC:
  [Pull Request][CBMC]
- Crust:
  [repository][Crust],
  [paper][toman:ase:2015]
- Crux-mir:
  [repository][Crux-mir],
- Electrolysis:
  [blog post](https://kha.github.io/2016/07/22/formally-verifying-rusts-binary-search.html),
  [repository][Electrolysis],
  [thesis](https://pp.ipd.kit.edu/uploads/publikationen/ullrich16masterarbeit.pdf),
  [slides](http://kha.github.io/electrolysis/presentation.pdf)
- Haybale:
  [repository][Haybale],
  [crates.io](https://crates.io/crates/haybale),
  [announcement
  (twitter)](https://twitter.com/craigdissel/status/1199046678818385920?s=20)
- KLEE Rust (abandoned):
  [repository][KLEE Rust] https://github.com/jawline/klee-rust
- MIRAI:
  [repository][MIRAI]
- Prusti:
  [website](https://www.pm.inf.ethz.ch/research/prusti.html)
  [repository][Prusti],
  [VS code extension](https://marketplace.visualstudio.com/items?itemName=viper-admin.prusti-assistant),
  [paper][astrauskas:oopsla:2019]
- RustBelt:
  [website][RustBelt],
  [paper][jung:popl:2017]
- RustHorn:
  [repository][RustHorn],
  [paper][matsushita:esop:2020]
- Seer:
  [repository][Seer]
- SMACK:
  [website](https://smackers.github.io),
  [repository][SMACK],
  [paper][baranowski:atva:2018]

There are also some interpreters, tools and libraries that are not formal
verification tools but that are relevant – I mention these at the end.


_Before I go any further, I should probably add a disclaimer:
Although I have spent some time looking at what is available and
reading [Rust verification papers],
I am not an expert in this area so I have probably got things wrong, missed
out important tools, etc.
You should also bear in mind that things are changing fast: I am writing this
in early May 2020 but I hope that, in a few months time, everything I
say will be out of date.
Do please [contact me](mailto:adreid@google.com)  with additions and
corrections._

_Of course, the fact that I am updating this post as people point things out
means that if you look at comments in twitter or reddit about this post,
they may not make sense because I have tried to fix this post in response._


## What can the tools verify?

There are four major categories of software verification tool
in roughly increasing order of how hard it is to use them:
symbolic execution tools,
automatic (aka extended static checkers),
auto-active verifiers
and deductive verifiers.

### Symbolic execution tools

These tools are designed to find bugs by exploring
paths through your program and/or to generate testsuites
with high control coverage.
Unlike the other three kinds of tool, these tools typically don't provide
any guarantee that there are no bugs left but they scale really well
and they are probably the best tools to use on a new codebase.

The tools that I know to be in this category are
[Cargo-KLEE],
[Haybale]
and [Seer].


### Automatic verification tools

These tools are good for checking for what some call "Absence of Run-Time
Exception" (AoRTE).
Runtime errors includes things like the following
(not all of these apply to safe Rust code).

- No division by zero
- No integer overflow
- No failing assertions
- Memory safety
  - All array accesses in bounds
  - No null dereferences
  - No buffer overflows
  - No use after free
  - No memory leaks
- Lock safety of concurrent code

While not all tools aim to check all of the above,
the automatic verification tools I know of are
[CBMC],
[Crux-mir],
[MIRAI],
[RustHorn],
[SMACK].
It is worth saying that the [Crust] tool is different from the other
tools in that it is designed to check that a library that contains
unsafe Rust code is externally safe.

One of the appealing features of the automatic verification tools
is that you don't have to write specifications.
Typically, all you have to do is build a verification harness
(that looks a wee bit like a fuzzing harness)
and maybe add some extra assertions into your code.

For me, this makes these tools the most interesting because,
once the kinks have been worked out, these tools have the
most potential to be added into a normal development flow.
You don't need a lot of training to make use of these tools.
(But note the comments below about the kinks that still have
to be worked out.)


### Auto-active verification tools

While automatic tools focus on things not going wrong,
auto-active verification tools help you verify some key
properties of your code: data structure invariants,
the results of functions, etc.
The price that you pay for this extra power is that
you may have to assist the tool by adding function
contracts (pre/post-conditions for functions),
loop invariants, type invariants, etc. to your code.

The only auto-active verification tool that I am
aware of is [Prusti].
Prusti is a [really interesting tool][astrauskas:oopsla:2019] because
it exploits Rust's unusual type system to help it verify code.
Also Prusti has the slickest user interface:
a [VSCode extension](https://marketplace.visualstudio.com/items?itemName=viper-admin.prusti-assistant)
that checks your code as you type it!


### Deductive verification tools

These tools can be used to show things like "full functional correctness":
that the outputs are exactly what they should be.
Deductive verification tools typically generate a set of "verification
conditions" that are then proved using an interactive theorem prover.

The deductive verification tools for Rust that I know of are
[Electrolysis] and [RustBelt].
[Electrolysis] transpiles Rust code into a functional program in the [Lean]
interactive theorem prover
and you then prove correctness of that program using Lean.
The goal of [RustBelt] is to verify unsafe Rust code but,
strictly speaking, RustBelt does not actually verify Rust code:
you manually transcribe Rust code into &lambda;-Rust and
then use RustBelt to verify that code using IRIS and
the Coq theorem prover.


## How much Rust do these tools support?

As far as I can tell, no verification tool currently
supports the full Rust language.
(In contrast, C verification tools are complete enough to verify
things like OS device drivers.)
Some of the big challenges are:
- Unsafe code
- Closures
- Stdlib

The Electrolysis repository has the [clearest statement of
language coverage](http://kha.github.io/electrolysis/)
of all the tools.
It uses the language reference manual as a guide to what
has to be covered and it uses test code from the manual
(as well as some hand-written tests) to confirm that
that feature is supported.


### Unsafe code

> THE KNOWLEDGE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
> IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF UNLEASHING
> INDESCRIBABLE HORRORS THAT SHATTER YOUR PSYCHE AND SET YOUR MIND ADRIFT IN THE
> UNKNOWABLY INFINITE COSMOS.
> <br>--- The [Rustonomicon].[^irrelevant]

[^irrelevant]:
    That quote from the Rustinomicon isn't really relevant – but it is fun!

The problem with unsafe code is that it eliminates the big advantage
of Rust code: that the type system gives you a bunch of guarantees that
you can rely on while reasoning about your code.
This means that every tool that takes advantage of the Rust typesystem
is going to have a problem with unsafe code.
In particular, I think that this is a problem for [Electrolysis],
[Prusti] and [RustHorn].
On the other hand, tools like [SMACK] that are based on the LLVM IR
have no problem with unsafe code.


### Closures

While "unsafe" code raises some fundamental barriers for some tools,
as far as I can tell, closures just seem to take more effort.
They bring in a degree of indirection / higher-order behaviour that
is harder for tools to handle.

The only tools that I am aware of that can handle closures at the moment
are [Electrolysis] and, I suspect, [SMACK].
(But I could easily have missed some.)


### Standard library

The standard library is complicated in two ways:
1. Some of it uses unsafe code
2. Some of it is highly optimized

So, many verification tools replace the standard library with
something simpler such as a simpler implementation or
a function contract.
It is quite a lot of work to create and maintain this verification
version of the library so standard library support can be quite
incomplete.

Two tools that I know are affected by this are
- the [RustHorn] tool cannot handle the RefCell and Rc
- and the [SMACK] tool has only a
  [small subset of the standard library](https://github.com/smackers/smack/blob/master/share/smack/lib/smack.rs).
But, as far as I know, all tools have problems with incomplete
standard library support.


## Which tools are being maintained?

These tools all vary in how actively they are being developed.
Here is what I know about them.
(Please tell me if I got this wrong.)

- Actively developed: 
  [Cargo-KLEE],
  [Crux-mir],
  [haybale],
  [MIRAI],
  [Miri],
  [Prusti],
  [RustBelt],
  [RustHorn],

- Seems to have stalled:
  Pull request for [CBMC],
  (Rust support in) [SMACK].

- Appears to be abandoned: 
  [Crust],
  [Electrolysis],
  [Seer].

- Definitely abandoned:
  [KLEE Rust].


## Emerging standards and benchmarks

If verification of Rust programs is going to take off, we
need standards and benchmarks.

Standard interfaces
let us try different tools to see which one is best for our codebase;
they let us switch between different kinds of tools (maybe one is
great for finding bugs while another is great for showing the
absence of bugs);
and they let us use a portfolio of tools running in parallel.
Three emerging interfaces are

- The [verifier crate] that provides
  macros `assert!` (and the usual variants like `assert_eq!`),
  `assume!`, `unreachable!` and `nondet!`[^fuzzers]
  that can be used to create verification harnesses.

[^fuzzers]:
    I wonder whether it would be possible to create a further
    layer of abstraction to give fuzzers and verifiers
    a common interface that invokes 
    the [arbitrary crate] in fuzzers and uses `nondet!` in
    fuzzers.

- [Viper rust-contracts] that
  provides macros `requires!`, `ensures!` and `invariant!`
  for use in function attributes and loop bodies.

- The [contracts crate] that
  provides macros `pre!` and `post!` for function contracts
  and `invariant!` for loop invariants.

There is a virtuous cycle between standard interfaces, benchmarks
and [verification competitions].

- Standard interfaces enable the development of meaningful benchmarks
  because they make it possible to share verification harnesses
  and code annotations.

- Benchmarks allow you to compare tools which makes it possible to
  create [verification competitions].[^Haskell-benchmarks]
  The best benchmark suites contain a mixture of different types and
  sizes of code
  and a mixture of code with known (tricky) bugs and of code
  with no bugs to identify tools that are good in one mode or another.
  This mixture reflects real requirements for the tools but it also
  allows for multiple winners – depending on which category matters
  most to each user group or different project phase.

  (Benchmarks are also useful when developing tools and competitive
  benchmark results are useful when publishing papers about tools.)

- [Verification competitions] such as [SV-COMP]
  let tool developers demonstrate how
  good their tools are and they encourage friendly competition between
  tools.
  But you can only take part if your tool implements the interface
  used in the benchmarks.

[^Haskell-benchmarks]:
    One of the motivations for developing the Haskell language
    was the difficulty of comparing all the different lazy functional
    languages that existed before Haskell.
    With a standard language, benchmarks like the brilliantly named
    [nofib benchmark suite] could be developed.


## Cargo integration

While I was looking at these tools, I noticed that many of the tools act on
a single file.  But if I want to verify a Rust package, I really want something
that is integrated with the [Cargo tool].
Tools that seem to have Cargo integration are [Cargo-KLEE] and [Crux-mir].


## Runtime checks, etc.

This article is about *formal* verification tools.
But testing and fuzzing tools are an important, complementary part
of any verification story.

- [LibHoare] is a Rust library for adding runtime pre- and post-conditions to
  Rust programs.

- [Miri] ([paper][jung:popl:2020]) is not a formal verification tool
  but it can be used to detect undefined behaviour
  and it is important in defining what "unsafe" Rust
  is and is not allowed to do.

- [RustFuzz] is a collection of resources for fuzz-testing Rust code.

- [Sealed Rust] is "Ferrous System's plan to qualify the Rust
  Language and Compiler for use in the Safety Critical domain."


## Conclusion

Is looks as though Rust is a very active area for verification tools.
I am not sure yet whether any of the tools are complete enough for
me to use them in anger but it seems that some of them are getting close.

&#x1F576;
The Rust verification future looks very bright!
&#x1F576;


### Postscript

_Where did I get this list of tools from?_
As you might imagine, I searched Google Scholar and the 
web for things like "Rust verification tool"
This finds things like
- The [Rust verification working group] which seems to be dormant,
- The [Rust verification workshop] – I planned to attend this but it has been
  delayed.  The list of talks was helpful in finding some of the tools
  listed on this page.

Also:
- Martin Nyx Brain pointed me at the CBMC pull request for Rust support
- @matt_dz pointed me at his list of [LLVM based program analysis tools](https://gist.github.com/MattPD/00573ee14bf85ccac6bed3c0678ddbef#llvm---verification)
- Zvonimir Rakamaric pointed me at the [verifier crate] and the [verifier benchmarks].



### Footnotes

[Rust language]: https://www.rust-lang.org
[Rust book]: https://doc.rust-lang.org/book/
[Cargo tool]: https://doc.rust-lang.org/cargo/
[Rust fuzzing]: https://github.com/rust-fuzz
[Rustonomicon]: https://doc.rust-lang.org/nomicon/
[Sealed Rust]: https://ferrous-systems.com/blog/sealed-rust-the-pitch/

[astrauskas:oopsla:2019]: {{ site.baseurl }}/RelatedWork/papers/astrauskas:oopsla:2019/
[baranowski:atva:2018]: {{ site.baseurl }}/RelatedWork/papers/baranowski:atva:2018/
[jung:popl:2017]: {{ site.baseurl }}/RelatedWork/papers/jung:popl:2017/
[jung:popl:2020]: {{ site.baseurl }}/RelatedWork/papers/jung:popl:2020/
[lindner:indin:2018]: {{ site.baseurl }}/RelatedWork/papers/lindner:indin:2018/
[lindner:indin:2019]: {{ site.baseurl }}/RelatedWork/papers/lindner:indin:2019/
[matsushita:esop:2020]: {{ site.baseurl }}/RelatedWork/papers/matsushita:esop:2020/
[toman:ase:2015]: {{ site.baseurl }}/RelatedWork/papers/toman:ase:2015/

[Rust verification papers]: {{ site.baseurl }}/RelatedWork/notes/rust-language/

[verification competitions]: {% post_url 2020-04-19-verification-competitions %}

[Lean]: {{ site.baseurl }}/RelatedWork/notes/lean-theorem-prover/
[SV-COMP]: {{ site.baseurl }}/RelatedWork/notes/sv-competition/
[Haskell]: https://haskell.org/
[nofib benchmark suite]: https://link.springer.com/chapter/10.1007/978-1-4471-3215-8_17

[Rust verification working group]: https://rust-lang-nursery.github.io/wg-verification/
[Rust verification workshop]: https://sites.google.com/view/rustverify2020

[CBMC]: https://github.com/diffblue/cbmc/pull/4894
[Crust]: https://github.com/uwplse/crust
[Crux-mir]: https://github.com/GaloisInc/mir-verifier
[Electrolysis]: https://github.com/Kha/electrolysis
[Haybale]: https://github.com/PLSysSec/haybale
[Cargo-KLEE]: https://gitlab.henriktjader.com/pln/cargo-klee
[KLEE Rust]: https://github.com/jawline/klee-rust
[LibHoare]: https://github.com/nrc/libhoare
[MIRAI]: https://github.com/facebookexperimental/MIRAI
[Miri]: https://github.com/rust-lang/miri
[PRUSTI]: https://github.com/viperproject/prusti-dev
[RustBelt]: https://plv.mpi-sws.org/rustbelt/
[RustFuzz]: https://github.com/rust-fuzz
[RustHorn]: https://github.com/hopv/rust-horn
[Seer]: https://github.com/dwrensha/seer
[SMACK]: https://github.com/smackers/smack

[contracts crate]: https://gitlab.com/karroffel/contracts
[Viper rust-contracts]: https://github.com/viperproject/rust-contracts
[arbitrary crate]: https://github.com/rust-fuzz/arbitrary
[librarification]: http://smallcultfollowing.com/babysteps/blog/2020/04/09/libraryification/
[verifier crate]: https://crates.io/crates/verifier
[verifier benchmarks]: https://github.com/soarlab/rust-benchmarks

[Rust logo]: {{ site.baseurl }}/images/Rust_programming_language_black_logo.svg

[KLEE]: https://klee.github.io/
[SeaHorn]: https://seahorn.github.io/
