---
date: 2025-01-08T18:22:48+05:45
title: "CheatSheet for Vim Key Bindings"
description : "Cheatsheet for Vim Key Bindings"
categories : ["CheatSheets"]
tags : ["cheatsheet",'cli','tldr']
---
# Vim Key Bindings CheatSheet

## Vim Modes:
- There are three modes. It's used for the following:
1. Normal Mode: Movement, deletion and searching
2. Insert Mode: Entering text directly
3. Visual: Manipulate text using selection

## Movement:
### 1. Basic navigations
```
h -> left
j -> down
k -> up
l -> right
gg -> first line of page
G -> last line of page
:number -> specified line number
```
### 2. Moving through lines
```
$ -> end of line 
0 -> start of line
b -> previous word
w -> next word
```

## Normal Mode

### 3. Editing Text
```
x -> delete character
dd -> delete line
yy -> copy line
p -> paste

u -> undo
ctrl + r -> redo

/ -> search forward
? -> search backward
:s/old/new/g ->replace all "old" with "new"
```
