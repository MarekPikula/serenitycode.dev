---
title: "Discovering NixOS: A Journey of a Self-Hosted Server Admin"
description: |
  Join me on a journey through my experience as a self-hosted server admin,
  where I share valuable lessons learned along the way. From my fascination with
  technology to maintaining school networks, experimenting with different
  distros, and settling on Fedora, I've learned three crucial pieces of advice
  for aspiring sysadmins. And now, I'm excited to share my next adventure with
  NixOS, a flexible and stable semi-rolling distro with a fully declarative
  configuration. Stay tuned for the blog post series, where I'll share my
  experience and endeavour to create a perfect NixOS-based backup server.
image: discovering-nixos.png
image_caption: Illustration by Katarzyna Foszcz
image_caption_link: https://dribbble.com/katarzyna-foszcz
slug: discovering-nixos
date: 2023-09-10 00:00:00+0000
categories:
  - history
  - nixos
  - sysops
tags:
  - CentOS
  - Fedora
  - Gentoo
  - Linux
  - NixOS
  - self-hosted
---

*This post introduces a series of articles about my experience as a self-hosted
server admin. I will cover many topics, including personal history, server
setup, service configuration, networking and (hopefully only a few)
post-mortems.*

## Where it all started

I have been fascinated with technology since I can remember. When I got my first
PC with Windows XP, I spent countless hours exploring all the apps and system
settings. I quickly became the home IT helpdesk – whenever the printer didn't
work, or there was no space left on a disk, I was there to help (although
usually not so eagerly 😜).

> I need to thank my teacher for seeing potential in me, spending all this
> time in the classroom after hours and teaching me how things work.

From these times, I also fondly remember assisting my primary school teacher
with some IT classroom issues. Be it formatting the PCs because someone loaded a
surprising amount of viruses from a Pen Drive, installing Windows connected to
the school's Windows Server 2003 box, or some general network maintenance. I can
say with all confidence that this was a crucial experience on the path to
becoming a sysadmin. I need to thank my teacher for seeing potential in me,
spending all this time in the classroom after hours and teaching me how things
work.

!["IT closet in school with old PC" – DALL·E](it_closet_in_school_with_old_pc.jpg)

Then, in secondary school, I was immediately picked by the IT teacher as an IT
assistant due to my previous experience. I helped him with school network issues
and maintained the school website hosted on a Windows Server box hidden
somewhere in a closet with a classic ISS setup. I spent most of the computer
science classes in my teacher's office configuring a new version of PHP,
installing some lovely Joomla plugins for the website or uploading photos from a
recent school trip.

## CentOS FTW

My next step on the sysadmin path was my first home server. I was still in
secondary school when one of my friends introduced me to a new game, Minecraft.
That rings a bell, doesn't it? Honestly, I'm amazed that Minecraft is still a
thriving game after all these years, with a lively community of players,
creators and modders. Anyway, we needed a server to play together, and I had an
itch to test my new-found Linux skills.

> Use RAID and do frequent backups.

There was this old laptop that was just lying around collecting dust, so I
thought I could use it as a Minecraft server. I searched the internet for what I
could use as a solid server OS, and CentOS caught my attention. After a few
failed tests, I finally got it working. There was this one little issue: it only
worked locally. I quickly needed to learn about all sorts of network caveats and
discovered for the first time what a NAT and dynamic IP is.

At last, it all worked, and I could finally enjoy an evening spent breaking and
placing blocks with my friends. Everything seemed to be working just fine until,
one day, I encountered my first server disk failure. As you might guess, the
last backup was from a month before, and the laptop had a single 2.5" HDD. Not
much could have been salvaged. Here, I learned the first and the most important
lesson for a sysadmin-to-be: **use RAID and do frequent backups**.

Later, I got increasingly invested in self-hosting. At first, it was some dodgy
Joomla blog for my YouTube channel, then came ownCloud, and all the fun began. I
had a great urge to make the services more reliable, so the natural next step
was going from on-premises to the cloud. That was when I decided to dedicate a
part of my monthly allowance for my first VPS. I remember the addictive feeling
of pure joy when I took care of a server, and it all simply worked, no matter
the internet connection or power outages, all accessible from the internet.

## Gentoo – NOT a server OS

> If it works on a desktop, it may very well not be the best choice for a server.

