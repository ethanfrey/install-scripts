## Basic

```
sudo apt update
sudo apt install wget curl git vim
```

### XPS Tweaks

Based on https://medium.com/@pwaterz/how-to-dual-boot-windows-10-and-ubuntu-18-04-on-the-15-inch-dell-xps-9570-with-nvidia-1050ti-gpu-4b9a2901493d

Download https://raw.githubusercontent.com/JackHack96/dell-xps-9570-ubuntu-respin/master/xps-tweaks.sh

```
sudo bash xps-install/xps-tweaks.sh
sudo prime-select intel
```

### Touchpad tweaks

```
sudo apt-get install xserver-xorg-input-libinput
sudo apt-get remove --purge xserver-xorg-input-synaptics
sudo reboot
```

```
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

## Dev tools

### Github

Log into github and go to https://github.com/settings/keys

```
ssh-keygen
cat ~/.ssh/id_rsa.pub
```

Click "New SSH key" and paste the key from above

### Git

```
git config --global user.email ethanfrey@users.noreply.github.com
git config --global user.name 'Ethan Frey'
```

### Golang (1.10)

Install package and set variables:
```
sudo apt install golang
cat << 'EOF' >> ~/.bashrc

export GOPATH=${HOME}/go
export PATH=${PATH}:${GOPATH}/bin
EOF
```

Add basic tools:
```
go get github.com/golang/dep/cmd/dep
```

### Node - [nvm](https://github.com/creationix/nvm)

Install nvm:
```
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash

export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

Set up node 8 and node 10 with yarn:
```
nvm install lts/carbon
npm install -g yarn

nvm install lts/dubnium
npm install -g yarn
```

### [Docker CE](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04)

```
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
sudo apt update
# apt-cache policy docker-ce
sudo apt install docker-ce
# sudo systemctl status docker
sudo usermod -aG docker ${USER}
# su - $USER
# docker run hello-world
```


### Python (2 and 3 with virtualenv)

Python3 is installed by default, let's add 2...

```
sudo apt install python 
sudo apt install libssl-dev libffi-dev python-dev python-pip
```

And add a few extra packages to 3 as well...

```
sudo apt install python3-dev python3-pip
```

### Other useful build tools

To compile usb support (eg. node-hid)

```
sudo apt install libudev-dev libusb-1.0-0 libusb-1.0-0-dev
```


## VSCode

Go to https://code.visualstudio.com/Download and click on `.deb` download

### Add support for big workspaces

```
echo "fs.inotify.max_user_watches=524288" | sudo tee -a /etc/sysctl.conf
sudo sysctl -p
```

### Install extensions

Start VSCode:

```
code
```

`Ctrl+Shift+X` to open Extensions tab.

Search and install the following:

* Debugger for Chrome (msjsdiag.debugger-for-chrome)
* Typescript TsLint Plugin (ms-vscode.vscode-typescript-tslint-plugin)
* Go (ms-vscode.go)
* Docker (peterjausovec.vscode-docker)

### [Chrome](https://ubunlog.com/google-chrome-ubuntu-1804/)

Install Chrome:

```
sudo add-apt-repository 'deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main' 
curl -fsSL https://dl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
sudo apt update
sudo apt install google-chrome-stable
```

TODO: install and setup react/redux dev tools (and more?)


## Ofice Tools

### Zoom

Go to https://zoom.us/support/download and follow instructions.

### [Slack](https://linuxconfig.org/how-to-install-slack-on-ubuntu-18-04-bionic-beaver-linux)

```
sudo snap install slack --classic
```

### [Spotify](https://www.spotify.com/es/download/linux/)

```
sudo snap install spotify
```


## Sysadmin Tools

### Networking

```
sudo apt install whois
```


* lvm checks
* backup state
* set desktop photos
* tmux or screen or such....
