---
layout: paper
abstract: |
    In this paper we describe the ARM Scalable Vector Extension
    (SVE). Several goals guided the design of the architecture. First was
    the need to extend the vector processing capability associated with
    the ARM AArch64 execution state to better address the compute
    requirements in domains such as high performance computing (HPC), data
    analytics, computer vision and machine learning. Second was the desire
    to introduce an extension that can scale across multiple
    implementations, both now and into the future, allowing CPU designers
    to choose the vector length most suitable for their power, performance
    and area targets. Finally, the architecture should avoid imposing a
    software development cost as the vector length changes and where
    possible reduce it by improving the reach of compiler
    auto-vectorization technologies.
    <p>
    We believe SVE achieves these goals. It allows implementations to
    choose a vector register length between 128 and 2048 bits. It supports
    a vector length agnostic programming model which allows code to run
    and scale automatically across all vector lengths without
    recompilation. Finally, it introduces several innovative features that
    begin to overcome some of the traditional barriers to
    auto-vectorization.
affiliation: ARM Ltd
ar_file: IEEE_Micro
ar_shortname: IEEE Micro
author: Nigel Stephens, Stuart Biles, Matthias Boettcher, Jacob Eapen, Mbou Eyole, Giacomo Gabrielli, Matt Horsnell, Grigorios Magklis, Alejandro Martinez, Nathanael Premillieu, Alastair Reid, Alejandro Rico, Paul Walker
doi: 10.1109/MM.2017.35
file: sve-ieee-micro-2017.pdf
journal: IEEE Micro
month: March
number: 2
pages: 26--39
title: The ARM Scalable Vector Extension
volume: 37
year: 2017
ENTRYTYPE: article
ID: journal/micro/sve2017
bibtex: |
    @article{journal/micro/sve2017
        , abstract = {In this paper we describe the ARM Scalable Vector Extension
    (SVE). Several goals guided the design of the architecture. First was
    the need to extend the vector processing capability associated with
    the ARM AArch64 execution state to better address the compute
    requirements in domains such as high performance computing (HPC), data
    analytics, computer vision and machine learning. Second was the desire
    to introduce an extension that can scale across multiple
    implementations, both now and into the future, allowing CPU designers
    to choose the vector length most suitable for their power, performance
    and area targets. Finally, the architecture should avoid imposing a
    software development cost as the vector length changes and where
    possible reduce it by improving the reach of compiler
    auto-vectorization technologies.
    <p>
    We believe SVE achieves these goals. It allows implementations to
    choose a vector register length between 128 and 2048 bits. It supports
    a vector length agnostic programming model which allows code to run
    and scale automatically across all vector lengths without
    recompilation. Finally, it introduces several innovative features that
    begin to overcome some of the traditional barriers to
    auto-vectorization.}
        , affiliation = {ARM Ltd}
        , ar_file = {IEEE_Micro}
        , ar_shortname = {IEEE Micro}
        , author = {Nigel Stephens
    and
    Stuart Biles
    and
    Matthias Boettcher
    and
    Jacob Eapen
    and
    Mbou Eyole
    and
    Giacomo Gabrielli
    and
    Matt Horsnell
    and
    Grigorios Magklis
    and
    Alejandro Martinez
    and
    Nathanael Premillieu
    and
    Alastair Reid
    and
    Alejandro Rico
    and
    Paul Walker}
        , doi = {10.1109/MM.2017.35}
        , file = {sve-ieee-micro-2017.pdf}
        , journal = {IEEE Micro}
        , month = {March}
        , number = {2}
        , pages = {26--39}
        , title = {{T}he {A}RM {S}calable {V}ector {E}xtension}
        , volume = {37}
        , year = {2017}
    }
---