In high school, I got fascinated with Gentoo (similar to my current passion for
NixOS – I hope it will end better 😅). First, I installed it on my 4-core Lenovo
X230t (poor thing) and regularly fried it with chromium builds (96 ℃ overnight –
it's a miracle it still works). Gentoo compelled me because it promised perfect
configurability, optimization, and the ability to tailor the system as you see
fit. It was an ideal learning experience, and I cannot overstate its importance
for my Linux skill development. The only problem was that I came up with this
awful idea that if it works for a desktop, it will surely work for a server.

![My poor Lenovo X220t. Notice the lack of keyboard (water damage) and cracked screen. It still runs though! – photo by Author](lenovo-x220t.jpg)

You might already know where the story goes, but if not, let me enlighten you.
Gentoo is a rolling distro (no releases, always fresh software) with a rather
complicated dependency system. Long story short, when something breaks, it
breaks with a flash. I recall the immeasurable amount of time I spent trying to
fix a dependency issue on a half-working remote headless server with a broken
glibc just when (or worse, someone else) needed the services the most.

That was certainly fun, but it was fun only because I had time for it and
nothing mission-critical was hosted there. When I'm thinking about it today, I
wonder how I and the data survived it and why I came so late to the second most
important lesson for a sysadmin: **If it works on a desktop, it may very well
not be the best choice for a server**. The day I finally concluded that I was
tired of dealing with dependency hells and build errors, I thought it was time
for a change.

## The days of bliss

I needed my server to simply *work* and yearned to concentrate on the services,
not on a constant struggle to install a new package that conflicted with another
in a thousand different ways. I recalled how blissful were the days of CentOS,
and I thought to myself that I needed that back. I *really* craved the peace and
comfort of RHEL-like distro. But it wasn't all sunshine and roses. When I tried
the good ol' CentOS after Gentoo, I realized I grew very fond of Gentoo's fresh
software. I had to seek alternatives. After some back and forth, I decided to go
the Fedora way.

It was delightful. Fedora has a vast software ecosystem, frequent releases with
fresh apps and an existing alternative repository collection (be it RPM Fusion
or COPR). Still, it is reliable and maintainable, so I wasn't worried about
breaking my system with the wrong set of `USE` flags. Going with Fedora was a
choice of convenience and pragmatism. I started having less time to take care of
the server and wanted to concentrate on maintaining a good experience for people
using the services.

> Sometimes, it's cheaper to pay for SaaS than to spend time trying to make a
> self-hosted setup work.

That was also when I engaged in what would become SENT Technology company, and I
started maintaining its on-prem self-hosted cloud services (file storage, chat,
GitLab and more). I went all-in with Docker, learned a lot about cloud-native
technologies (including Kubernetes) and started to invest in Ansible to have the
server more declaratively defined. On the other side, I would say that at one
point, I overdid it and tried to self-host *everything*. It generated an
increasing maintenance burden for me at times when I should have concentrated
more on the business than on the self-hosting for the sake of self-hosting.
That's a sysadmin lesson number three: **Sometimes, it's cheaper to pay for SaaS
than to spend time trying to make a self-hosted setup work**.

## Going stable

Unfortunately, I had to withdraw from SENT Technology. I moved professionally
towards FPGA and embedded development, and because of the shifted focus, I
needed to optimize my server to require even less maintenance. I resigned from a
few extra self-hosted services and, in general, shrank the setup. What was left
was mainly a Nextcloud and private GitLab instance running under Docker on a
stable Fedora Server instance.

While my current server configuration is satisfactory, there is always room for
improvement – optimizing the setup and increasing its resilience is essential.
Recently, I went through a busy period where I had a lot on my plate, and it
made me reconsider how I want to host the services that my loved ones and I use.
It is crucial to me that we have access to reliable and secure options with as
little maintenance burden as possible.

## Flakes on the horizon

!["Calming first flakes of snow on the horizon in a server room" – DALL·E](calming_first_flakes_of_snow_on_the_horizon_in_a_server_room.jpg)

I heard about NixOS first in one of the [Jupiter Broadcasting][JB] podcasts –
[LINUX Unplugged][LUP]. The hosts advertised it as a flexible yet stable
semi-rolling distro with a fully declarative configuration. Now, as you came to
know my sysadmin background, you can probably imagine how that appealed to me
and my needs. I didn't participate in the [NixOS challenge][NixOS challenge]
organized by JB, but I stayed in the loop and cautiously, yet with keen
interest, entertained the idea of giving the distro a try.

First, I deployed a tiny VM providing Tailscale VPN access to some of my
intranet services. It all suddenly clicked. I got hooked from the start. I
suddenly realized that this is precisely how I want to run my servers. Now, it
is only a matter of one big experiment and (hopefully) one last migration.

[JB]: https://www.jupiterbroadcasting.com/
[LUP]: https://linuxunplugged.com/
[NixOS challenge]: https://www.jupiterbroadcasting.com/show/linux-unplugged/451/

## The big experiment

The big experiment I'm talking about is a backup server. You might think I've
learned nothing, and I most definitely shouldn't perform experiments on anything
touching backups. Let's say it is a backup backup server I'm talking about 😉

I must be brutally honest with myself: *I need to take backups more seriously*.
Currently, I have a working solution, but it's built from a set of self-written
scripts, lacking in areas of automatic redundancy and verification. It's
alright, but could be better. I undoubtedly consider it the most significant
shortcoming in my entire self-hosted workflow.

As for achieving inner peace with backups, I intend to have a separate server
cut off from the internet. Its sole purpose will be ensuring that all my servers
are fully backed up and performing a suite of automatic integrity checks,
pruning, and replication. All this will be built on a solid, maintainable base
of NixOS.

## Summary

I am thrilled to share my journey as a self-hosted server admin through a series
of blog posts. Over the years, I have maintained various systems, including
school networks, a gaming server and a small business on-prem cloud services. I
have experimented with different distros like CentOS, Gentoo, and Ubuntu before
finally settling on Fedora. Through my journey, I have learned valuable lessons
I want to share with aspiring sysadmins. The three pieces of advice I'd like you
to remember may not be much. Still, they go very deep into my experience as a
self-taught sysadmin and will be helpful if you're a seasoned SysOp or just
starting your journey.

**So here are the three points you should remember:**

1. Use RAID and do frequent backups.
2. If it works on a desktop, it may very well not be the best choice for a
   server.
3. Sometimes, it's cheaper to pay for SaaS than to spend time trying to make a
   self-hosted setup work.

As for what the future holds, stay tuned for the blog post series, where I'll
share my experience with NixOS, a flexible and stable semi-rolling distro with a
fully declarative configuration. I plan to discuss in detail the unique value of
NixOS, my reasons for choosing it, and, finally, my endeavour of creating a
perfect NixOS-based backup server. See you soon 👋

*Images marked with "DALL·E" are generated using [Bing Create][BC] which
internally uses DALL·E AI for image generation. The prompt used to generate the
image is written in quotes.*

[BC]: https://www.bing.com/create
