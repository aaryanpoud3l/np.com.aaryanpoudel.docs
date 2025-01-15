---
date: 2025-01-07T20:49:53+05:45
title: "Neovim Init Setup"
description : "Docs On Installing Neovim and to set up a base config"
categories : ["Setups"]
tags : ["init","setup","blog","cli"]
---

# Neovim
Neovim is a cli based text editor written in lua. It's written in lua and is based on vim.

_Use :q! to quit or :wq to write & quit btw._

## Installation on Mac
```bash
#Using HomeBrew
brew install neovim 

#Verify the Installation
nvim -v
```
## Configuring Lazy (Package Manager)
```bash
#Setting up lazy.nvim
mkdir ~/.config/nvim && touch ~/.config/nvim/init.lua
echo 'require("config.lazy")' >> ~/.config/nvim/init.lua

mkdir ~/.config/nvim/lua/config && touch ~/.config/nvim/lua/config/lazy.lua

# Paste the following to the lazy.lua file
local lazypath = vim.fn.stdpath("data") .. "/lazy/lazy.nvim"
if not (vim.uv or vim.loop).fs_stat(lazypath) then
  local lazyrepo = "https://github.com/folke/lazy.nvim.git"
  local out = vim.fn.system({ "git", "clone", "--filter=blob:none", "--branch=stable", lazyrepo, lazypath })
  if vim.v.shell_error ~= 0 then
    vim.api.nvim_echo({
      { "Failed to clone lazy.nvim:\n", "ErrorMsg" },
      { out, "WarningMsg" },
      { "\nPress any key to exit..." },
    }, true, {})
    vim.fn.getchar()
    os.exit(1)
  end
end
vim.opt.rtp:prepend(lazypath)

vim.g.mapleader = " "
vim.g.maplocalleader = "\\"

require("lazy").setup({
  spec = {
    { import = "plugins" },
  },
  install = { colorscheme = { "gruvbox" } },
  checker = { enabled = true },
})
```

## Plugins and Customizations

```sh 
#Clone my .dotfiles
git clone git@github.com:aaryanpoudel/.dotfiles.git
mv .dotfiles ~/
ln -s ~/.dotfiles/terminal/nvim ~/.config/nvim
```