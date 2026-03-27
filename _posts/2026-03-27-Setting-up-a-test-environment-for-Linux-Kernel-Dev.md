---
title: "Setting up a test environment for Linux Kernel Dev using QEMU and libvirt"
date: 2026-03-27 10:00:00 -0300
categories: [Development, Open Source]
tags: [free software, learning]
---

## Goals
In this tutorial, the goal was to get used to a virtual test environment for Linux Kernel. Since our main goal is to submit patches to the Linux Kernel current code, by setting up this environment, we will be able, in the future, to test our updates before submitting them.

## Problems and Difficulties
Because it was my first time setting up an environment, I had some problems understanding what was happening in each step. The part of environment customization wasn't difficult by itself, but understanding if the command I was using was supposed to be on my normal terminal, on LK-DEV, or on my virtual machine root@localhost was confusing in the beginning.

Some other small problems I had were:
- Adapting commands from arm64 architecture to amd64 architecture
- Working on activate.sh and changing its lines
- Working on ssh using my IP (I don't know if it was because of it, but, since I did this first tutorial in two different days, my IP changed in the middle of it, causing confusion for me)
