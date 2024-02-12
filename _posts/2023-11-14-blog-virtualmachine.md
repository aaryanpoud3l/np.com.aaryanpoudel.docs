---
title: "Virtual Machine"
date: 2023-11-14T11:54:24+05:45
categories: ['Blogs']
tags: ["blog","vm"] 
---

Virtual Machine is an OS running over a base OS allowing users to run different operating systems on a single instance

Hypervisors are the VM monitors used for making virtualization possible.
It's of two types of hypervisors:
1. Type 1 Hypervisor
2. Type 2 Hypervisor

- In linux it's recommended to use QEMU KVM as it's Type 1.
- Type 1 is also called bare-metal as it runs directly on the host's hardware. eg: QEMU KVM, Microsoft Hyper-V
- Type 2 is also called hosted as it runs on top of the host OS. eg: VMware, Virutal Box, Parallels Desktop