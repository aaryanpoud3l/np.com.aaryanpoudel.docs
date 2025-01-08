---
date: 2025-01-06T23:25:50+05:45
title: "Jekyll Installation on Mac"
description : "Docs on Setting up Jekyll"
categories : ["Setups"]
tags : ["init","setup","blog"]
---

Jekyll is used to convert your markdown notes into a static site. This blog was created by converting my Obsidian notes written as .md and converting them to a static site using Jekyll.

## Setting up Jekyll on Mac using Homebrew:

```bash
# Install chruby (Version Manager) and ruby-install (Package Manager)
brew install chruby ruby-install

# Check the latest Ruby Version: https://jekyllrb.com/docs/installation/macos/#:~:text=Install%20the-,latest,-stable%20version%20of
ruby-install ruby 3.3.5

#To Add to the ~/.zhsrc file . Have these declared after the homebrew path declaration
echo "source $(brew --prefix)/opt/chruby/share/chruby/chruby.sh" >> ~/.zshrc
echo "source $(brew --prefix)/opt/chruby/share/chruby/auto.sh" >> ~/.zshrc
echo "chruby ruby-3.3.5" >> ~/.zshrc
# To Verify, use ruby -v to check the running version of Ruby

#Install Jekyll
gem install jekyll bundler
```
## Commands

```bash
#Project Setup
jekyll new siteName
cd siteName
git init

#Serve Project Locally On: http://localhost:4000
bundle exec jekyll serve --livereload

#For Ddding Content
cd _posts/
touch blogName.md

#For Config Issues
jekyll doctor

#To Build the Project for Production
jekyll build
```
