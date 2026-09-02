---
layout: ../layouts/BaseLayout.astro
title: "Getting Started"
show: True
order: 1
---

### Join [#solder](https://hackclub.slack.com/archives/C08L288G22Y) on Slack!

If you're not already on the Hack Club Slack, get in here: https://hackclub.com/slack/ - join thousands of other technical teens, ask for help, and learn about the latest Solder updates!

When you finish your project, you'll also need to post it in the [#solder-ships](https://hackclub.enterprise.slack.com/archives/C08N2CN8E2C) channel. Join it and check out what others are making!

### What's a PCB?

PCB stands for printed circuit board!

It's a board that links all the electronics together via copper wires that run through it. Think of it as a breadboard - but the wires are built into it and all you need to do is _solder_ your components on.

See also: [SparkFun's article](https://learn.sparkfun.com/tutorials/pcb-basics/all) explaining PCBs!

Here are some PCBs made by hack clubbers:

![](/pcb-examples.png)

### KiCad Quick Start

Complete beginner? No worries!

This tutorial aims to teach you how to design a PCB from scratch.

To design PCBs, we use **KiCad**! It's free and open source. **Download it here: https://www.kicad.org/download/**

If you're not able to download anything, [EasyEDA](https://easyeda.com/) is a web-based alternative.

**After downloading KiCad:**

Open up the app, and you will be presented with a small popup; click apply. And now you are presented with the main menu.

You first need to create a new project: Go to File &gt; New Project and create it. It should look like this:

![](/tutorial/start.png)

If it looks like that, congrats - you've just started your first PCB project!

### Kit Contents

Here are the parts you get!

* 1x 555 Timer
* 6x 5mm LED (various colors)
* 24x resistors (12x 220Ω, 6x 4.7kΩ, 6x 47kΩ)
* 15x 2N3904 transistor
* 15x 2N3906 transistor
* 1x mini motor disc
* 1x photoresistor
* 2x 10uF capacitor
* 10x 6mm push button
* 2x potentiometer
* 1x breadboard
* 15x jumper wires
* 2x CR2032 battery cell holders

Note you'll need to get your own coin cell batteries (those are harder to ship), but the CR2032 is pretty common!

### PCB Design Requirements

This program doesn't use any form of time tracking to approve projects. However, projects do need to meet a minimum quality criteria in order to pass!

- the PCB needs to be original
- the PCB needs to fit within 100x100mm
- use the components given in the kit

The PCB is expected to have a custom outline / cool silkscreen, unless it is intentionally rectangular to fit a more technical circuit (ie: something with lots of logic gates). That means your PCB should:

- have a custom outline
- have rounded corners
- include silkscreen art (and/or text) on both sides
- be intentional with part placement

Here are examples of PCBs that would be approved:

![](/pcb-examples-good.png)

And here are examples of PCBs that would be rejected / require changes before resubmitting: 

<img src="/pcb-examples-bad.png" style="max-height: 100px;" />

Please be creative! Make something you'd actually want to look at / put on display / use as a keychain or badge.
