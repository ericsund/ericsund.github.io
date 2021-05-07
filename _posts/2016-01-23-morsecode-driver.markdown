---
title: "💡 Linux Driver to Flash Morsecode"
layout: post
date: 2021-04-1 22:10
tag: C
image: https://sergiokopplin.github.io/indigo/assets/images/jekyll-logo-light-solid.png
headerImage: false
projects: true
hidden: true # don't count this post in blog pagination
description: "This is a simple and minimalist template for Jekyll for those who likes to eat noodles."
category: project
author: johndoe
externalLink: false
---

"Morse Driver" is a misc driver that runs on a custom Linux kernel.

In Linux, hardware interaction is exposed via device driver files.  Writing a string to `/dev/morse-code` will flash an onboard LED with the morse code equivalent.  Reading will spit out the dot/dash equivalent of your strings in text.  This is all stored in the kernel's FIFO queue.

This was a neat project where I got to learn about:

* Building Linux drivers, of course
* Modifying and copmiling a custom Linux kernel
* Booting a device tree and kernel via TFTP with UBoot
* Bit twiddling and masking
* -- --- .-. ... . / -.-. --- -.. . -.-.--

Here's a demo:

<iframe width="560" height="315" src="https://www.youtube.com/embed/OSjaFn4PI-o" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---

Stuff used:

- C
- Bit manipulation and masking
- Kernel FIFO queues