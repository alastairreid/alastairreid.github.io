---
layout: post
title: ARM Releases Machine Readable Architecture Specification
---

![ARM logo]({{ site.baseurl }}/images/ARM_logo.svg){: style="float: left; width: 10%; padding: 1%"}
The device you are reading this post on consists of a very tall
stack of layers - all the way from transistors and NAND gates all the
way up to processors, C, Linux/ Android/ iOS/ Windows to the browser.
Each of these layers may be written by a different team possibly in a different
company and the interface between these layers is documented and specified
so that each team knows what it  can assume and what it must provide.
One of the most important interfaces in this stack is the one between
hardware and software that says what a processor will do if it is configured
a certain way, provided with page tables, interrupt handlers, put in a certain
privilege level and finallyprovided with a program to execute.
If you want to write a compiler, operating system, hypervisor or security
layer, then you need to know how the processor will behave.
If someone gives you a virus and asks you to figure out how it works
and how to defend against it, then you need to know how the processor will
behave.

The companies that design processors all provide specifications of their
products that detail the processor architecture in excruciating detail.
These specifications are usually in the form of books or PDF documents.
Very large books: [ARM's 64-bit
architecture](https://static.docs.arm.com/ddi0487/b/DDI0487B_a_armv8_arm.pdf) (aka the ARM v8-A architecture)
is over 6000 pages thick.
And these specifications usually contain English text, pseudocode and diagrams
that illustrate the binary format of instructions and of system control/status
registers.
It is then up to diligent engineers and academics around the world to
read those documents and transcribe the relevant parts into computer languages
such as C, C++, Verilog, O'Caml, Coq, Isabelle, ... to implement tools
that generate, dissect or analyse programs for those processors.
This is a very tedious, error-prone process.  But worse, all the popular
architectures are growing at a steady rate so just keeping up with the latest
architecture extensions and bugfixes since the last release is a full time job.

Today ARM released version 8.2 of the ARM v8-A processor specification in machine readable
form.
This specification describes almost all of the architecture: instructions,
page table walks, taking interrupts, taking synchronous exceptions such as page faults,
taking asynchronous exceptions such as bus faults, user mode, system mode,
hypervisor mode, secure mode, debug mode.  It details all the instruction
formats and system register formats.
The semantics is written in [ARM's ASL Specification Language]({{ site.baseurl
}}{% post_url 2016-08-17-specification_languages %}) so
it is all executable and has been tested very thoroughly using the same
architecture conformance tests that ARM uses to test its processors.
(See my paper ["Trustworthy Specifications of ARM v8-A and v8-M
System Level Architecture"]({{ site.url }}/papers/FMCAD_16/).)

The specification is [being released in three sets of XML files](https://developer.arm.com/products/architecture/a-profile/exploration-tools):

* The [System Register Specification](https://developer.arm.com/-/media/developer/products/architecture/armv8-a-architecture/ARMv82A-SysReg-00bet3.1.tar.gz)
  consists of an XML file for each system register in the architecture.
  For each register, the XML details all the fields within the register, how to
  access the register and which privilege levels can access the register.

* The [AArch64 Specification](https://developer.arm.com/-/media/developer/products/architecture/armv8-a-architecture/A64_v82A_ISA_xml_00bet3.1.tar.gz)
  consists of an XML file for each instruction in the 64-bit architecture.  For
  each instruction, there is the encoding diagram for the instruction, ASL code
  for decoding the instruction, ASL code for executing the instruction and
  any supporting code needed to execute the instruction and the decode tree
  for finding the instruction corresponding to a given bit-pattern.  This also contains
  the
  ASL code for the system architecture: page table walks, exceptions, debug,
  etc.

* The [AArch32 Specification](https://developer.arm.com/-/media/developer/products/architecture/armv8-a-architecture/AArch32_v82A_ISA_xml_00bet3.1.tar.gz)
  is similar to the AArch64 specification: it contains encoding diagrams,
  decode trees, decode/execute ASL code and supporting ASL code.

So what can you do with this?  Well, to get you started, here are some of the
things that I have done with it in the past:

* I wrote an interpreter for ASL, added in an ELF loader and hey presto,
  I had a simulator for the ARMv8 architecture.
  (Not a very fast simulator but a simulator all the same.)

* I wrote a transpiler for ASL that converts ASL to C, wrote another ELF loader
  and I had a faster simulator for the architecture.
  (Still not all that fast: I am sure you can do better!)
  I used that to let me [run ARM's internal architecture conformance test suite
  on the spec]({{ site.url }}/papers/FMCAD_16/):
  getting the ISA to pass was a lot of work - but it was nothing
  compared with getting all those fiddly parts of the different privilege
  levels working.

* I modified my interpreter to generate a symbolic representation of its
  actions then used a symbolic expression solver (aka an SMT solver) to
  generate test inputs that would make the ASL take different paths through
  the code for each different input.  In other words, I wrote a test-case
  generator that could get very high branch coverage through the code.
  (Someday I should write about why I gave up on doing this.)

* One of my colleagues wrote a dependency analysis tool that used the symbolic
  representation to perform an information flow analysis.  We used that to
  find security problems in an architecture extension we were working on.

* I wrote a transpiler for ASL that converts ASL to Verilog, wrote yet another
  ELF loader and I had yet another simulator for the architecture.
  (Surprisingly, this simulator ran faster than the C simulator: Verilog
  simulators are very good - or my C generation is very bad.)
  This was the basis for the [ISA-Formal technique for verifying ARM processors]({{ site.url }}/papers/CAV_16/)
  that we use to [formally verify parts of ARM processors]({{ site.baseurl }}{% post_url 2016-07-26-using-armarm %}) or,
  more accurately, to let us use formal verification tools as the best [bug-hunting]({{ site.baseurl }}{% post_url 2016-07-18-finding-bugs %})
  tools we have ever found.

* This year, I wrote yet another transpiler for ASL that converts ASL directly to SMT,
  skipped the ELF loader for a change and I can now prove properties about
  the architecture.  For example, is it possible for a low priority interrupt
  to preempt high priority code?   My tool says no.

* Kathy Gray at Cambridge University has been writing a tool to convert ARM's
  ASL specs to their specification language SAIL - from which they can then
  generate O'Caml to use as a simulator and Isabelle to use for proofs.
  The translated spec is tantalisingly close to working well enough for
  release.

But the specification can be used for much, much more - so download it and do
something surprising with it.

Enjoy!

------

I have written a followup post about [dissecting the ARM Machine Readable
Architecture files]({{ site.baseurl }}{% post_url 2017-04-29-dissecting-ARM-MRA
%}) and I have written [some
scripts](https://github.com/alastairreid/mra_tools) that demonstrate how to do
it.

This post was discussed on [reddit](https://www.reddit.com/r/programming/comments/66kyez/arm_releases_machine_readable_architecture/)
and on [Hacker News](https://news.ycombinator.com/item?id=14174533).

### Related posts and papers

* Paper: [End-to-End Verification of ARM Processors with ISA-Formal]({{ site.url }}/papers/CAV_16/), CAV 2016.
* [Verifying against the official ARM specification]({{ site.baseurl }}{% post_url 2016-07-26-using-armarm %})
* [Finding Bugs versus Proving Absence of Bugs]({{ site.baseurl }}{% post_url 2016-07-18-finding-bugs %})
* [Limitations of ISA-Formal]({{ site.baseurl }}{% post_url 2016-07-30-isa-formal-limitations %})
* Paper: [Trustworthy Specifications of ARM v8-A and v8-M System Level Architecture]({{ site.url }}/papers/FMCAD_16/)), FMCAD 2016.
* [ARM's ASL Specification Language]({{ site.baseurl }}{% post_url 2016-08-17-specification_languages %})
* This post: [ARM Releases Machine Readable Architecture Specification]({{ site.baseurl }}{% post_url 2017-04-20-ARM-v8a-xml-release %})
* [Dissecting the ARM Machine Readable Architecture files]({{ site.baseurl }}{% post_url 2017-04-29-dissecting-ARM-MRA %})
* Code: [MRA Tools](https://github.com/alastairreid/mra_tools)
* [ASL Lexical Syntax]({{ site.baseurl }}{% post_url 2017-05-07-asl-lexical-syntax %})
* [Arm v8.3 Machine Readable Specifications]({{ site.baseurl }}{% post_url 2017-07-31-arm-v8_3 %})
* Paper: [Who guards the guards?  Formal Validation of the Arm v8-M Architecture Specification]({{ site.url }}/papers/OOPSLA_17/)), OOPSLA 2017.
* [Are Natural Language Specifications Useful?]({{ site.baseurl }}{% post_url 2017-08-19-natural-specs %})
* [Formal validation of the Arm v8-M specification]({{ site.baseurl }}{% post_url 2017-09-24-validating-specs %})
