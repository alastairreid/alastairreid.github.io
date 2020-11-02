---
layout: paper
year: 2003
title: Lock inference for systems software
png: tsl-acp4is.png
month: March
location: Boston, MA, USA
file: tsl-acp4is.pdf
day: 17
booktitle: Proceedings of the Second AOSD Workshop on Aspects, Components, and Patterns for Infrastructure Software (ACP4IS)
author: John Regehr, Alastair Reid
ar_shortname: ACP4IS 03
ar_file: ACP4IS_03
affiliation: University of Utah
abstract: |
    
    We have developed task scheduler logic (TSL) to automate
    reasoning about scheduling and concurrency in systems software.
    TSL can detect race conditions and other errors as well as
    supporting lock inference: the derivation of an appropriate
    lock implementation for each critical section in a system. Lock
    inference solves a number of problems in creating flexible,
    reliable, and efficient systems software. TSL is based on
    a notion of asymmetrical preemption relations and it exploits
    the hierarchical inheritance of scheduling properties that is
    common in systems software.
ENTRYTYPE: inproceedings
ID: tsl-acp4is2003
bibtex: |
    @inproceedings{tsl-acp4is2003
        , abstract = {
    We have developed task scheduler logic (TSL) to automate
    reasoning about scheduling and concurrency in systems software.
    TSL can detect race conditions and other errors as well as
    supporting lock inference: the derivation of an appropriate
    lock implementation for each critical section in a system. Lock
    inference solves a number of problems in creating flexible,
    reliable, and efficient systems software. TSL is based on
    a notion of asymmetrical preemption relations and it exploits
    the hierarchical inheritance of scheduling properties that is
    common in systems software.
    }
        , affiliation = {University of Utah}
        , ar_file = {ACP4IS_03}
        , ar_shortname = {ACP4IS 03}
        , author = {John Regehr and Alastair Reid}
        , booktitle = {Proceedings of the Second AOSD Workshop on Aspects,
    Components, and Patterns for Infrastructure Software (ACP4IS)}
        , day = {17}
        , file = {tsl-acp4is.pdf}
        , location = {Boston, MA, USA}
        , month = {March}
        , png = {tsl-acp4is.png}
        , title = {{L}ock inference for systems software}
        , year = {2003}
    }
---
