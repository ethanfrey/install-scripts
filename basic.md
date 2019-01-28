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

## Wifi Firmware Upgrade

[Instructions to upgrade the driver](https://www.dell.com/support/article/es/es/esbsdt1/sln306440/killer-n1535-wireless-firmware-manual-update-guide-for-ubuntu-systems?lang=en)

```shell
# check this is the proper driver to upgrade (shows rev 32)
sudo lspci | grep –i qca6174

# download and install new firmware
cd ~/utils
mkdir linux-firmware
cd linux-firmware
wget http://mirrors.edge.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.176_all.deb
sudo dpkg -i *.deb
sudo modprobe -r ath10k_pci && sudo modprobe ath10k_pci
```
(You can check for the latest package in http://mirrors.edge.kernel.org/ubuntu/pool/main/l/linux-firmware/ and update the version in wget)

Then reboot and see....

**TODO** Configure screen resolution better, power saving???