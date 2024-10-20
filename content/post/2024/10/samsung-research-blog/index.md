---
title: "Bringing RVV to Life: Overcoming Hardware Gaps in RISC-V Development"
description: |
  My article just got published on the official Samsung Research blog 🥳

image: header.png
slug: samsung-research-blog
date: 2024-10-18 00:00:00+0000
categories:
  - riscv
tags:
  - CI
  - FPGA
  - RISC-V
  - RVV
  - open source

license: Licensed as Public Domain
---

I’m happy to share that my latest blog post, “Bringing RVV to Life: Overcoming
Hardware Gaps in RISC-V Development,” has just been published on the official
Samsung Research blog.

In this post, I dive deep into Samsung’s efforts as part of the [RISC-V Software
Ecosystem (RISE)][RISE] project, focusing on how we tackled the hardware
challenges around the RISC-V Vector (RVV) extension. We explored FPGA-based
solutions and built a multi-platform CI pipeline to improve software testing for
the RISC-V platform. It's an in-detail article about the topic I presented at
[ORConf 2024].

If you’re interested in RISC-V development or want to learn more about our
approach, feel free to [check it out][post]!

> One of the goals of the System Libraries Work Group within RISE is to extend
> support for the RISC-V Vector (RVV) extension throughout the Linux software
> ecosystem, providing significant performance and power efficiency gains for
> selected computation-heavy libraries. These include audio and video codecs,
> graphical workloads, and vector-based computations such as AI inference. As
> the first porting effort, our team selected the pixman project, which is used
> in Cairo and Chromium. Pixman has well-compartmentalized SIMD code, with
> existing implementations for multiple well-known backends, including x86 and
> ARM64 SIMD extensions.

**[Read the full article here!][post]**

[RISE]: https://riseproject.dev/
[ORConf 2024]: {{< ref "/post/2024/09/orconf" >}}
[post]: https://research.samsung.com/blog/Bringing-RVV-to-Life-Overcoming-Hardware-Gaps-in-RISC-V-Development
