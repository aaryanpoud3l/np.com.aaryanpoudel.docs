---
title: "Symbolic Link / Symlink"
date: 2025-01-09T17:52:24+05:45
categories: ['TLDR']
tags: ["tldr,blog"]
---

# Symlink:

Symlink is a type of file that's used to point to another file/directory. It contains a text string that's automatically interpreted and followed by the OS as a path to another file/directory. The source file/dir is called a target.

```bash
#create
ln -s ~/path/to/target ~/symlinkFile

#delete
rm -rf ~/symlinkFile
```
