---
date : 2023-11-14T12:30:31+05:45
title : "QEMU Virtual Machine Setup"
description : "Docs On Setting Up the QEMU KVM Virtual Machine Manager"
categories: ["Setups"]
tags : ["setup","init"]
---

QEMU is a Level 0 HyperVisor and allows for the best VM performance in linux.

## Installation:

```bash
sudo apt update -y; sudo apt upgrade -y; sudo apt autoremove -y; sudo apt autopurge;
sudo apt install virt-manager qemu-kvm -y;
```
