---
title: "ORConf 2024 Summary"
description: |
  This week, I had a great pleasure to present my work done at Samsung R&D
  Institute Poland at the ORConf 2024 conference organised by the FOSSi
  Foundation.

  I presented the same topic as my poster at this year's RISC-V Summit Europe,
  but this time in the form of a 15-minute presentation.

image: orconf.jpg
slug: orconf
date: 2024-09-15 00:00:00+0000
categories:
  - conference
  - riscv
  - fpga
tags:
  - AWS
  - CI
  - cloud
  - conference
  - FPGA
  - hardware
  - RISC-V
  - RVV
---

ORConf holds a special place in my heart, and this year marked my second time
attending. Last year, I gave a lightning talk, which was a great experience (you
can check it out [here][orconf-2023]!). This year, I was excited to return, this
time with both a full 15-minute presentation and another lightning talk. It was
a fantastic opportunity to share what I’ve been working on and connect with
other engineers and open-source enthusiasts. Hopefully, this will become a
tradition 😄

[orconf-2023]: https://www.youtube.com/watch?v=jrZlqJOdzv4&list=PLdf9WdtHD80DYE961eCicG5Atx97U0iUS&index=1&pp=gAQBiAQB

## General Overview

Before diving into the details of my talks, let’s talk about the event itself.
ORConf 2024 took place in Gothenburg, Sweden, from September 13th to 15th. It
was exciting to see that attendance significantly increased this year. Let's
hope to keep that momentum going for open silicon in the coming years!

The conference followed a single-track format with 31 talks, along with an
additional lightning talk session featuring 15 submissions, and an unconference
on Sunday, which included five workshop tracks. ORConf is organized by the
[FOSSi Foundation], a non-profit dedicated to fostering community and innovation
in Free and Open Source Silicon. Besides ORConf, the FOSSi Foundation also
organizes the annual [LatchUp] conference in the USA.

While the primary focus of ORConf is on chip design, there were a few
software-related talks as well, including mine. Topics ranged from RISC-V,
open-source EDA tools, verification ([cocotb] FTW), and modern HDLs, with great
representation from nearly all “new” HDLs: [SpinalHDL], [Chisel], [Clash],
[DFHDL], [Amaranth], and [Spade].

In general, I highly recommend browsing through [the list of talks][talks] and
picking out the ones that catch your interest – you won’t be disappointed! There
was also a lightning talk session, and [a video has already been posted on the
FOSSi YouTube channel][lightning-talks] (complete with chapter markers for each
topic). **Huge kudos to the organizers for getting the videos online just hours
after the talks wrapped up!**

[FOSSi Foundation]: https://fossi-foundation.org/
[LatchUp]: https://fossi-foundation.org/latch-up/2024
[cocotb]: https://www.cocotb.org/
[SpinalHDL]: https://github.com/SpinalHDL/SpinalHDL
[Chisel]: https://www.chisel-lang.org/
[Clash]: https://clash-lang.org/
[DFHDL]: https://dfianthdl.github.io/
[Amaranth]: https://github.com/amaranth-lang/amaranth
[Spade]: https://spade-lang.org/
[talks]: https://fossi-foundation.org/orconf/2024
[lightning-talks]: https://www.youtube.com/watch?v=Xm_kUVhMBdw

## My RVV Talk

{{< youtube 04YZcZ8E_jg >}}

For the past year, my work at *Samsung R&D Institute Poland* has primarily
focused on RISC-V Vector (RVV) development. My talk at ORConf centered around
the process of enabling hardware-accelerated RVV software development, which I
also discussed in my [RISC-V Summit Europe 2024 poster][poster-post].

It’s amazing to see how the open-source RISC-V IP core ecosystem has evolved
over the past year. When I started creating the FPGA-based platform for RVV
software development earlier this year, my options were limited. The only viable
choice at the time was [PULP Ara], a vector coprocessor for the well-known
[CVA6] processor from [OpenHW Group].

Now, the landscape looks very different. PULP Ara has seen significant
improvements over the last few months, fixing most of the bugs I encountered.
Additionally, we now have more high-quality RVV coprocessors available. One
example is the [Saturn Vector Unit], which was [presented at ORConf this
year][saturn-talk] by Jerry Zhao from UC Berkeley. If I’d had access to this six
months ago, my project would have been a walk in the park!

> In my opinion, a platform that prides itself on being open should provide open
> reference implementations *during* the ratification process.

The point is that RVV was ratified in November 2021, but it took nearly *three
years* for the RISC-V community to gain access to quality open-source
RVV-capable cores. In my opinion, a platform that prides itself on being open
should provide open reference implementations *during* the ratification process.
It feels like the RISC-V ISA specification is created by hardware people, for
other hardware people, without adequately considering the needs of software
developers. There seems to be an expectation that the open-source software
community will step in and offer first-class support for new ISA extensions. But
how can that happen if these developers don’t have access to real hardware in
time?

Alright, enough ranting. I encourage you to watch my talk and let me know if you
found the insights valuable. All project materials are available on [my
GitHub][github-project] (additional links: [extended abstract], [poster],
[slides]).

[poster-post]: {{< ref "/post/2024/06/riscv-summit-europe#my-poster" >}}
[PULP Ara]: https://github.com/pulp-platform/ara
[CVA6]: https://github.com/openhwgroup/cva6
[OpenHW Group]: https://www.openhwgroup.org/
[Saturn Vector Unit]: https://github.com/ucb-bar/saturn-vectors
[saturn-talk]: https://www.youtube.com/watch?v=5eitFdW8CCM
[github-project]: https://github.com/MarekPikula/RISC-V-Summit-Europe-ORConf-2024
[extended abstract]: https://riscv-europe-2024.serenitycode.dev/abstract/index.html
[poster]: https://riscv-europe-2024.serenitycode.dev/poster/poster.pdf
[slides]: https://riscv-europe-2024.serenitycode.dev/presentation/2024-09-14-orconf-presentation.pdf

## Multiplatform CI Pipeline Lightning Talk

{{< youtube X8vGJXupbEE >}}

Besides my main talk, I also gave a lightning talk about my recent work on
overhauling the CI pipeline for the [pixman] project. In this short
presentation, I explained my approach to multiplatform CI in GitLab, which
leverages Debian as the base OS, given its fantastic support for a wide range of
platforms. I also used Docker in tandem with QEMU to seamlessly emulate all the
platforms supported by pixman.

You can check out the pipeline description [here][pipeline-code] and see the
execution in action [here][pipeline-execution]. The slides from my lightning
talk are also available [on my GitHub][lightning-slides].

See you next year at ORConf! 👋

[pixman]: https://gitlab.freedesktop.org/pixman/pixman
[pipeline-code]: https://gitlab.freedesktop.org/pixman/pixman/-/tree/277f485a9cfeb757c4627b9465bc26f3e74c1724/.gitlab-ci.d
[pipeline-execution]: https://gitlab.freedesktop.org/pixman/pixman/-/commit/277f485a9cfeb757c4627b9465bc26f3e74c1724/pipelines?ref=master
[lightning-slides]: https://riscv-europe-2024.serenitycode.dev/presentation/2024-09-14-orconf-lightning-talk.pdf
