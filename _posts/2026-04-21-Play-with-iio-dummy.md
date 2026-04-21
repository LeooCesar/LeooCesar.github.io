---
title: "IIO Dummy module Experiment One: Play with iio_dummy"
date: 2026-04-02 21:50:00 -0300
categories: [Development, Open Source]
tags: [free software, learning, linux kernel, iio]
---

## Goals
In this tutorial, the goal was to finally deploy and test our iio_dummy sensor module inside an ARM64 QEMU virtual machine. Unlike previous theoretical studies, this was a hands-on session aimed at 
mastering the development cycle using Kworkflow (kw). The objective was to compile the kernel module on the host machine, send it to the VM using kw deploy, and load it into the kernel using kw ssh 
and modprobe.

## Content Summary
If I had to summarize this session in one word, it would be: Debugging. The theory is always cleaner than practice, and this tutorial was a raw lesson in how the Linux kernel ecosystem actually 
operates. Initially, I struggled with basic connectivity. kw ssh couldn't reach the VM because I was mixing up isolated QEMU scripts with libvirt background networks. Once inside, I mistakenly tried 
to run make modules_install directly in the VM, which taught me an important architectural lesson: test VMs are minimal environments. They don't have build tools; the compilation must happen on 
the Host. Transitioning to Kworkflow brought its own set of challenges. My first kw deploy failed spectacularly with strip errors. This happened because my Host (x86) was trying to process files for 
the VM (ARM64) without the proper cross-compilation environment variables (ARCH and CROSS_COMPILE). Even after fixing the environment and successfully deploying, modprobe iio_dummy failed. Why? 
Because I had skipped the kw build step! The configuration (.config) was perfect, but the actual .ko files were never generated. Finally, after successfully building and deploying the modules, the 
kernel rejected the driver with an Unknown symbol (irq_domain_remove_sim) error. Checking dmesg revealed the ultimate catch: the VM had received the updated kernel files but was still running the old
kernel in its RAM. Rebooting the VM to load the new kernel resulted in a completely unreachable machine and a blank serial console—likely a Kernel Panic or a network interface failure on the new 
build.
