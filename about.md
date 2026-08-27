---
layout: page
title: About
permalink: /about/
---

I am a Senior Principal Engineer at Intel Strategic CAD Labs
working at the intersection of
formal verification,
security,
privacy,
software,
hardware,
compilers,
processor architecture and
microarchitecture.

I have a history of initiating projects with impact across the company
and
of creating systems that push the boundary of what is feasible but that I can help transfer to production engineering.

Where possible, I use existing tools and techniques often derived from [academic papers and projects]({% post_url 2020-10-04-a-year-of-papers %}).
If I find gaps where the state of the art does not solve the full problem, I invent ways to fill them.
*There are always gaps.*

## Intel (2021--present)

I am working on formal ISA specifications of the x86 architecture.
I designed a new specification language to [balance precision and readability](https://intellabs.github.io/isa-tools/2026/06/27/designing-a-language-for-readability.html),
and released [a compiler for the language](https://github.com/IntelLabs/isa-tools).
A [preview of the specification](https://intel.github.io/SDM/sdm.html) was released in August 2026.


## Google (2019--2021)

I was tech lead on Google Research's
[Rust Verification Tools project](https://project-oak.github.io/rust-verification-tools/)
working on how to make Rust developers more productive with formal verification tools.
Specifically, our  aim was to *democratize* and *deskill* formal verification to make it
not just accessible by developers but something that developers actually want to use
because they can see how it helps them do their job.

We took the approach of
[meeting the developer where they are](/papers/HATRA_20/):
looking for ways to make
formal verification fit into developers existing workflow of
documentation tests, property-based testing,
fuzzing and automatic test generation.
The first phase of this work was figuring out
[how to use KLEE with Rust]({% post_url 2021-03-29-klee-status %});
as a prelude to shifting focus to usability and productivity.

See also: [project progress posts](https://project-oak.github.io/rust-verification-tools/);
[the code on github](https://github.com/project-oak/rust-verification-tools);
[my Google webpage](https://research.google/people/AlastairReid/);
and blog posts about Rust
([#1]({% post_url 2020-09-03-why-not-both %}),
[#2]({% post_url 2020-05-08-rust-verification-tools %}),
[#3]({% post_url 2021-06-03-automatic-rust-verification-tools-2021 %}),
[#4]({% post_url 2020-10-30-rust-testability %}),
[#5]({% post_url 2020-04-19-verification-competitions %})).

<!--
My boss likes to use the phrase
"[#VerifyAllTheThings](https://twitter.com/hashtag/VerifyAllTheThings?src=hashtag_click)"
and I am figuring out how to make it happen.
-->

I also worked on a fun hardware-software codesign project (not yet public) where I
worked on tools to allow hardware engineers and software engineers to collaborate more
closely by letting them explore the hw/sw design space together.


## Arm (2004--2019)

Until August 2019, I was a senior principal research engineer at Arm Ltd.
working on
[formal specification of the Arm processor architecture](#mechanized-processor-specification).
My research at Arm revolved around the interplay between software/hardware, security, compilers, architecture and
microarchitecture in microprocessors.
This resulted in
[patents](/papers/#patents),
[papers](/papers/#papers)
and, most importantly, tools that are used every day by Arm's processor and architecture teams.

My most influential Arm project produced a methodology and tools for
[formal validation of Arm processors](#processor-formal-verification)
against a 
[formal specification of Arm's processor architecture](#mechanized-processor-specification).
The methodology and tools are in daily use by Arm's processor teams
and the specification has been [publicly released](/arm-v8_3/).
This work inspired RISC-V to do the same and Intel has publicly stated an intention
to create a public, formal x86 specification.

I was a founding member of Arm's team that developed the [Scalable Vector Extension](#vector-processing):
a major new wide-vector instruction set that is used by
[Fujitsu's Post-K
supercomputer](http://www.fujitsu.com/global/Images/armv8-a-scalable-vector-extension-for-post-k.pdf).
I was a founding member of Arm's "Ardbeg"
[software defined radio project](#software-defined-radio)
where I 
[created a language and compiler for programming heterogeneous parallel system](#software-defined-radio).

I have also worked on
[vectorizing compilers](#vectorizing-compiler-for-neon),
defending against architectural side channels,
architectural coverage analysis,
CPU simulators and both the A- and M-class ARMv8 architectures.

## Utah, Yale and Glasgow Universities (1988--2004)

Before working at Arm, I worked on
[functional programming](#yale-university-projects),
[functional reactive programming](#robotics)
and
[operating systems](#university-of-utah-projects).
I hold over 20 [patents](/papers/#patents),
have written over 20 peer reviewed [papers](/papers/#papers)
and I hold a [PhD in formal specification](/papers/PhD_19/) from Glasgow University.


I also like to
[build my own keyboards](/building-keyboards/).


# Professional Experience

| Position                           || Institution                      || Date           |
| :--------------------------------- || :------------------------------- || :------------- |
| Senior Principal Engineer          || Intel                            || 2021 -         |
| Research Scientist                 || Google Research                  || 2019 - 2021    |
| Senior Principal Research Engineer || Arm Ltd                          || 2017 - 2019    |
| - ASL Steering Committee           ||                                  || 2017 - 2019    |
| - Patent Review Committee          ||                                  || 2014 - 2019    |
| Principal Research Engineer        || Arm Ltd                          || 2004 - 2017    |
| - Skill Group Leader               ||                                  || 2011 - 2014    |
| Director                           || Reid Consulting (UK) Ltd         || 2002 - 2004    |
| Research Associate                 || Flux group, University of Utah   || 1998 - 2001    |
| Systems Programmer                 || Haskell Project, Yale University || 1994 - 1998    |

* Table of contents
{:toc}

## Program committees

I have served on the following conference program committees.

- [PLDI 2024](https://pldi24.sigplan.org/) Program Committee
- [PLDI 2023](https://pldi23.sigplan.org/) Program Committee
- [HATRA 2022](https://2022.splashcon.org/home/hatra-2022) Program Committee
- [HATRA 2021](https://2021.splashcon.org/home/hatra-2021) Program Committee
- [PLDI 2018](http://conf.researchr.org/home/pldi-2018) External Review Committee
- [SPIN 2012](http://qav.cs.ox.ac.uk/spin2012/) Program Committee
- [RTAS 2012](http://2014.rtas.org/wp-content/uploads/archives/2012/) Program Committee
- [LCTES 2011](http://lctes2011.elis.ugent.be/?file=kop1.php) Program Committee
- [LCTES 2008](http://lctes08.flux.utah.edu) Program Committee
- [RTAS 2007](http://2014.rtas.org/wp-content/uploads/archives/2007/) Program Committee
- HiPEAC 2007 Program Committee
- [RTAS 2006](http://2014.rtas.org/wp-content/uploads/archives/2006/index.htm) Program Committee

---

## Google Research Projects

I [joined Google Research]({% post_url 2019-11-02-joining-google %}) in 2019 to work on
[Project Oak](https://github.com/project-oak/oak):
an ambitious, multistranded project to provide privacy-respecting computation
in the cloud where all sensitive information is governed by a user policy
and cannot be seen by environments that have not been verified to respect that policy.

The [Oak runtime](https://github.com/project-oak/oak) is written in the
[Rust language](https://www.rust-lang.org/) so it was important to understand how
to apply formal verification to Rust code.
We soon realized that formal verification of Rust was in its infancy and many Rust
verification tools could not handle enough of the Rust language and library features
to be able to verify Oak and the libraries that Oak depends on.

This led me to propose [a project focused on Rust
verification](https://project-oak.github.io/rust-verification-tools/) that
would focus on supporting as much real Rust code as possible and on developing
tools and techniques that could feasibly be adopted into a production
engineering environment.
We can now apply the 
[KLEE](https://klee.github.io/) symbolic execution tool to most Rust code
(see [status update]({% post_url 2021-03-29-klee-status %}))
and we published a paper about our plans for 
[making formal normal](/papers/HATRA_20/): tackling the usability and acceptance
issues developers face with formal verification tools.


## Arm Ltd. Projects (selected)

I joined Arm Research in 2004 and initiate and lead research projects.  As
a supplier of commercial IP, we don't publish details of all our projects so
the following is only a selection.


### Mechanized Processor Specification

This was a very influential project to change the way that Arm thinks about
their processor specifications: how it creates them, how it validates them and
the many different ways that they can use them.

As a result of this work, the specification is executable instead of just being
a static document and we formally validate processor RTL against the
specification, generate parts of simulators, etc. from the specification,
and measure the architectural coverage of testsuites.
It is now standard practice for new architecture extensions
to be tested as they are being designed and for specifications to undergo
regression testing during maintenance.

Concurrently with the [Processor Verification](#processor-formal-verification)
project, I formalized the "pseudocode" that Arm uses to define their
processors; developed a toolchain to parse, typecheck and execute the
specifications; tested and fixed the pseudocode; and evangelized on the
benefits of having a single mechanized specification shared across the company.
The specifications, approach and tools are now in standard use across Arm's
engineering divisions and the specifications have been publicly released in
machine readable form.

This project has been an exercise in _soft power_:
showing the way,
building credibility and support,
paying and asking favours,
building a virtual team across the company,
understanding and overcoming [Conway's
Law](https://en.wikipedia.org/wiki/Conway%27s_law),
and exercising patience.
Changing Arm's use of the specification is only half the challenge;
the other half is helping the ecosystem to use the specification
so Arm has publicly released the mechanized v8-A architecture specification,
I have written papers about the creation, use and testing of the
specification
and I have gone to the USA, Germany, the UK, France, Austria,
and Italy [to give talks](/papers#talks) to industry,
to government agencies, to ``hacker'' conventions, to IETF and
theorem prover workshops,
and to universities about the potential uses of the specification.


3 architecture specifications mechanized,
3 major architecture extensions mechanized (TZM, SVE, Helium),
1 tool publicly released ([ASLi](https://github.com/ARM-software/asl-interpreter)),
1 tool tech-transferred (in regular use by four Arm divisions),
3 papers published
([POPL 19](/papers/POPL_19/),
 [OOPSLA 17](/papers/OOPSLA_17/),
 [FMCAD 16](/papers/FMCAD_16/)),
1 PhD ([thesis](/papers/PhD_19/)),
1 architecture specification publicly released.


### Processor Formal Verification

This was a project to develop a flow to use Arm's architecture specifications
to formally validate Arm's processors and related IP.  This was the primary
motivation for the concurrent project on [mechanizing Arm's processor
specifications](#mechanized-processor-specification).

Working with verification engineers in Arm's processor division, I developed
the ISA-Formal processor verification technique that is based on:

- Machine generation of verification IP from Arm's official processor
  specification documents
- Using model checking for end-to-end verification of processor pipelines

This technique has proven very effective at detecting complex bugs early in the
design process.  It has been used on eight Arm processors and the tools and
technique will be used in all of Arm's next generation processors.

This project was a joy to work on: working with and learning to communicate
with subject experts, hard technical challenges and adoption of the techniques
by multiple project groups and by senior engineering management.

1 paper published ([CAV 16](/papers/CAV_16/)), 1 tool tech-transferred.


### Vector Processing

Building on the experience from [NEON](#vectorizing-compiler-for-neon) and from the
[Software Defined Radio](#software-defined-radio)
project, I spent some time working on how to make vector processing more
flexible and on how to implement it more efficiently.
This led to a major architecture extension known as the Scalable Vector
Extension (SVE) and to multiple architecture and
microarchitecture patents.

Since vector architecture projects always lead to large ISA extensions, I also
created a language and tool to describe large ISAs in a compact, structured
way and, of course,
I made sure that we had a [formal
specification](#mechanized-processor-specification).

Visiting the same topic three times within Arm has taught me a lot about how
to conduct an ISA extension project all the way from initial investigations
with dodgy, hacked-together tools through to a finished design with
benchmarking, assembler, compiler, OS, etc. support, with a formal ISA
specification, processor verification IP, testsuites, etc.
And, most importantly, how to get from those rough beginnings to a polished
design ready for processor teams to implement.

10 patents granted, 2 papers published ([IEEE
Micro 17](/papers/IEEE_Micro/), [DATE 14](/papers/DATE_14/)), 1 tool tech-transferred.


### Software Defined Radio

I led the team developing software tools for Arm's Software Defined Radio
platform. This included developing C language extensions to support
heterogeneous multiprocessors ('System-on-chip C' or just SoC-C), developing
the SoC-C compiler and linker and driving the specification of the toolchain
for individual processors. I also contributed to the initial design of the
Vector (SIMD) instructions for the DSP engine we developed and to both hardware
and software aspects of the trace generation system for low overhead monitoring
of parallel real-time systems. The platform has been spun out into another
company (Cognovo) which has since been acquired by u-blox.

1 working test chip, 8 patents granted, 4 papers published ([CASES 08](/papers/CASES_08/),
[MICRO 08](/papers/MICRO_08/),
[SIPS 06](/papers/SIPS_06/),
[SDR 06](/papers/SDR_06)), 3 tools released, 1 spinout company purchased,
numerous training sessions provided to potential customers.


### Thread Support

A chance discussion over coffee lead to an interesting idea on how to share
resources between hardware threads of different priorities. 

1 patent granted, 1 paper published ([SBAC-PAD 07](/papers/SBAC_PAD_07/)).


### Reliability/Security

Another team had developed an interesting circuit for running processors faster
by detecting and recovering from errors. This short project looked at how this
circuit could be used to detect that someone is tampering with the chip. 

1 patent granted.


### Parallel H.264 decoder

This project explored use of ideas from stream computation to structure
a parallel H.264 decoder. Observations of the difficulty handling control in
stream computation fed into the later development of SoC-C
(see [Software Defined Radio](#software-defined-radio) project).

1 patent filed.


### Vectorizing Compiler for NEON

I joined an existing hardware-software project developing Arm's Advanced SIMD
extensions (NEON). The software component was to improve/test/demonstrate the
design by showing that a vectorizing compiler could be written. My role was to
add floating point support and make the compiler robust enough for release to
partners. One of the nicest comments we received was that our prototype R&D
compiler was more reliable than many production quality commercial tools that
the partner uses.

1 tool released.

---

## University of Utah Projects

I joined the University of Utah's Flux research group in 1999 where I worked on
microkernels, component-based operating systems and embedded systems.

### Embedded Systems

I developed a variety of tools for analyzing embedded systems including
a binary analysis tool to identify which interrupts were enabled/disabled and
a worst-case stack-depth analysis (which accounted for interrupt-handlers).

4 papers published
([ASPLOS 04](/papers/ASPLOS_04),
[TECS 05](/papers/TECS_05),
[ACP4IS 03](/papers/ACP4IS_03/),
[EMSOFT 03](/papers/EMSOFT_03/)).

### Component-Based Operating Systems

I designed and implemented a component extension for C which could handle the
needs of low-level code with complex interconnections and even more complex
component initialization requirements. I used this to develop a more modular
version of the operating system toolkit 'OSKit' previously developed at Utah.

3 papers published
([OSDI 00](/papers/OSDI_00/),
[ASPSE 01](/papers/ASPSE_01/),
[ICSE 02](/papers/ICSE_02/)),
2 open source projects released.

---

## Yale University Projects

I joined Yale University's [Haskell](https://haskell.org/) research group in 1994.

### Robotics

I applied the principles of Functional Reactive Programming to the tasks of
Visual Tracking and Robotics.

2 papers published ([ICSE 99](/papers/ICSE_99/), [PADL 01](/papers/PADL_01/)).

### Haskell Compiler Development

I worked on the Yale Haskell Compiler, the Hugs (Haskell) Compiler, the Glasgow
Haskell Compiler, the standard Haskell libraries, graphics libraries, exception
handling and the foreign function interface.

6 papers published
([PLDI 99](/papers/PLDI_99),
[IFL 98](/papers/IFL_98),
[GFPW 98](/papers/Exceptions),
[RR 98](/papers/StdLib_98),
[Haskell Report](/papers/Haskell_Report),
[Haskell Library](/papers/Haskell_Lib),
[Haskell FFI](/papers/Haskell_FFI/),
[HW 97](/papers/Haskell_97),
[HW 95](/papers/Haskell_95a),
[HW 95](/papers/Haskell_95b)),
1 open source project released,
1 open source project maintained.

---

## University of Glasgow Projects

I earned an [M.Sc. by research](/papers/MSc_93) in formal methods from the
University of Glasgow.


### Foreign Function Interface

I extended the [Glasgow Haskell Compiler](https://wiki.haskell.org/GHCi)'s
garbage collector to better support
the foreign function interface,

1 paper published ([GFPW 94](/papers/GFPW_94)), contributed to 1 open source project.


### GUIs

I implemented a widget library for [Haskell](https://haskell.org/)
using the recently developed 'monad
programming' technique and an early version of Haskell's foreign function
interface.

1 paper published ([GFPW 93](/papers/GFPW_93)).


### GHCi

I worked on adding an interpreter to [GHC](https://wiki.haskell.org/GHC)
and on allowing compiled code and
interpreted code to call each other.  This was not released at the time but
several years later, Julian Seward revived the idea although a new runtime
system was also being written at the time so I think the only part of the
original GHCi that survives is the name.  (Which is a shame because the name
doesn't really make any sense.)


The opinions expressed are my own views and not those of my employer.
