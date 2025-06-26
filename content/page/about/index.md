---
title: About me
date: 2022-03-07
slug: about
menu:
  main:
    weight: 2
    params:
      icon: user
---

> FPGA developer by day, DevOps engineer by night.
>
> I strive to create high-quality, well-tested and documented solutions in
> established technologies while actively exploring the new and shiny. Deeply
> in love with functional programming (Scala ❤️) and declarative UI development
> (Flutter 👌). For tooling, automation, Docker and CI, I'm your man.
>
> I feel the best in complex projects requiring both system-level and in-detail
> perspectives, connecting multiple domains from hardware through gateware and
> firmware up to the software. There's nothing better than a perfectly
> integrated project delivered on time that serves the client's needs.
>
> In my spare time, I like to play tennis. I also have lots of 3D printing
> experience, which I gladly share, and a deep interest in space exploration
> and cutting-edge technologies.

## Notable professional projects

### Blackwire – 100G WireGuard smart NIC on FPGA

Part of a team developing a transparent WireGuard smart NIC achieving speeds up
to 100Gbps. Main focus on the [Scalable Pipelined Lookup][Blackwire Lookup] IP
core providing fixed-latency IP address lookup and CI setup.

Open-sourced [on GitHub][Blackwire GitHub]. You can read more about the project
[here][Blackwire LinkedIn].

<small>01.2023—05.2023 at BrightAI<br>
**Tech:** SpinalHDL, SystemVerilog, Xilinx Vivado, Wireguard, PCI-E, Docker,
GitLab CI </small>

[Blackwire Lookup]: https://github.com/brightai-nl/scalable-pipelined-lookup-fpga
[Blackwire GitHub]: https://github.com/brightai-nl/BrightAI-Blackwire
[Blackwire LinkedIn]: https://www.linkedin.com/pulse/open-sourcing-blackwire-wireguard-vpn-protocol-fpga-100-oerlemans

### Components for Curium One satellite

![](curiumone.png) Lead embedded Linux and FPGA engineer in a project involving
acquisition of 360° in-orbit images, video pipeline scheduling, and interfacing
with a satellite communication module. Development of the Linux driver for the
camera, system architecture and CI setup. Involved in communication with the
client.

<small>01.2022—10.2022 at [Embevity][Embevity]<br>
**Tech:** SpinalHDL, C (Linux), Python, Lattice Diamond, Nvidia Jetson, MIPI
CSI-2, SLVS, Docker, GitLab CI </small>

### PocketGourmet – a multi-platform café app

![](pocketgourmet.png) PocketGourmet is a customizable app/mobile website for
small cafés and restaurants.

I was a technical lead, developing a universal app in Flutter along with a
Python backend (FastAPI) and managing cloud services including the Firestore
database and CI/CD.

<small>11.2021—06.2022 at SENT Technology<br>
**Tech:** Flutter, Python, FastAPI, Firestore, CI/CD </small>

### Labyrinth Drives – encrypted SSD drive

![](labyrinthdrives.jpg) Lead firmware and test engineer for security system
based on an SSD with NIST-compliant hardware encryption and equipped with
several unique functionalities (BLE, LTE, GPS). Involved in system architecture
specification, low-level driver development, and CI setup in hardware-in-loop
methodology in Python. Firmware development in MicroPython and embedded C on
Zephyr RTOS.

<small>06.2021—12.2021 at [Embevity][Embevity]<br>
**Tech:** Embedded C, Zephyr, (Micro)Python, STM32, nRF52, TF-M, CMake, Docker,
GitLab CI </small>

### Medical and industrial imaging equipment

![](x-ray.jpg) Embedded Linux and FPGA developer in a design for high-speed
industrial and medical X-ray imaging equipment with 10G Ethernet.

<small>12.2020—06.2021 at [Embevity][Embevity]<br>
**Tech:** VHDL, C++, Xilinx Vivado, Docker </small>

### Dirac Farm – a scalable 3D printer farm control system

System specification connecting all layers of the system: server, networking,
driver board, driver module. Detailed specification and prototype work on 3D
printer driver based on Xilinx Zynq, connecting ARM microprocessor and FPGA
fabric. Stepper motor module prototype development including basic G-code
interpreter, S-shaped curve motion planner, stepper IC driver signal generator
and entire module board.

<small>04.2017—02.2022 at SENT Technology<br>
**Tech:** Verilog, SpinalHDL, embedded C++, motion control, Xilinx Vivado, PCB
design </small>

## Notable open-source contributions

### [Headscale-WebUI](https://github.com/iFargle/headscale-webui)

Headscale frontend written with Flask. I was part of a major refactor effort,
resulting in better quality and more understandable code.

<small>04.2023—present<br>
**Tech:** Python, Flask, OIDC </small>

### [SystemRDL/PeakRDL](https://peakrdl.readthedocs.io/en/latest/)

PeakRDL is a free and open-source control & status register (CSR) toolchain
based on [Accellera's
SystemRDL](https://www.accellera.org/downloads/standards/systemrdl) register
descriptions. I have contributed some PeakRDL exporter plugins
([Markdown](https://github.com/SystemRDL/PeakRDL-Markdown),
[Python](https://github.com/MarekPikula/PeakRDL-Python-simple)).

<small>10.2022—present<br>
**Tech:** Python, SystemRDL, FPGA </small>

### [Xournal++](https://xournalpp.github.io/)

Linux-native handwriting notepad. I took part in effort of transitioning from
GTK+ 2 to 3, from Autotools to CMake and was responsible for UTF-8 string
handling refactor.

<small>03.2015—06.2016<br>
**Tech:** C++, GTK+, CMake, Autotools </small>

[Embevity]: https://embevity.com/
