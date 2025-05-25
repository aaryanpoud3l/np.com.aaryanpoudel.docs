---
title: "Cheatsheet for Linux"
date: 2025-05-24T17:28:00+01:00
description : "Cheatsheet for Linux"
categories : ["CheatSheets"]
tags : ["blog","cheatsheet",'tldr']
---

### Ownership
```sh
sudo chown $USER:$USER fileName

sudo chown $USER:$USER folderName
sudo chown -R $USER:$USER folderName //Modifies the files inside
```

### File Permission
There are three permissions:
Read: `4` Write `2` Execute `1` or `rwx`
```sh
chmod 777 fileName
chmod +rwx fileName
chmod -rwx fileName

chmod 755 folderName
chmod -R 755 folderName  // Modifies the files inside
```

Defaults:
1. General Folder: 775
2. General File: 664
3. Deployment Folder: 755
4. Deployment File: 644

### Tips:

Executing scripts without entering password
```sh
sudo visudo #or sudo nano /etc/sudoers
userName ALL=(ALL) NOPASSWD: /pathToScript # add to the eof
```