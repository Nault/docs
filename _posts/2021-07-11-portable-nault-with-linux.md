# How to use Nault on a bootable Linux flash drive

Using a wallet on an online machine comes with a risk. The OS can contain malicious software such as keylogger, screen recorder or code that looks for and replaces crypto addresses without your consent. In that case, it doesn't matter if you use Nault on the web or as a desktop app. One way to protect against this is to use a Ledger device, another is to only sign transactions via an offline Nault on another machine.

This guide is about a third option:

**Make Nault portable by booting up a clean Linux distro and install the Nault desktop app within it**

This will reduce the risk of getting viruses if you never use the OS for anything other than Nault and never install any other software. It's nice to have Nault in your pocket when travelling, visiting friends, school or workplace.

![](/images/slax_desktop.png)

============================
## Table of Contents

1. TOC
{:toc}

============================
## Introduction

We will use a Linux distro called [Slax](https://www.slax.org/) which is a modern graphical light-weight OS that runs directly from a USB flash drive.

**Benefits with Slax:**

1. [Truly portable](https://www.slax.org/starting.php): No installation needed
2. [Nice spec](https://www.slax.org/introduction.php): Only 128MB of RAM needed (512 if running it in ram), 32 or 64 bit (x86_64 CPU)
3. [Pre-installed apps](https://www.slax.org/using.php) such as a web browser, file manager and terminal
4. Based on Debian: Can install thousands of precompiled apps via the APT command just like in Ubuntu
5. Super light-weight: Under 300MB total disk (Plus Nault 100MB). Fast boot.
6. Persistent changes or optionally choose to do a fresh start every time
7. Customizable: Changes can be exported as a module or as a whole new ISO to be loaded on the next boot
8. Can be loaded into RAM only
9. Free

============================
## Preparing the USB flash drive with Slax

**A.** Download the Slax ISO. Currently has to be done with a little compromise since Nault requires Ubuntu20 or Debian10 and the latest Slax uses Debian9. A new version will hopefully come and this guide will update accordingly.

* **Option 1:** [Download official Slax 9](https://www.slax.org/#purchase) (32 or 64 bit). At this time limited to [Nault 1.10.2 desktop app](https://github.com/Nault/Nault/releases/tag/v1.10.2) or [nault.cc](https://nault.cc) web app. Could also compile Nault from source code, see the advance section below.

![](/images/slax_download-iso-a.png)

* **Option 2:** [Dowload unofficial Slax 10](http://lucbie.altervista.org/slax.php) (32 or 64 bit). It can run the latest Nault desktop app or [nault.cc](https://nault.cc) web app. More info about the unofficial build can be found [here](https://groups.google.com/g/slax-users/c/l8M2-zLG5GE) and [here](https://www.slax.org/blog/25684-Testing-Slax-10.2-beta1.html#comments).

![](/images/slax_download-iso-b.png)

{% include alert.html text="Please be aware that running unofficial versions of Linux distros comes with its own risk. Even the official Slax. We do not endorse Slax or make promises about security." %}


**B.** Copy the slax folder from the ISO to a USB flash drive with at least 1GB in order to have some extra space. Or burn the ISO on a DVD but then you can't have persistent storage. More info [here](https://www.slax.org/starting.php)

![](/images/slax_extract-iso.png)

**C.** Make the USB bootable by running bootinst.bat (if Windows) or bootinst.sh (if Linux) from slax/boot. The USB should now look like this:

![](/images/slax_usb.png)


============================
## Install Nault inside Slax

**A.** Launch Slax by restarting the computer with the USB flash drive. If it's not automatically booting, most computers allow you to press F8 to override the boot drive. During boot you can press ESC for more options, for example, erase any changed data or load into RAM.

**B.** When Slax has been launched you may want to change keyboard layout if not English. Right-click on the desktop and select keyboard layout of your choice. Possibly also change the screen resolution. If you rely in WiFi you need to launch the "Net Manager" and connect.

**C.** Start the built-in browser from the bottom left start button. Go to [Nault Github releases](https://github.com/Nault/Nault/releases) and download the latest appImage for Linux.

**If using Slax 9 (Debian 9) you are limited to [Nault 1.10.2 desktop app](https://github.com/Nault/Nault/releases/tag/v1.10.2) or you have to compile Nault from source code.**

![](/images/slax_download.png)

**D.** Open a terminal (xterm). Also from the start button.

**E.** Create a script to launch Nault more easily since it can't run under "root" without a special flag.

{% include info.html text="To paste clipboard (ctrl+c) into xterm you can use the middle mouse button." %}

Make sure to type the correct Nault version below. Chmod is to make the script executable.

    cd Downloads
    chmod +x Nault-1.13.3-Linux.AppImage
    echo '#!/bin/bash' >> start.sh
    echo '/root/Downloads/Nault-1.13.3-Linux.AppImage --no-sandbox' >> start.sh
    chmod +x start.sh

![](/images/slax_nault-install.png)

**If using Slax 9 (Debian 9) you also need these before you can launch the AppImage:**

    apt update
    apt install libatk-bridge2.0-0 libgtk-3-0 -y

Now you can run ./start.sh from a terminal or double click it in the file manager. It should open up Nault and you are ready to go! The changes you made will be available during the next boot (because it's being saved to the USB/slax/changes/changes.dat, including the wallet if not setting up Nault to erase cache on exit. It's recommended to disable the auto-login, please see the next section.

![](/images/slax_files.png)

![](/images/slax_execute.png)

![](/images/slax_installed.png)

{% include alert.html text="Do not unplug the flash drive or cut the power to the computer while Slax is running. This will invalidate changes made. If you want persistent data you must shut down properly from the OS (bottom right) and wait to unplug the drive until the machine has turned off." %}

============================

## Advanced: Protect your persistent data

Slax logs in automatically and if someone finds your flash drive they can see your data, for example the wallet balance if you have that saved. It's recommended to change the root password and disable auto-login.

From a terminal run (one line at a time):

    passwd
    systemctl disable xorg

The next time you boot, use "root" as username and your new password. To start the GUI, run:

    startx

If there is a better method to achieve this, please let us know!

## Advanced: How to compile Nault from source code inside Slax

You may want to compile Nault, for example, if you have made your own changes to the code or do not trust the official build. Tested with Slax 9.11.

**This procedure will require at least 1.5GB extra space on the USB**

**A.** Install dependencies not included with Slax

From a terminal run (one line at a time):

    apt install curl -y
    curl -sL https://deb.nodesource.com/setup_12.x | bash -
    apt install nodejs -y
    apt install git libudev-dev libusb-1.0-0-dev make build-essential pkg-config -y

**If using Slax 9 (Debian 9) you will also need to change the source list and install gcc and g++:**

    nano /etc/apt/sources.list

..and add these lines at the bottom:

    deb http://ftp.us.debian.org/debian/ jessie main contrib non-free
    deb-src http://ftp.us.debian.org/debian/ jessie main contrib non-free

When finished, exit the nano editor by ctrl+x and run these commands. gcc and g++ is for compiling Nault and the other for running the AppImage:

    apt update
    apt install gcc-4.8 g++-4.8 libatk-bridge2.0-0 libgtk-3-0 -y

**B.** Compile Nault

From a terminal run (one line at a time):

    git clone https://github.com/Nault/Nault
    cd Nault
    npm install -g @angular/cli
    npm install
    npm run desktop:build-local

The binary is located in desktop-app\build. Run it with

    ./Nault/x.xx.AppImage --no-sandbox

============================
## Advanced: Store Nault as a Slax module

This will allow you to erase user data and start fresh every launch with Nault still installed. Useful if you never want to connect to the internet and just use Nault in offline mode.

Read more [here](https://www.slax.org/customize.php).

**A.** Boot Slax with a fresh install or hit ESC during the boot screen and select "Fresh start"

**B.** Install Nault according to above

**C.** When you have verified it works, run the command

    savechanges nault.sb

**D.** Optional: Create a fresh ISO which you can load on another flash drive or DVD:

    genslaxiso nault-slax.iso nault.sb

**E.** Allow the flash drive to load the module on boot (even if running in RAM or starting fresh). Note: This command will not work if you already running slax via RAM. In that case you will need to copy the module manually to the USB folder /slax/modules/ from another OS:

    mv nault.sb /run/initramfs/memory/data/slax/modules/

{% include alert.html text="If you protected Slax by changing the root password or disabled the GUI, that will not be stored in the module. Slax would auto-login if loaded only with this module." %}

{% include info.html text="If you want to make sure you only store what you want in the module you can inspect it by converting to a directory with sb2dir, modify and revert with dir2sb. Or create the directory structure first and create the module that way." %}

============================

**Good luck with your Linux distro!**
