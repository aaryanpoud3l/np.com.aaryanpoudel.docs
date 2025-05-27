---
title: "Cheatsheet for Tmux"
date: 2025-05-27T20:26:00+01:00
description : "Cheatsheet for Tmux"
categories : ["CheatSheets"]
tags : ["blog","cheatsheet",'tldr']
---

### Basic Commands
```sh
#basic
tmux
tmux ls

#sessions
tmux new -s sessionName
tmux a # #attach
tmux a -t sessionName
tmux kill-session -t sessionName
```
