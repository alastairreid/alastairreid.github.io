---
layout: paper
year: 2008
title: SoC-C - efficient programming abstractions for heterogeneous multicore systems on chip
slides: cases2008-SoC-C-slides.pdf
publisher: ACM
png: cases2008-SoC-C.png
pages: 95--104
month: October
location: Atlanta, GA, USA
file: cases2008-SoC-C.pdf
editor: Erik R. Altman
doi: 10.1145/1450095.1450112
day: 19-24
booktitle: Proceedings of the 2008 International Conference on Compilers, Architecture, and Synthesis for Embedded Systems (CASES 2008)
author: Alastair D. Reid, Krisztián Flautner, Edmund Grimley-Evans, Yuan Lin
ar_shortname: CASES 08
ar_file: CASES_08
affiliation: ARM Ltd and University of Michigan
acceptance: 33
abstract: |
    
    The architectures of system-on-chip (SoC) platforms found in high-end
    consumer devices are getting more and more complex as designers strive
    to deliver increasingly compute-intensive applications on
    near-constant energy budgets.  Workloads running on these platforms
    require the exploitation of heterogeneous parallelism and increasingly
    irregular memory hierarchies.  The conventional approach to
    programming such hardware is very low-level but this yields software
    which is intimately and inseparably tied to the details of the
    platform it was originally designed for, limiting the software's
    portability, and, ultimately, the architectural choices available to
    designers of future platform generations.  The key insight of this
    paper is that many of the problems experienced in mapping applications
    onto SoC platforms come not from deciding how to map a program onto
    the hardware but from the need to restructure the program and the
    number of interdependencies introduced in the process of implementing
    those decisions.  We tackle this complexity with a set of language
    extensions which allows the programmer to introduce pipeline
    parallelism into sequential programs, manage distributed memories, and
    express the desired mapping of tasks to resources.  The compiler takes
    care of the complex, error-prone details required to implement that
    mapping.  We demonstrate the effectiveness of SoC-C and its compiler
    with a ``software defined radio'' example (the PHY layer of a Digital
    Video Broadcast receiver) achieving a 3.4x speedup on 4 cores.
ENTRYTYPE: inproceedings
ID: DBLPconf/cases/ReidFGL08
bibtex: |
    @inproceedings{DBLP:conf/cases/ReidFGL08
        , abstract = {
    The architectures of system-on-chip (SoC) platforms found in high-end
    consumer devices are getting more and more complex as designers strive
    to deliver increasingly compute-intensive applications on
    near-constant energy budgets.  Workloads running on these platforms
    require the exploitation of heterogeneous parallelism and increasingly
    irregular memory hierarchies.  The conventional approach to
    programming such hardware is very low-level but this yields software
    which is intimately and inseparably tied to the details of the
    platform it was originally designed for, limiting the software's
    portability, and, ultimately, the architectural choices available to
    designers of future platform generations.  The key insight of this
    paper is that many of the problems experienced in mapping applications
    onto SoC platforms come not from deciding how to map a program onto
    the hardware but from the need to restructure the program and the
    number of interdependencies introduced in the process of implementing
    those decisions.  We tackle this complexity with a set of language
    extensions which allows the programmer to introduce pipeline
    parallelism into sequential programs, manage distributed memories, and
    express the desired mapping of tasks to resources.  The compiler takes
    care of the complex, error-prone details required to implement that
    mapping.  We demonstrate the effectiveness of SoC-C and its compiler
    with a ``software defined radio'' example (the PHY layer of a Digital
    Video Broadcast receiver) achieving a 3.4x speedup on 4 cores.
    }
        , acceptance = {33}
        , affiliation = {ARM Ltd and University of Michigan}
        , ar_file = {CASES_08}
        , ar_shortname = {CASES 08}
        , author = {Alastair D. Reid and
    Kriszti{\'a}n Flautner and
    Edmund Grimley-Evans and
    Yuan Lin}
        , booktitle = {Proceedings of the 2008 International Conference on Compilers, Architecture,
    and Synthesis for Embedded Systems (CASES 2008)}
        , day = {19-24}
        , doi = {10.1145/1450095.1450112}
        , editor = {Erik R. Altman}
        , file = {cases2008-SoC-C.pdf}
        , location = {Atlanta, GA, USA}
        , month = {October}
        , pages = {95--104}
        , png = {cases2008-SoC-C.png}
        , publisher = {ACM}
        , slides = {cases2008-SoC-C-slides.pdf}
        , title = {{S}oC-{C}: efficient programming abstractions for heterogeneous multicore
    systems on chip}
        , year = {2008}
    }
---
