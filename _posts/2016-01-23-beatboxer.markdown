---
title: "🎶 Beatboxer on an Embedded System"
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

Beatboxer lets a user playback some pre-made beats, or create their own!  Beatboxer runs on physical hardware and connects your local network allowing for control by hand or by web.

Here's what the whole system looks like:

![Screenshot](../assets/images/beatboxer.png)

This project touched on a huge range of abstractions - from reading individual bytes in registers to showing content on the frontend.

Getting the *MMA8452Q accelerometer* working was a little challenging.  The first 8-bit register you read in C is always `0xFF`.  To read something you care about (like x-y-z coordinates), you need to read multiple registers in one go with an 8-bit offset, to get an array of bytes.  Each coordinate is stored as a 16-bit value across two registers - the LSB and MSB bits.  By default, reading multiple bytes will skip the LSB, so you also need to write to other registers so this is turned off!

The audio was done using the ALSA C API.  Pushing the joystick will queue new PCM samples for playback.  A thread will load the samples into memory, and another thread will play them back.  A third (heartbeat) thread will send/receive the current beat over UDP to the node web server so it can be displayed and controlled from the frontend!

Here's what it's like to use:

<iframe width="560" height="315" src="https://www.youtube.com/embed/xLffg8iiZPw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---

Stuff used:

- C
    - Multithreading
    - UDP networking
    - Bit-twiddling
    - ALSA
- Web sockets
- NodeJS
- Jquery
