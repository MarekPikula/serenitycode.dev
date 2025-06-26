---
title: "RISC-V Summit Europe 2025 Summary"
description: |
    I recently attended RISC-V Summit Europe 2025 in Paris, representing Samsung
    R&D Institute Poland. On Thursday, I presented a poster titled “Enabling
    RISC-V CI in Open-Source Projects: Challenges and Solutions” – an effort to
    streamline continuous integration for RISC-V in Freedesktop.org projects
    using Docker and QEMU.
image: conference-center-1.jpg
slug: riscv-summit-europe-2025
date: 2025-06-26 00:00:00+0000
categories:
  - conference
  - riscv
tags:
  - conference
  - RISC-V
  - CI
  - Docker
  - QEMU
  - open-source
---

Last month, I had the opportunity to attend [**RISC-V Summit Europe
2025**][rv-summit] in Paris, representing **Samsung R&D Institute Poland**. On
Thursday, I presented a poster titled *“Enabling RISC-V CI in Open-Source
Projects: Challenges and Solutions”* – you can find more details about it in the
[My Poster](#my-poster) section below.

Following the summit in Munich last year, it was encouraging to see how the
RISC-V ecosystem continues to evolve. From the variety of advanced topics –
spanning automotive, HPC, and AI – to the growing emphasis on developer tooling
and platform integration, 2025 felt like a year in which the RISC-V ecosystem
continued to mature across the stack, even if the software infrastructure is
still catching up.

***Side note:** I’ll be presenting a summary of the RISC-V Summit Europe 2025 as
a lightning talk during the [FPGA FIRE Workshop][fire] in Utrecht on June 27th,
2025. I uploaded a [slide deck][fire-slides] with more talk highlights.*

![Inside the conference center.](conference-center-2.jpg)

> The summit gathered hundreds of attendees for three packed days of talks,
> tutorials, demos, and posters in the heart of Paris.

[rv-summit]: https://riscv-europe.org/summit/2025
[fire]: https://hwacc-nl.github.io/2025/06/16/event-announcement-update.html
[fire-slides]: https://github.com/MarekPikula/Conferences/blob/main/2025/2025-06-27%20FIRE%20Workshop/RISC-V%20Summit%20Europe%202025%20Summary.pdf

## General impressions

Compared to last year’s event, I noticed a stronger emphasis on tooling maturity
and cross-domain deployment. While the AI/ML and custom accelerator wave
continues, there was a marked increase in presentations that focused on
practical engineering work: reproducibility, CI/CD integration, and developer
tooling.

In addition, several talks explored the intersection of RISC-V and critical
domains such as space, automotive, and security – showing growing confidence in
deploying RISC-V beyond labs and into real-world applications.

## My poster

![Standing next to my poster in Paris.](poster.jpg)

This year, I presented my work on *“Enabling RISC-V CI in Open-Source Projects:
Challenges and Solutions,”* which I’ve been working on for quite some time at
Samsung. The motivation behind the project was simple: while RISC-V adoption is
growing, most upstream open-source projects (in our case, those hosted on
[Freedesktop.org]) still lack **automated CI testing for RISC-V**. This makes it
harder to validate architecture-specific contributions, especially for
performance-critical SIMD and RVV (RISC-V Vectors) code.

At Samsung R&D Institute Poland, we tackled this by designing a **QEMU-based
GitLab CI template framework** that allows testing across multiple architectures
– RISC-V included – without needing dedicated hardware.

> The approach uses Docker-based runners, native toolchains (both GNU and LLVM),
> and multi-architecture images to support RVV and other SIMD backends across
> platforms.

We first rolled this out for [Pixman], a pixel manipulation library used by
Cairo and some Wayland compositors, where we added RVV SIMD support and
uncovered several bugs through automated CI. From there, we are in the process
of applying the same model to [GStreamer Orc], which dynamically compiles
vectorized media pipelines, and in the future to [Opus], a widely-used audio
codec.

The CI templates are modular and reusable, allowing projects to run native tests
on supported architectures using Docker and QEMU – all integrated into GitLab’s
pipelines. The pipeline generates a unified coverage report for all platforms
using the gcovr tool, which greatly improves test visibility and bug triaging.

> For RVV in particular, testing across multiple **VLENs** exposed subtle
> configuration-specific issues that would have gone unnoticed in manual
> testing, especially with the limited amount of hardware available on the
> market.

This work shows how relatively small infrastructure changes can have a large
impact on open-source contribution velocity and software robustness for emerging
architectures like RISC-V.

If you’d like to dive into the technical details or reuse our approach,
everything is publicly available on [GitHub][poster], and the template itself is
hosted (for now) on [FDO’s GitLab][ci-fdo].

[Freedesktop.org]: https://freedesktop.org
[Pixman]: https://pixman.org
[GStreamer Orc]: https://gitlab.freedesktop.org/gstreamer/orc
[Opus]: https://gitlab.xiph.org/xiph/opus
[poster]: https://github.com/MarekPikula/RISC-V-Summit-Europe-2025
[ci-fdo]: https://gitlab.freedesktop.org/MarekPikula/ci-multiplatform/

## Hardware

This year’s expo floor featured a wide range of RISC-V hardware – from compact
microcontrollers and SoCs to full development boards and AI-capable edge
devices. The DeepComputing booth showcased their latest DC-ROMA RISC-V AI PC and
a motherboard for the Framework Laptop. It’s clear that the hardware ecosystem
is becoming more diverse and deployment-ready. Below, I’ve included a few photos
of the hardware, courtesy of my colleague from Samsung, [Filip Wasil].

![Hardware demo area](hw/hw-1.jpg) ![ESWIN booth](hw/hw-2.jpg)

![DeepComputing AI PC](hw/hw-3.jpeg) ![DeepComputing Framework motherboard](hw/hw-4.jpeg)

![Raspberry Pi Pico 2](hw/hw-5.jpeg) ![BananaPi BPI-F3](hw/hw-6.jpeg)

[Filip Wasil]: https://www.linkedin.com/in/filip-wasil-b4a487104/

## Presentation highlights

As always, the conference featured an excellent lineup of speakers representing
academia, industry, and open-source communities. While it’s impossible to cover
everything, here are some of the talks and sessions that stood out to me –
either for their technical depth, unique perspective, or practical relevance to
RISC-V adoption.

### RISC-V State of the Union

{{< youtube vThTOrV0brk >}}

A keynote-level update from one of RISC-V’s founders. Krste Asanović, Chief
Architect at SiFive, reflected on how far the ecosystem has come since the ISA’s
inception (this year marks the 15th birthday of RISC-V!) and laid out a
forward-looking strategy for growth. He touched on RISC-V profiles, DSP
extension improvements, documentation cleanup, and early work on long
instructions.

### The RISE Project: Advancing RISC-V Software

{{< youtube XQz7AtnbPzI >}}

This joint talk by Nathan Egge (Google) and Ludovic Henry (Rivos) is especially
close to my heart, as I’m part of the [RISE] project within Samsung. The
presentation offered updates on RISC-V software enablement, the open-source
contribution awards program, and new training materials (with optional
certification). A great summary of the software community’s progress.

[RISE]: https://riseproject.dev

### The Significance of the RVA23 Profile in Advancing RISC-V Ecosystem

{{< youtube VJ2bkXZ5Cog >}}

Mark Hayter (Rivos) discussed the current state of RISC-V profiles and their
roadmap. He introduced RVM23 for embedded systems and hinted at RVA30 as the
next major milestone. Until then, RVA23 will get minor updates with optional ISA
extensions. This talk is a great primer if you’re still unfamiliar with how
profiles simplify platform compatibility and software development.

### RISC-V: Powering the Future of High Performance Computing?

{{< youtube l3SGGMlL-4s >}}

Nick Brown, chair of the HPC SIG at RISC-V International, spoke on the
importance of open standards in HPC. He mentioned the free-access RISC-V HPC
lab, discussed hardware readiness and challenges for RISC-V adoption.

### RISC-V: Reaching New Orbits in Space Computing

{{< youtube j7KVb2gGVgA >}}

Lucana Santos from the European Space Agency (ESA) gave a compelling talk on
ESA’s shift from SPARC to RISC-V SoCs. She discussed their goals for the next
generation of space-grade chips – improved performance, AI/ML support, DSP
capabilities, and enhanced fault tolerance. In her view, RISC-V hasn’t just
started taking over in space – it already has.

### Flex-RV: World’s First Non-silicon RISC-V Microprocessor

{{< youtube IjZXPOQnRFQ >}}

This talk introduced Flex-RV, the world’s first RISC-V processor built using a
non-silicon, (literally) flexible semiconductor process. It’s really cool to see
RISC-V being used on the forefront of new semicon technologies.

## Closing thoughts

It’s been great to reconnect with familiar faces from past years and see new
contributors join the RISC-V community. Each year, the Summit feels more
professional, more collaborative, and more diverse in terms of domains and
applications.

I’m already looking forward to the next edition in Bologna – and in the
meantime, I’ll be continuing this CI enablement work and hopefully expanding it
to even more projects and use cases.
