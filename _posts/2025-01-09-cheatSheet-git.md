---
title: "Git & GitHub SSH Setup"
date: 2025-01-09T18:07:24+05:45
categories: ['Cheatsheets']
tags: ["tldr,blog,cheatsheet,cli"]
---

# Git
Git is an opensource version control system used to track changes in files. It's a powerful tool allowing multiple developers to work efficiently on a single code-base.

### Cheatsheet
```shell
git init
git add .
git pull
git push
git clone https://git@repositoryUrl
git commit -m "my first commit"

git branch branchName
git checkout branchName
```
### GitHub SSH Setup
It's a dev platform utilizing git for distributed version control. The best way to use github is by setting it up via ssh.
```bash
#If no password is needed, press enter on prompts
ls -al ~/.ssh
ssh-keygen -t ed25519 -C "your_email@example.com"
eval "$(ssh-agent -s)"

#Paste the following in config
#touch ~/.ssh/config
#Host github.com
#  AddKeysToAgent yes
#  UseKeychain yes
#  IdentityFile ~/.ssh/id_ed25519
#ssh-add --apple-use-keychain ~/.ssh/id_ed25519

pbcopy < ~/.ssh/id_ed25519.pub
```
Open Github > Settings > SSH and GPG Keys > New SSH Key and paste the public key. To verif the ssh connection use the following cmd `ssh -T git@github.com`
