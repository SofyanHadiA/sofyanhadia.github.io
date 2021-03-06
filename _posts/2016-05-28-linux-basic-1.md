---
layout: post
title: Linux Basic - Kernel
categories: [os]
tags: [linux, os]
fullview: false
comments: true
---
What is the Linux Kernel? Let's talk about it. Well, the kernel is a program. 
The kernel program has a name. That name is often something like vmlinuz-. Maybe, vmlinuz-3.1.1. 
That program needs to be loaded into memory and run, and that operation is done by a bootloader. 
With Linux, we often have a bootloader called GRUB. 

So, GRUB reads the kernel file from disk into memory, and will transfer control to it.
The kernel program, like other programs, has command-line parameters, and GRUB is responsible for passing those parameters to the kernel. 
The Linux kernel is an API. It provides a programming interface. The functions that we can call from user space into the kernel we call system calls. But the Linux kernel also provides virtual file systems, proc and sys and the lesser-known debugfs, and through those virtual file systems, we can interact directly with the kernel, getting information from the kernel, and changing things in the kernel.

Also, our file system has device files. We interact with device drivers by doing operations on those device files. Those are standard system calls, like read and write and open. The kernel is a gatekeeper. The kernel enforces privileges. In Linux, we call those privileges capabilities. In the Linux kernel sourcecode, it refers to checking the capabilities of a process to see if it allowed to perform some sort of privilege operation. 

We think of root processes having all the privileges. More precisely, root processes typically have a large set of capabilities. Also, CPUs have special instructions that only are allowed to be executed when the CPU itself is in a special supervisor mode. It's in that mode when we're executing inside the kernel. So, that means there are assembly-language instructions that only can be executed by the kernel. The Linux kernel also implements a number of security policies. 
The underlying mechanisms used by SELinux, for example.
And finally, the kernel provides controlled access to hardware and other resources. It wouldn't be safe, say, to allow processes to willy-nilly access the disk at will. No, the kernel has to provide controlled access, to make sure that things are done in an orderly and safe manner. The kernel is modular. The kernel image itself, that vmlinuz file, is relatively small, just a few meg. 

The kernel image, though, is sufficient to boot to user space, to begin running some processes.
Once we have processes, we can load additional functionality into the kernel through the loadable kernel module mechanism. The loadable module mechanism means we can just load the drivers that we need. We don't need to load drivers for hardware that's not present.
