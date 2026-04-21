---
title: "Sending My First Linux Kernel Patch"
date: 2026-04-21 16:30:00 -0300
categories: [Development, Open Source]
tags: [free software, learning, linux kernel, amdgpu]
---

## Goals
In this task, the goal was to finally send my first code contribution to the Linux Kernel. The patch was a refactoring to deduplicate a function (`ring preempt ib`) in the AMDGPU driver. More than 
just writing the code, the main goal was to understand the entire workflow of submitting a patch using Kworkflow (`kw`), dealing with email configurations, and interacting with the community. The ring
preemption function was identical for both gfx_v11_0 and gfx_v12_0, so my patch refactors the code by moving the core logic into a generic function inside amdgpu_gfx.c to reduce code duplication and 
simplify future maintenance.

## Experience Summary
The process of sending a patch involves many steps outside of just coding. First, I had to configure my email to work with `git send-email`. It took some tries because of Google's OAuth2 and some 
missing SASL packages in my system, but it eventually worked and I was able to send the email.
After sending the patch to a test list, a CI robot tested my code. The compilation passed, but the VM gave a Kernel Panic during boot. To find out what happened, I used `kw build` and `kw deploy` to 
test my patched kernel locally in a virtual machine (KVM). The local boot worked perfectly. By reading the CI logs, I discovered the panic was caused by a broken `initramfs` in their test environment,
not by my code!
Finally, I sent the patch to the real AMD maintainers. Very quickly, I got a reply from Alex Deucher, an important maintainer. He asked me to remove the wrapper functions and just replace the old 
functions directly. Now, I am getting ready to send the v2 of this patch.
