---
date: 2023-11-28T02:30:53+05:45
title: "Hugo Init Setup & CMD"
description : "Docs On Setting Up Hugo"
categories : ["Setups"]
tags : ["init","setup","staticsitegenerator","blog"]
---

Hugo is used for generating static sites using markdown. This blog has been created using Hugo.

Get Hugo using apt on Ubuntu based distros:

```bash
sudo apt install hugo;
```

## Commands

```bash
#Project Setup
hugo new site siteName
cd siteName
git init
#Sample hugo theme add as submodule
git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke
echo "theme = 'ananke'" >> hugo.toml

#Adding Content
hugo new content posts/postName.md

#Serve Hugo Projects
#for local
hugo server

#for production
hugo
```