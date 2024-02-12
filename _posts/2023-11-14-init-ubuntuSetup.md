---
date : 2023-11-14T11:48:48+05:45
title: "Ubuntu Initial Setup"
description : "Docs On Setting Up Minimal Ubuntu After Install"
categories: ["Setups"]
tags : ["ubuntu","linux","init","setup","blog"]
---

The scripts have been verified on _Ubuntu 22.04 LTS_ :

```bash
#Essentials
sudo apt remove firefox geary gnome-weather gnome-contacts gnome-system-monitor gnome-user-docs gnome-logs;
sudo snap remove firefox;
sudo apt update -y && sudo apt upgrade -y;
sudo apt install ubuntu-restricted-extras gufw htop curl wget git;

#Nvida Graphic Driver
apt list | grep nvidia; #View if Installed
sudo apt install nvidia-driver-535;

#Must Have Pkgs
sudo apt install qbittorrent vlc cheese;
sudo apt install inkscape libreoffice; #Productivity Suite

#Tweaks
sudo apt install chrome-gnome-shell gnome-shell-extensions gnome-tweaks;
gsettings set org.gnome.shell.window-switcher current-workspace-only false;
gsettings set org.gnome.shell.extensions.dash-to-dock click-action 'minimize';
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop;

#Swappiness
cat /proc/sys/vm/swappiness;
sudo bash -c "echo 'vm.swappiness = 10' >> /etc/sysctl.conf";
sudo sysctl -p;
cat /proc/sys/vm/swappiness;
```
For Lenovo laptops, save your battery health using conservation mode : 

```bash
cat /sys/bus/platform/drivers/ideapad_acpi/VPC2004:00/conservation_mode;
echo 1 | sudo tee /sys/bus/platform/drivers/ideapad_acpi/VPC2004:00/conservation_mode;
```