---
date: 2025-01-09T17:36:48+05:45
title: "Dotfiles & Config Setup using Git"
description : "Setup for Dotfiles and Configs"
categories : ["Setups"]
tags : ["init",'setup','cli']
---

# Dotfiles
Dotfiles are files that's used by applications or packages for storing it's configurations. It's called a dot file as it's naming starts with a dot > `.`

Common dotfiles include `.zshrc .bashrc .gitignore` and are mostly stored in your home under `.config` directory.

In this guide, I'll list out the steps that I found to be the most way of storing, backing up the `.dotfiles` . The easiest and most efficient way of storing dot files are by using [symlinks](./2025-01-09-tldr-symlink.md "tldr: Symlink"). It avoids duplication and allows you to use [git](./2025-01-09-cheatSheet-git.md) to track and version changes, acting as a backup in case some configs go haywire with a single command.

## Managing .dotfiles using symlinks
*eg: managing the `.zshrc`*
```sh
mkdir ~/.dotfiles/zsh/
mv ~/.zshrc ~/.dotfiles/zsh/
ln -s ~/.dotfiles/zsh ~/.zshrc
cd ~/.dotfiles ; git init
```