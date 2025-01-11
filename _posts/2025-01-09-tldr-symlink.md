---
title: "Symbolic Link / Symlink"
date: 2025-01-09T17:52:24+05:45
categories: ['TLDR']
tags: ["tldr,blog"]
---

# Symlink:

Symlink is a type of file that's used to point to another file/directory. It contains a text string that's automatically interpreted and followed by the OS as a path to another file/directory.
- The source file/dir is called a target. 
- Example use case: if you want your game's save file to be stored in /hardDisk/saveFile then create a symlink from /saveFolder/saveFile to the new location.
- Symlinks are of two types:
	1. Soft Links: Points to the original file > Original File points to the inode
	2. Hard Links: Points to the inode itself	

1. Soft Links:

```bash
#create
ln -s ~/path/to/original ~/symlinkFile
ln -s '/path/to/original with spaces' '/path/to/link with spaces'

#delete
rm -rf ~/symlinkFile
```

2. Hard Links:

```bash
ln ~/path/to/original ~/symlinkFile
```
