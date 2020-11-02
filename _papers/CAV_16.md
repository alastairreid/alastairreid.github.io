---
layout: paper
year: 2016
volume: 9780
title: End-to-End Verification of ARM Processors with ISA-Formal
slides: cav2016_isa_formal-slides.pdf
series: Lecture Notes in Computer Science
publisher: Springer Verlag
png: cav2016_isa_formal.png
pages: 42-58
number: 9780
month: July
location: Toronto, Canada
journal: CAV 2016, Part II, Lecture Notes in Computer Science
isbn: 978-3-319-41539-0
file: cav2016_isa_formal.pdf
editor: S. Chaudhuri, A. Farzan
doi: 10.1007/978-3-319-41540-6_3
booktitle: Proceedings of the 2016 International Conference on Computer Aided Verification (CAV'16)
authors: Alastair Reid and Rick Chen and Anastasios Deligiannis and David Gilday and David Hoyes and Will Keen and Ashan Pathirane and Erin Shepherd and Peter Vrabel and Ali Zaidi
ar_shortname: CAV 16
ar_file: CAV_16
affiliation: ARM Ltd
acceptance: 28
abstract: |
    
    Despite 20+ years of research on processor verification, it remains hard to use
    formal verification techniques in commercial processor development.  There are
    two significant factors: scaling issues and return on investment.  The
    scaling issues include the size of modern processor specifications, the
    size/complexity of processor designs, the size of design/verification teams and
    the (non)availability of enough formal verification experts.  The return on
    investment issues include the need to start catching bugs early in development,
    the need to continue catching bugs throughout development, and the need to be
    able to reuse verification IP, tools and techniques across a wide range of
    design styles.
    <p>
    This paper describes how ARM has overcome these issues in our Instruction Set
    Architecture Formal Verification framework ``ISA-Formal.'' This is an
    end-to-end framework to detect bugs in the datapath, pipeline control and
    forwarding/stall logic of processors.  A key part of making the approach scale
    is use of a mechanical translation of ARM's Architecture Reference Manuals to
    Verilog allowing the use of commercial model-checkers.  ISA-Formal has proven
    especially effective at finding micro-architecture specific bugs involving
    complex sequences of instructions.
    <p>
    An essential feature of our work is that it is able to scale all the way from
    simple 3-stage microcontrollers, through superscalar in-order processors up to
    out-of-order processors.  We have applied this method to 8 different ARM
    processors spanning all stages of development up to release.  In all
    processors, this has found bugs that would have been hard for conventional
    simulation-based verification to find and ISA-Formal is now a key part of ARM's
    formal verification strategy.
    <p>
    To the best of our knowledge, this is the most broadly applicable formal
    verification technique for verifying processor pipeline control in mainstream
    commercial use.
ENTRYTYPE: inproceedings
ID: conf/cav/Reid16
bibtex: |
    @inproceedings{conf/cav/Reid16
        , abstract = {
    Despite 20+ years of research on processor verification, it remains hard to use
    formal verification techniques in commercial processor development.  There are
    two significant factors: scaling issues and return on investment.  The
    scaling issues include the size of modern processor specifications, the
    size/complexity of processor designs, the size of design/verification teams and
    the (non)availability of enough formal verification experts.  The return on
    investment issues include the need to start catching bugs early in development,
    the need to continue catching bugs throughout development, and the need to be
    able to reuse verification IP, tools and techniques across a wide range of
    design styles.
    <p>
    This paper describes how ARM has overcome these issues in our Instruction Set
    Architecture Formal Verification framework ``ISA-Formal.'' This is an
    end-to-end framework to detect bugs in the datapath, pipeline control and
    forwarding/stall logic of processors.  A key part of making the approach scale
    is use of a mechanical translation of ARM's Architecture Reference Manuals to
    Verilog allowing the use of commercial model-checkers.  ISA-Formal has proven
    especially effective at finding micro-architecture specific bugs involving
    complex sequences of instructions.
    <p>
    An essential feature of our work is that it is able to scale all the way from
    simple 3-stage microcontrollers, through superscalar in-order processors up to
    out-of-order processors.  We have applied this method to 8 different ARM
    processors spanning all stages of development up to release.  In all
    processors, this has found bugs that would have been hard for conventional
    simulation-based verification to find and ISA-Formal is now a key part of ARM's
    formal verification strategy.
    <p>
    To the best of our knowledge, this is the most broadly applicable formal
    verification technique for verifying processor pipeline control in mainstream
    commercial use.
    }
        , acceptance = {28}
        , affiliation = {ARM Ltd}
        , ar_file = {CAV_16}
        , ar_shortname = {CAV 16}
        , authors = {Alastair Reid and Rick Chen and Anastasios Deligiannis and
    David Gilday and David Hoyes and Will Keen and Ashan Pathirane and
    Erin Shepherd and Peter Vrabel and Ali Zaidi}
        , booktitle = {Proceedings of the 2016 International Conference on Computer Aided Verification (CAV'16)}
        , doi = {10.1007/978-3-319-41540-6\_3}
        , editor = {S. Chaudhuri and A. Farzan}
        , file = {cav2016_isa_formal.pdf}
        , isbn = {978-3-319-41539-0}
        , journal = {CAV 2016, Part II, Lecture Notes in Computer Science}
        , location = {Toronto, Canada}
        , month = {July}
        , number = {9780}
        , pages = {42-58}
        , png = {cav2016_isa_formal.png}
        , publisher = {Springer Verlag}
        , series = {Lecture Notes in Computer Science}
        , slides = {cav2016_isa_formal-slides.pdf}
        , title = {{E}nd-to-{E}nd {V}erification of {A}RM {P}rocessors with {I}SA-{F}ormal}
        , volume = {9780}
        , year = {2016}
    }
---
