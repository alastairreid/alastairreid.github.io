---
layout: page
title: Papers, Talks and Patents
permalink: /papers/
---

* Table of contents
{:toc}

My [Google Scholar](https://scholar.google.co.uk/citations?hl=en&user=oT8RhJgAAAAJ),
[DBLP](http://dblp.uni-trier.de/pers/hd/r/Reid:Alastair_David),
[ORCID](https://orcid.org/0000-0003-4695-6668) and
[Microsoft Academic](https://academic.microsoft.com/#/detail/2293162450)
pages.

## Papers

<table>
{% for paper in site.data.biblio %}
    <tr style="vertical-align:top">
        <td class="bibtexnumber" style="text-align:right; padding: 10px;">
            <a class="papertitle" href="{{ site.baseurl }}/papers/{{ paper.ar_file }}">{{ paper.ar_shortname | replace:' ','&nbsp;'}}</a>
        </td>
        <td class="bibtexitem">
            {{ paper.ar_title }}
        </td>
    </tr>
{% endfor %}
</table>


## Talks

<h3>Specifications</h3>

  - Connecting MLIR with ISA specifications (WIP)
    <br>
    Talk at [ACM Europe School on MLIR 2026](https://mlir-school.github.io/summer-2026/)
    <br>
    14 August 2026, A Coruña, Spain
    <br>
    [[pdf]](talks/mlir2026-slides.pdf)
    <br>

    What kind of MLIR do we want to generate from ISA specifications?
    This talk captures how my thinking had evolved over the course
    of the meeting from the ideas in the poster that I created 2 weeks before.

    The ideas benefited enormously from work I did with
    [Mathieu Fehr](https://grosser.science/team/fehr/)
    and
    [Sasha Lopoukhine](https://www.lopoukhine.com)
    (both at the University of Cambridge)
    but I think that they disagree with my conclusions a little.

    Also, the "Option #2" slide near the end where I propose making types
    into first class values might be the right idea but every detail on
    the slide is wrong :-(

    _(Note: This talk contains several gratuitious photos of solar eclipses
    because there was a total solar eclipse during the workshop and I was
    determined to work some photos into my talk.
    Sadly, none of the photos are mine because my photos didn't work well.)_

  - Connecting MLIR with ISA specifications (WIP)
    <br>
    Poster at [ACM Europe School on MLIR 2026](https://mlir-school.github.io/summer-2026/)
    <br>
    10 - 14 August 2026, A Coruña, Spain
    <br>
    [[pdf]](talks/connecting-MLIR-and-ISA-MLIR-2026-08-10.pdf) (A0 paper size)

  - Goals of a modern ISA specification
    <br>
    [Programming Languages for Architecture (PLARCH)](https://pldi23.sigplan.org/home/plarch-2023)
    <br>
    17 June, 2023
    <br>
    [[pdf]](talks/goals-of-modern-ISA-spec-PLARCH-2023-06-17.pdf)

    What should we consider when creating an ISA specification?
    What can we learn from the 1970s?
    What are the conflicts between different uses of an ISA specification?

    _(Talking to other researchers after the workshop, it became clear that I had missed out something
    important: we need to have a range of tools available that can be adapted
    to suit various needs. If we don't, then people will continue to roll their
    own specialized spec because it is too hard to use the official one.)_

  - Towards a formal specification of Intel’s x86 architecture
    <br>
    [Novel Architecture and Novel Design Automation (NANDA)](http://cc.doc.ic.ac.uk/nanda/)
    <br>
    Virtual.
    <br>
    5--6 September, 2022
    <br>
    [[pdf]](talks/towards-a-formal-x86-specification-ImperialCollege-2022-09-05.pdf)

    This talk is about my work on creating a formal specification of Intel's
    x86 architecture: goals, why it is easy, why it is hard and the research
    challenges I see in the future.

  - Leaky abstractions
    <br>
    [RISE summer school 2022](https://www.ukrise.org/2022-summer-school/)
    <br>
    Keynote talk
    <br>
    [UK Research Institute in Secure Hardware and Embedded Systems (RISE)](https://www.ukrise.org)
    <br>
    Centre for Secure Information Technology (CSIT)
    <br>
    Belfast UK
    <br>
    20--21 July, 2022.
    <br>
    [[pdf]](talks/leaky-abstractions-RISE-2022-07-19.pdf)

    Since at least the 1950s, computer design has been viewed as a stack of
    separate concerns: programmers need not worry about how the hardware works
    as long as it satisfies its functional specification; and digital logic
    designers need not worry about how transistors work as long as they turn on
    and off. This separation has allowed engineers at each layer of the stack
    to innovate and has resulted in the remarkable improvements in power,
    performance and area seen over the last 70+ years. Layers in the stack can
    be changed independently of their neighbours because each layer in the
    stack only depends on an abstraction of the layer below. However, these
    abstractions are "leaky": the abstractions are approximate and they omit
    properties such as time, space and power. This talk is about the
    connections between leaky abstractions and security and on both recent
    research and research opportunities in relating architectural security to
    the hardware stack that it rests on.

  - Machine readable specifications at scale
    <br>
    [ZISC seminar, ETH Zurich](https://zisc.ethz.ch/)
    <br>
    Virtual
    <br>
    2 June, 2022
    <br>
    [[pdf]](talks/mrs-at-scale-ETHZ-2022-06-02.pdf)

    There are lots of potential uses for machine readable specifications so you
    would think that every major real world artifact like long-lived hardware
    and software systems, protocols, languages, etc. would have a formal
    specification that is used by all teams extending, implementing, testing,
    verifying or securing the design. But, in practice, this is usually not
    true: most real world systems do not have a well tested, up to date,
    machine readable specification.

    This talk is about why you might want to change this and some things to
    consider as you go about it. In particular, it is about the use and
    creation of machine readable specifications at scale: when the number of
    engineers affected is counted in the thousands. This sort of scale leads to
    different problems and solutions than you would see in a 5–10 person
    project and both the challenges and the potential benefits are
    significantly larger.

    [See also my blog post
    [Machine readable specifications at scale]({{site.baseurl}}{% post_url 2022-01-25-mrs-at-scale %}).]

<h3>Rust Verification</h3>

Talks about the [Rust verification project](https://project-oak.github.io/rust-verification-tools/)
at Google.

  - How can we formally verify Rust for Linux
    <br>
    [Kangrejos](https://kangrejos.com/)
    (workshop attached to [Linux Plumbers 2021](https://linuxplumbersconf.org/event/13/timetable/#20210913.detailed)).
    <br>
    Virtual.
    <br>
    13 September 2021.
    [[pdf]](talks/Kangrejos-2021-09-13.pdf)

    This talk describes the state of formal verification for Rust code in the
    Linux kernel based on the
    [blog posts]({% post_url 2021-08-22-rust-on-linux-1 %})
    I wrote.

  - Building Better Systems (Episode #11): Meeting Developers Where They Are
    <br>
    23 July 2021 (recorded 2nd February).
    [[youtube]](https://www.youtube.com/watch?v=yXEVO-26eC8)
    [[apple podcast]](https://podcasts.apple.com/us/podcast/11-alastair-reid-meeting-developers-where-they-are/id1537190695?i=1000529842759)
    [[simplecast]](https://building-better-systems.simplecast.com/episodes/11-alastair-reid-meeting-developers-where-they-are-TSRN2M5n)
    [[mp3]](https://cdn.simplecast.com/audio/83a96719-0b3a-4a2c-b6ef-4cbfc1905808/episodes/1b616260-3607-44c2-807a-117160a33368/audio/d5b73395-8453-42f6-a66b-1516814cf77f/default_tc.mp3)
    [[transcript]](https://building-better-systems.simplecast.com/episodes/11-alastair-reid-meeting-developers-where-they-are-TSRN2M5n/transcript)

    This 36 minute interview with Joey Dodds and Shpat Morina at Galois focuses on adoption and usability of verification tools
    and where we sit on the spectrum from high-assurance/high-cost to lower-assurance/lower-cost.


  - Using KLEE with Large Rust Programs
    <br>
    [KLEE workshop 2021](https://srg.doc.ic.ac.uk/klee21/)
    <br>
    Virtual (London, UK).
    11 June 2021.
    [[pdf]](talks/using-KLEE-with-Rust-2021-07-11.pdf)
    [[video]](https://youtu.be/zR7oDg7zix0)

    This 12 minute talk focuses on tools: what we have done to adapt KLEE for use with Rust;
    the language, compiler, library and linker features we have encountered in real
    code out in the wild;
    and how we have tried to solve issues in a way that other Rust verification tools can directly use or adapt.


<h3>The Hardware-Software Interface: Quality and Performance</h3>

_One of the most important interfaces in a computer system is the
interface between hardware and software.
This talk examines two critical aspects of defining the
hardware-software interface: quality and performance._

_The first aspect concerns the "radical" idea of creating a single,
high-quality, formal specification of microprocessors that everybody
can use.
This idea does not seem "radical" until you realize that standard
practice is for every group to create their own version of a
specification in their preferred toolchain.
I will describe the challenges that lead to this behavior and how to
overcome the challenges.
This project lead to the creation of Arm's official formal
specification of their microprocessors and to the formal validation of
Arm's processors against that specification._

_The second aspect concerns the tradeoff between portability and
performance in the context of high performance, energy efficient,
parallel systems.
I will describe the challenges in balancing portability and
performance and how I overcame them by defining the hardware-software
interface in terms of extensions of the C language.
This project played a key part in creation of a software-defined radio
system capable of implementing the 4G cellphone protocol._

_The Arm architecture is the largest computer architecture by volume in
the world; it behooves us to ensure that the interface it describes is
appropriately defined._

  - Computer Science Department, Glasgow, UK.
    21 February, 2019
    [[pdf]](/talks/hw-sw-interfaces-2019-02-21.pdf)


<h3>Engineering and Using Large Formal Specifications</h3>

_We have great tools and technique to formally verify hardware and software but,
if we are apply these to real world systems, we need high quality
specifications of real world artifacts such as processors, OSes, libraries,
programming languages and internet protocols.
This talk is about how we are going to avoid a specification bottleneck - it
uses my experience in formalising the ARM processor architecture to suggest an
approach that we can use on other large, complex hardware and software to
create the specifications we need._

  - [ACL2 2018](http://www.cs.utexas.edu/users/moore/acl2/workshop-2018/index.html)
    <br>
    Keynote talk,
    Austin, Texas, USA.
    5-6 November, 2018.
    [[pdf]](/talks/engineering-large-specs-ACL2-2018-11-06.pdf)

<h3>What makes processors fail - and how to prevent it</h3>

A more accessible presentation of the ideas in the [ISA-Formal paper](_papers/CAV_16.md)
for the Electromagnetic Field maker festival.

_Modern processors are amazing devices: small, fast, low power and getting
better with every generation.  But the most amazing things about modern
microprocessors is that they work so incredibly reliably despite all their
incredible complexity._

_This talk is about the battle between complexity and correctness and about how
new formal verification tools can be used to help you design higher performance
processors that actually work.  I will describe the common optimisations, the
bugs that these often introduce and how open source tools such as SAT solvers
and bounded model checkers can be used to find these bugs._

  - [Electromagnetic Field 2018](https://www.emfcamp.org/line-up/2018/417-what-makes-processors-fail-and-how-to-prevent-it)
    <br>
    Eastnor, UK.
    31 August - 2 September 2018.
    [[pdf](/talks/what-makes-processors-fail-EMF-2018-09-02.pdf)]
    [[video](https://media.ccc.de/v/emf2018-417-what-makes-processors-fail-and-how-to-prevent-it)]

<h3>Creating Formal Specifications of the Arm Processor Architecture</h3>

_A talk about why creating formal specifications for real world systems
is hard and what we can do about it.
Some of the key problems are the semantic gap between the architects’ intention
and the written specification; challenges persuading different groups to adopt
a common specification; the number and diversity of existing implementations;
and the practical impossibility of formally verifying all implementations
against the specification.
I discuss lessons learned when creating a formal specification of the Arm
Processor Architecture and using that specification to formally validate
processors against the specification.  And I discuss how those lessons can be
applied in other contexts.  This includes use of traditional testing, formal
validation, social engineering and building a virtuous cycle to drive up the
quality of the specification._

  - [Agence National de la sécurité des systèmes d'information (ANSSI)](https://www.ssi.gouv.fr/)
    <br>
    Invited talk,
    Paris, France.
    24 October, 2018.
    [[pdf]](/talks/creating-formal-specs-ANSSI-2018-10-24.pdf)


  - [Austrian Computer Science Day](https://arise.or.at/2018/01/austrian-computer-science-day-june-2018-salzburg/)
    <br>
    Invited talk,
    Salzburg, Austria.
    15 June, 2018.
    [[pdf](/talks/formalizing-arm-specs-ACSD-2018-06-15.pdf)]

  - [OAuth Security Workshop](https://st.fbk.eu/osw2018)
    <br>
    Invited keynote talk,
    Fondazione Bruno Kessler, Trento, Italy.
    14-16 March, 2018.
    [[pdf](/talks/real-world-artifacts-OSW-2018-03-15.pdf)]

<h3>Specifications: The Next Verification Bottleneck</h3>

_A talk about the importance and difficulty of creating trustworthy specifications of all
the software and protocols we will need to verify software and about the
techniques I used to create a trustworthy specification of the ARM processor
architecture._

  - [ENTROPY 2018: ENabling TRust through Os Proofs...and beYond](https://entropy2018.sciencesconf.org)
    <br>
    Invited talk,
    Villeneuve d'Ascq, France,
    25-26 January, 2018.
    [[pdf](/talks/specs-the-next-bottleneck-ENTROPY-2018-01-26.pdf)]

<h3>How can you trust formally verified software?</h3>

_A talk about practical things you can do with ARM's executable formal
specification with an emphasis on security research.
Despite having the same title, this is a completely different talk from the next one._
TUWAT!

  - [Chaos Communication Congress (34C3)](https://events.ccc.de/congress/2017/wiki/index.php/Main_Page)
    <br>
    [CCC](https://ccc.de/en/),
    Leipzig, Germany,
    27-30 December, 2017.
    [[video](https://media.ccc.de/v/34c3-8915-how_can_you_trust_formally_verified_software)]
    [[pdf](/talks/using-arm-specs-34C3-2017-12-27.pdf)]

<h3>How can you trust formally verified software?</h3>

_A gradually evolving series of talks about my work on creating
correct formal specifications (when there are multiple implementations
already in existence).
Reinforces the idea of having multiple users of a single specification and
includes a short version of the FMCAD16, CAV16 and OOPSLA17 talks._

  - High Performance Embedded and Distributed Systems (HiPEDS) seminar series
    <br>
    Invited talk,
    Imperial College London, UK,
    6th November, 2017.
    [[pdf](/talks/trusting-verified-software-ICL-2017-11-06.pdf)]

  - [Formal Aspects of Computing Science (British Computer Society)](https://www.bcs.org/content/ConWebDoc/58298)
    <br>
    Invited talk,
    London, UK,
    29th September, 2017.
    [[pdf](/talks/trusting-verified-software-BCS-2017-09-29.pdf)]

  - [Reliable, Secure and Scalable Software Systems (RS4) Workshop](https://www.sicsa.ac.uk/events/reliable-secure-scalable-software-systems-rs4-workshop/)
    <br>
    Invited talk,
    Glasgow, UK,
    1st September, 2017.
    [[pdf](/talks/trusting-verified-software-GLA-2017-09-01.pdf)]
    <br>
    (Completely rewritten from May version.)

  - Microsoft Research
    <br>
    Invited talk,
    Cambridge, UK,
    22nd May, 2017.

  - [Cambridge University Computer Laboratory](http://talks.cam.ac.uk/talk/index/72325)
    <br>
    Cambridge, UK,
    2nd May, 2017.
    [[pdf](/talks/trusting-verified-software-CUCL-2017-05-02.pdf)]

  - Queen Mary University
    <br>
    Invited talk,
    London, UK,
    30th November, 2016.
    [[pdf](/talks/trustworthy-specs-QMU-2016-11-30.pdf)]

<h3>Trusting Large Specifications: The Virtuous Cycle</h3>

_First talk emphasizing the importance of having multiple users of a single
specification._

  - [The 4th South of England Regional Programming Language Seminar (S-REPLS 4)](http://srepls4.doc.ic.ac.uk/abstracts/reid/)
    <br>
    Imperial College London, UK,
    27th September, 2016.
    [[pdf](/talks/srepls4-trustworthy.pdf)]


<h3>Trustworthy Specifications of ARM System Level Architecture</h3>

  - [First Deepspec Workshop](https://deepspec.org/events/workshop2016/index.html),
    Princeton, NJ, USA,
    7th June, 2016.

<h3>Backwards compatible formalization of the ARM Architecture</h3>

_First public talk about creating formal specifications of ARM processors._

  - Cambridge University Computer Laboratory
    <br>
    Cambridge, UK,
    February, 2012.
    [[pdf](/talks/bottom-up-formalization-CUCL-2012-02.pdf)]


## Patents

<table>
{% for paper in site.data.patents %}
    <tr style="vertical-align:top">
        <td class="bibtexnumber" style="text-align:right; padding: 10px;">
            {% if paper.link %}
                <a class="papertitle" href="{{ paper.link }}">{{ paper.number | replace:' ','&nbsp;'}}</a>
            {% else %}
                {{ paper.number | replace:' ','&nbsp;'}}
            {% endif %}
        </td>
        <td class="bibtexitem">
            {{ paper.title }}
            <br>
            {{ paper.author }},
            {{ paper.location }}
            {{ paper.type }},
            {{ paper.month }}
            {{ paper.year }}
        </td>
    </tr>
{% endfor %}
</table>
