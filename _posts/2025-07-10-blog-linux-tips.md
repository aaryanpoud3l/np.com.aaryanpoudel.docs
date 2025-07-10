---
title: "Linux Tips & Nuggets"
date: 2025-07-10-T17:30:00+00:00
categories: ['Blogs']
tags: ["blog","linux"] 
---

### Command List

| Command | Description |
| - | - |
| visudo | Run CMD as sudo without PW |
| realpath | Provides Absolute Path|

--- 
### Usage:

1. visudo

```sh
sudo visudo

#At EOL, add:
userName ALL=(targetUser) NOPASSWD: /home/userName/sh/myScript.sh
```
_Parameters_
- _userName: user who will run the command_
- _targetUser: user as whom the command should run (e.g., root)_

_For security:_

```sh
sudo chown root:root /home/userName/sh/myScript.sh
sudo chmod 700 /home/userName/sh/myScript.sh
```

2. realpath

```sh
realpath ~/Documents/ # gives absolute path
```