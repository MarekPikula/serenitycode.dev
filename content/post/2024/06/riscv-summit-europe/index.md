---
title: "RISC-V Summit Europe 2024 Summary"
description: |
  This week, I had the pleasure of attending the second edition of RISC-V
  Summit Europe in Munich, Germany, on behalf of Samsung R&D Institute Poland.
  On Thursday, I had an opportunity to present my work as a poster:
  “Accelerating software development for emerging ISA extensions with
  cloud-based FPGAs: RVV case study.”
image: riscv-summit-europe.jpg
slug: riscv-summit-europe
date: 2024-06-29 00:00:00+0000
categories:
  - conference
  - riscv
  - fpga
tags:
  - conference
  - RISC-V
  - FPGA
  - cloud
  - AWS
  - RVV
---

This week, I had the pleasure of attending the second edition of **RISC-V Summit
Europe** in Munich, Germany, on behalf of **Samsung R&D Institute Poland**. On
Thursday, I had an opportunity to present my work as a poster: *“Accelerating
software development for emerging ISA extensions with cloud-based FPGAs: RVV
case study”* – you can read more about it in the [Poster](#my-poster) section.

It was my first in-person RISC-V Summit – before, I was present remotely at the
RISC-V Summit 2022 – and let me tell you, it was great to see first-hand how the
RISC-V community continuously grows and becomes a driving force for today’s
computing.

> The attendees (over 720 of them) had an opportunity to listen to over 25 hours
> of talks and demos and engage with companies in the expo hall.

The conference took place in the MOC Event Center in Munich from Tuesday to
Thursday, with side events on Monday and Friday. The attendees (over 720 of
them) had an opportunity to listen to over **25 hours of talks and demos** and
engage with companies in the expo hall. In addition to that, each day, there was
a new set of posters (**over 140 submissions** in total!), so you had a chance to
personally speak with people presenting the latest and greatest of
RISC-V-related developments on new ISA extensions, IPs, hardware, and software.
Great stuff!

![Banner on the entrance to MOC Conference Center.](entrance.jpg)

## General impressions

I must say that I was positively surprised by how dynamically the RISC-V
ecosystem is evolving. In 2022, I felt that the main focus was getting the RVV
(RISC-V Vector) extension ratified, applications in automotive and HPC, and some
AI-related use cases. This year, I had an impression that heterogeneous
computing with AI/ML was in the spotlight, followed by (now ratified) RVV
support throughout the stack and security-focused talks and posters. Sure, there
were some HPC and automotive/space submissions, but I think that much less than
in 2022. Overall, even though the RISC-V ecosystem is stabilizing, it’s still
moving fast to catch up to the long-established competition or explore new and
shiny compute workloads.

Moreover, it was very pleasing to see an increase in software-related topics,
which is proof of the RISC-V ecosystem getting more mature. I would say that
it’s still much too little, but slowly and surely, we’re getting there.

## Vectors, Vectors everywhere

Presently, I’m mainly invested in work related to the RVV extension, so it was
exciting to see how it gained industry adoption. The specification was ratified
in December 2021, but we only started seeing some actual hardware and tier-1
support in compilers and toolchains this year.

From the hardware standpoint, we had both IP presentations (like the
[XiangShan] core) and physical boards and computers. It was great to
be able to interact with the first-of-a-kind [DC-ROMA RISC-V Laptop II]
featuring 8-core, RVV-capable [SpacemiT K1 SoC] (it’s the same one as
in the new [BananaPi BPI-F3] board). Deep Computing also presented a
motherboard compatible with the [Framework Laptop 13].

On the toolchain side, there was a prominent presence of both LLVM and GCC
developers who work on RISC-V-related optimizations, and autovectorization
support (I can’t wait to try out the new GCC 14).

[XiangShan]: https://github.com/OpenXiangShan/XiangShan
[DC-ROMA RISC-V Laptop II]: https://deepcomputing.io/product/dc-roma-risc-v-laptop-ii/
[SpacemiT K1 SoC]: https://docs.banana-pi.org/en/BPI-F3/SpacemiT_K1
[BananaPi BPI-F3]: https://docs.banana-pi.org/en/BPI-F3/BananaPi_BPI-F3
[Framework Laptop 13]: https://frame.work/pl/en/products/deep-computing-risc-v-mainboard

![One of the hardware exhibition tables with DC-ROMA RISC-V Laptop II.](roma.jpg)

## AI hype train and security

It was hard not to notice how much RISC-V’s AI/ML applications have become a
focus point for many companies over recent years. During the summit, many
presentations touched on the topic from the purely architectural perspective
(ISA extensions vs. separate specialized coprocessors) but also on the software
side, with a focus on integrating the various extensions and accelerators in the
existing ecosystem (e.g., [oneAPI], [SYCL]).

I appreciate how much importance the RISC-V community puts on the platform’s
security aspects. Here, I’m talking about the verification aspect, functional
safety, and new specifications (there were a LOT of presentations about [CHERI]
and other protection mechanisms). Shout out to my colleague Piotr Lipiak, who
presented a poster titled *“Enhancing SecureOS porting to RISC-V architecture
using hypervisor.”*

[oneApi]: https://www.oneapi.io
[SYCL]: https://sycl.tech
[CHERI]: https://github.com/riscv/riscv-cheri

## My poster

![Hi there! It's me!](poster.jpg)

As mentioned in the beginning, I had an opportunity to present my work during
the summit in the form of a poster about *“Accelerating software development for
emerging ISA extensions with cloud-based FPGAs: RVV study.”*

I was involved in open-source RISC-V-related tasks at Samsung for the last two
years. Last year, it was porting the [Tizen OS] to RISC-V; this year, we’re
concentrating on software optimization tasks for some core libraries. The main
topic is RVV (RISC-V Vector) extension support, and we chose [pixman] as the
first library to port, as there was no existing upstream effort, and the library
was used in some essential parts of Tizen (e.g., Chromium, Cairo).

> When the RVV porting effort was started, there was no RVV1.0-capable hardware
> available on the market.

When the RVV porting effort was started, there was no RVV1.0-capable hardware
available on the market. Sure, some were with RVV0.7 support, but it wasn’t our
target. Everyone on the project was learning how to write a good quality RVV
code, but there were no easy ways to benchmark it – QEMU is suitable for
correctness verification but not for measuring performance (at the time, it even
had a 2× slowdown compared with scalar code). That’s when I came up with the
crazy idea to take an open-source IP and deploy it on an FPGA with the primary
goal of creating multiple RVV-enabled environments with various configurations
(e.g., VLEN and lane count).

[Tizen OS]: https://www.tizen.org
[pixman]: https://pixman.org/

### Hardware stack

It was a small, experimental project, so spending $10k on a large enough FPGA
and Vivado license was not an option. The alternative was to use [AWS EC2 F1]
instances with VU9P FPGA (which is a beast), which cost $1.734 per hour.

The second layer was the [FireSim] framework, which is a cycle-accurate
simulation platform that can be run either in software (Verilator) or in
hardware, be it an in-house FPGA or F1 cloud instance. The great thing about
FireSim (and [Chipyard], which is the SoC-like hardware integration platform) is
that it provides you with the entire tooling from setting up AWS through
automated FPGA synthesis to running custom workloads.

As for the core itself, I went with [PULP Ara], which is a coprocessor to
[CVA6]. It promised full RVV1.0 support, and there was MMU support in
development. Actually, I just about didn’t have any other options – at the time,
the only other RVV1.0-capable open-source cores were [Tenstorrent Ocelot] (which
isn’t FPGA-friendly), [PULP Spatz] (which is not designed to be fully
RVV1.0-compliant), and [T1 core] from CHIPS Alliance (which doesn’t have MMU
support). I settled on the officially supported VLEN=2024 and two lanes for the
initial test configuration.

[AWS EC2 F1]: https://aws.amazon.com/ec2/instance-types/f1
[FireSim]: https://fires.im/
[Chipyard]: https://github.com/ucb-bar/chipyard
[PULP Ara]: https://github.com/pulp-platform/ara
[CVA6]: https://github.com/openhwgroup/cva6
[Tenstorrent Ocelot]: https://github.com/tenstorrent/riscv-ocelot
[PULP Spatz]: https://github.com/pulp-platform/spatz
[T1 core]: https://github.com/chipsalliance/t1

### The results

Fast forward a few months, I had a working PULP Ara integrated into the FireSim
framework on AWS F1 cloud FPGA. Now, it was time to do some actual benchmarks. I
used a really nice RVV benchmark suite from Olaf Bernstein called [rvv-bench].
Besides the “real-life” benchmarks (like UTF encoding, memcpy, and such), it has
an instruction tester that measures the cycle count of all vector instructions
in different variants. This information can be beneficial when writing a
hand-optimized algorithm. Sure, it’s not the only thing in play, as depending on
the microarchitecture the entire instruction chain can have different
performance. Still, it gives you a general overview of how the core is
performing.

> For my RGB565 to RGB888 conversion algorithm, I measured a 10× speedup for
> PULP Ara, which is interesting to see, as the same benchmark on CanMV-K230
> resulted in only a 2.5× performance increase.

Unfortunately, Ara is buggy in my configuration. Only about 75% of instructions
worked, with others resulting in either instruction errors or outright processor
hangs. Upstream efforts are being made to fix some issues (e.g., [*Initial
support for OS* PR][mmu]), but, at least for now, the core is definitely not
production-ready.

Finding this out was unfortunate, but it didn’t stop me from doing some
benchmarks on the pixman code. For my RGB565 to RGB888 conversion algorithm, I
measured a 10× speedup, which is interesting to see, as the same benchmark on
CanMV-K230 (2 lanes, VLEN=128) resulted in only a 2.5× performance increase.
This shows how much the VPU microarchitecture affects code performance.

[rvv-bench]: https://github.com/camel-cdr/rvv-bench
[mmu]: https://github.com/pulp-platform/ara/pull/311

### Conclusions

Presently, running Ara on FPGA to develop RVV software slowly stops making sense
as real hardware targets appear on the market. On the other hand, I would argue
that the approach presented in this work could be really useful for bridging the
gap between extension ratification and hardware availability.

> It would be great if, as part of the ratification process, there was a
> requirement to have a public reference implementation ready for use from day
> one.

During the conference, many presenters voiced concern about how we, as a
community, expect software engineers to port to emerging RISC-V ISA extensions
if no hardware is available to test it on. Sure, for some things, QEMU is just
fine, but for performance-focused extensions like RVV or the upcoming matrix
multiplication extensions, it’s crucial to have some hardware to learn the
intricacies of the new instructions and benchmark the code.

It would be great if, as part of the ratification process, there was a
requirement to have a public reference implementation ready for use from day
one. It doesn’t need to be open source; it can be an encrypted RTL or an AWS F1
image (which you cannot download to reverse engineer). I know that it would be
challenging to sell it to all the involved hardware vendors, but hey, one can
dream 😉

If you want to see more details about the project, go to the [project’s
website][project] or [GitHub] to see the original abstract, poster, code, and
benchmarks.

[project]: https://riscv-europe-2024.serenitycode.dev
[GitHub]: https://github.com/MarekPikula/RISC-V-Summit-Europe-2024
