---
layout: post
title: "Ubuntu 18.04 install on VMWare"
---

## Basic installation steps

#### Install from the mini.iso
My language is English, the timezone is Brussels/Europe, the keyboard is En/Us euro on 5

- task Basic Ubuntu Server
- task OpenSSH

#### Add GUI

I prefer a minimal GUI which I start up from the console. Problem is that the Ubuntu Desktops are either bloated (any desktop) or incomplete (Lubuntu Core has missing icons, problems with fonts, ...). What works for me is this:

```
sudo apt install --no-install-recommends xorg lxde
sudo systemctl set-default multi-user.target
#Enter the GUI with
startx
```

#### VMWare related settings

To support Cut&Paste and shared folders with the Windows host:

```
sudo apt install build-essential checkinstall open-vm-tools-desktop
```

**In VMWare Player**:
- set time synchronization with host. Maybe better alternative is install ntpd?
- enable a shared folder with windows.  You may need to add this in /etc/fstab: ```"vmhgfs-fuse /mnt/hgfs fuse defaults,allow_other 0 0"```
- sound is a problem on my system (Realtec drivers). This seems to solve it sometimes: add/change in the VMX file
```
sound.present = "TRUE"
sound.virtualdev = "hdaudio"
sound.fileName = "-1"
sound.autodetect = "TRUE"
```
#### Some other tools

For cleaning and navigating:
```
sudo apt install mc
sudo apt install bleachbit
```

#### Installing the ssh keys

I copied some keys and configurations from another vm using mc (sftp facility).
Same for git configuration and some aliases.


#### Some configuation changes

The system default PATH is set in /etc/environment. I remove the games stuff from it.
F10 in LxTerminal interferes with mc, so turn it off.
I use skin=darkfar in ~/.config/mc/ini to improve colors in console.


#### Some strange problems and some solutions

:+1: If terminal fonts in the GUI become suddenly badly spaced, a solution seems to be to install ubuntu fonts.
```
sudo apt install ttf-ubuntu-font-family
```

:+1: If console font is suddenly of bad quality and does not support graphical characters anymore, this solves it:
```shell
#to test some fonts, do like:
for i in /usr/share/consolefonts/Uni*;\  
  do setfont "$i"; ls -l /proc/; echo -e "\nINFO: currently set font: $i"; sleep 2; clear; done
#or 
setfont /usr/share/consolefonts/Uni3-Terminus20x10.psf.gz

#to set default font after reboot do like
sudo dpkg-reconfigure console-setup
#I chose a latin5 (Western Europe) and no changes to the boot font, which is good enough
```

:-1: Making a sftp connections from PcManFM does not work. There seems to be an un-met dependency to *gvfs*.  
I did not bother to find out what to do, instead I used sftp from midnight commander which is my preferred file manager anyway.


#### Cleaning up and creating a snapshot.

From console (no GUI)
- sudo bleachbit
- sudo vmware-toolbox-cmd disk wipe /
- sudo poweroff
In vmware player,


