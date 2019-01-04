# Basic Setup

First, update and install some useful command line tools, needed to set everything else up

```shell
sudo apt update
sudo apt upgrade
sudo apt install wget curl jq git vim
```

## XPS Tweaks

Based on https://medium.com/@pwaterz/how-to-dual-boot-windows-10-and-ubuntu-18-04-on-the-15-inch-dell-xps-9570-with-nvidia-1050ti-gpu-4b9a2901493d

Download https://raw.githubusercontent.com/JackHack96/dell-xps-9570-ubuntu-respin/master/xps-tweaks.sh

```shell
sudo bash xps-install/xps-tweaks.sh
sudo prime-select intel
```

## Touchpad tweaks

```shell
sudo apt-get install xserver-xorg-input-libinput
sudo apt-get remove --purge xserver-xorg-input-synaptics
sudo reboot
```

```shell
sudo apt install xdotool wmctrl libinput-tools
sudo gpasswd -a $USER input
mkdir ~/utils
cd ~/utils
git clone https://github.com/bulletmark/libinput-gestures.git
cd libinput-gestures
sudo make install
libinput-gestures-setup autostart
libinput-gestures-setup start
```

**TODO** Configure screen resolution better, power saving???