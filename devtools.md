# Dev Tools

Set up useful visual development tools...
currently focused on web development, and more as needed

## Github

Log into github and go to https://github.com/settings/keys

```
ssh-keygen
cat ~/.ssh/id_rsa.pub
```

Click "New SSH key" and paste the key from above

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

### Customize Keybindings

**TODO**

## [Chrome](https://ubunlog.com/google-chrome-ubuntu-1804/)

Install Chrome:

```
sudo add-apt-repository 'deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main' 
curl -fsSL https://dl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
sudo apt update
sudo apt install google-chrome-stable
```

### Configure multiple accounts

At least one with work passwords, one for personal use, and one for react dev tools 
(dev tools can read/write all webpages, so no important passwords on this persona)

### Add extensions

Activate the "react dev" persona

**TODO**: install and setup react/redux dev tools (and more?)

## Keybase

**TODO**

## Virtualbox

**TODO** set up some environments, including windows edge test box, linux server??
