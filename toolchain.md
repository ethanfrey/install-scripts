# Toolchains

Set up basic build toolchains for git, golang, node, docker, python (and more?)

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
