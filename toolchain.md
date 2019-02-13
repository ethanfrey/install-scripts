# Toolchains

Set up basic build toolchains for git, golang, node, docker, python (and more?)

## Git

Set up for commits:

```shell
git config --global core.editor "vim"
git config --global user.email ethanfrey@users.noreply.github.com
git config --global user.name 'Ethan Frey'
```

Add some helpers (to ~/.bashrc)

```shell
alias glog='git log --oneline --graph'
```

## Golang (1.10)

Install package and set variables:

```shell
sudo apt install golang
cat << 'EOF' >> ~/.bashrc

export GOPATH=${HOME}/go
export PATH=${PATH}:${GOPATH}/bin
EOF
```

Add basic tools:

```shell
go get github.com/golang/dep/cmd/dep
go get github.com/derekparker/delve/cmd/dlv

go get github.com/mdempsky/gocode
go get github.com/uudashr/gopkgs/cmd/gopkgs
go get golang.org/x/tools/cmd/goimports
go get github.com/sqs/goreturns
go get github.com/rogpeppe/godef
go get github.com/ramya-rao-a/go-outline
```

## Node - [nvm](https://github.com/creationix/nvm)

Install nvm:

```shell
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash

export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

Set up node 8 and node 10 with yarn:

```shell
nvm install lts/carbon
npm install -g yarn

nvm install lts/dubnium
npm install -g yarn
```

## [Docker CE](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04)

```shell
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


## Python (2 and 3 with virtualenv)

Python3 is installed by default, let's add 2...

```shell
sudo apt install python 
sudo apt install libssl-dev libffi-dev python-dev python-pip
sudo apt install python3-dev python3-pip
```

And setup [virtualenv](https://virtualenv.pypa.io/en/latest/installation/)
and [virtualenv-wrapper](https://virtualenvwrapper.readthedocs.io/en/latest/)

```shell
pip install virtualenv
# do we really need this?
pip3 install virtualenv
# we only need this once, as it is shell-scripts, version independent
pip install virtualenvwrapper

cat << 'EOF' >> ~/.bashrc
export PYTHONBIN=${HOME}/.local/bin
export PATH=${PATH}:${PYTHONBIN}
export WORKON_HOME=${HOME}/.virtualenvs
# export PROJECT_HOME=${HOME}/Devel
source ${PYTHONBIN}/virtualenvwrapper.sh
EOF
```

Demo virtualenvs:

```shell
mkvirtualenv py2
mkvirtualenv --python python3 py3

workon py2
python --version

workon py3
python --version
```

## Rust (with wasm)

Read [rustup docs](https://github.com/rust-lang/rustup.rs/blob/master/README.md) to make sense of the toolchain.

```shell
rustup show
rustup help
```

Taken from [substrate docs](https://github.com/paritytech/substrate#6-building):

```shell
curl https://sh.rustup.rs -sSf | sh
rustup update nightly
rustup target add wasm32-unknown-unknown --toolchain nightly
rustup update stable
cargo install --git https://github.com/alexcrichton/wasm-gc
```

## Kubernetes

Basic client side tooling and setup (`kubectl`):

### [Install kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/):

with snap:

```shell
sudo snap install kubectl --classic
```

or with apt: (note this is onlu 1.13 until they add a bionic repo)

```shell
sudo apt install -y apt-transport-https
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
sudo apt update
sudo apt install -y kubectl
```

And ensure you have the proper version

```shell
kubectl version
```

### Add credentials and configure (for GCE)

Add google compute sdk, with snap:

```shell
sudo snap install google-cloud-sdk
```

Or [apt](https://cloud.google.com/sdk/docs/downloads-apt-get):

```shell
CLOUD_SDK_REPO="cloud-sdk-$(lsb_release -c -s)"
curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
echo "deb http://packages.cloud.google.com/apt $CLOUD_SDK_REPO main" | sudo tee -a /etc/apt/sources.list.d/google-cloud-sdk.list
sudo apt update
sudo apt install -y google-cloud-sdk
```

Add credentials, for example "hugnet" project, listed as `iov-hugnet2` on GCE:

```shell
gcloud auth login
gcloud container clusters get-credentials hugnet --zone europe-west1-b --project=iov-hugnet2
kubectl config get-contexts
kubectl config use-context gke_iov-hugnet2_europe-west1-b_hugnet

gcloud projects list
gcloud config set project iov-hugnet2
```

View you can see the config:

```shell
kubectl cluster-info
```

Example - copy data:

```shell
mkdir bns-a-0
kubectl cp bns-a-0:/data/tendermint/data/state.db bns-a-0
kubectl cp bns-b-0:/data/tendermint/data/state.db bns-b-0
kubectl cp bns-c-0:/data/tendermint/data/state.db bns-c-0
kubectl cp bns-d-0:/data/tendermint/data/state.db bns-d-0
```

And check out [more useful commands](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)

*TODO* local cluster/deploy environment???
Some [instructions here](https://linuxconfig.org/how-to-install-kubernetes-on-ubuntu-18-04-bionic-beaver-linux)

## Bash tooling

Some tools to help with bash scripting

```shell
sudo apt install shellcheck
```

## Other useful build tools

To compile usb support (eg. node-hid):

```shell
sudo apt install libudev-dev libusb-1.0-0 libusb-1.0-0-dev
```

Clang and c compilation:

```shell
sudo apt install cmake pkg-config libssl-dev clang libclang-dev
```
