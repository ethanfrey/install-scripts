# Dev Tools

Set up useful visual development tools...
currently focused on web development, and more as needed

## Github

Log into github and go to https://github.com/settings/keys

```shell
ssh-keygen
cat ~/.ssh/id_rsa.pub
```

Click "New SSH key" and paste the key from above

## VSCode

Go to https://code.visualstudio.com/Download and click on `.deb` download

### Add support for big workspaces

```shell
echo "fs.inotify.max_user_watches=524288" | sudo tee -a /etc/sysctl.conf
sudo sysctl -p
```

### Install extensions

Start VSCode:

```shell
code
```

`Ctrl+Shift+X` to open Extensions tab.

Search and install the following:

* Debugger for Chrome (msjsdiag.debugger-for-chrome)
* Typescript TsLint Plugin (ms-vscode.vscode-typescript-tslint-plugin)
* Go (ms-vscode.go)
* Docker (peterjausovec.vscode-docker)
* Open in Github (fabiospampinato.vscode-open-in-github)
* Better TOML (bungcip.better-toml)
* Editor Config (editorconfig.editorconfig)

### [Customize Keybindings](https://code.visualstudio.com/docs/getstarted/keybindings)

* Type `Ctrl+k Ctrl+S` to open keyboard shortcuts.
* Click on `keybindings.json`
* Copy in the following set (some basic customizations):

```json
[
    // ctrl+a goes to line beginning
    { "key": "ctrl+a",                  "command": "cursorHome",
        "when": "textInputFocus" },
    { "key": "ctrl+shift+a",            "command": "cursorHomeSelect",
        "when": "textInputFocus" },

    // and redefine alt+a for select all
    { "key": "alt+a",                "command": "editor.action.selectAll",
        "when": "textInputFocus" },
    { "key": "alt+a",                "command": "editor.action.webvieweditor.selectAll",
        "when": "!editorFocus && !inputFocus && activeEditor == 'WebviewEditor'" },
    { "key": "alt+a",                "command": "editor.action.webvieweditor.selectAll",
        "when": "!editorFocus && !inputFocus && activeEditor == 'workbench.editor.htmlPreviewPart'" },
    { "key": "alt+a",                "command": "list.selectAll",
        "when": "listFocus && listSupportsMultiselect && !inputFocus" },

    // ctrl+e is end of line (currently same as ctrl+p)
    { "key": "ctrl+e",                   "command": "cursorEnd",
        "when": "textInputFocus" },
    { "key": "ctrl+shift+e",             "command": "cursorEndSelect",
        "when": "textInputFocus" }
]
```

### Some custom settings...

Open User Settings (JSON), with `Ctrl+Shift+P` : `Settings (JSON)`.
And add the following lines:

```json
{
    "go.vetFlags": ["-composites=false"]
}
```


## [Chrome](https://ubunlog.com/google-chrome-ubuntu-1804/)

Install Chrome:

```shell
sudo add-apt-repository 'deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main' 
curl -fsSL https://dl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
sudo apt update
sudo apt install google-chrome-stable
```

### Configure multiple accounts

At least one with work passwords, one for personal use, and one for react dev tools 
(dev tools can read/write all webpages, so no important passwords on this persona)

### Add extensions

Activate the "react dev" persona, and install the following:

* [Redux Dev Tools](https://chrome.google.com/webstore/detail/redux-devtools/lmhkpmbekcpmknklioeibfkpmmfibljd)
* [React Dev Tools](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi)
* [JSON View](https://chrome.google.com/webstore/detail/jsonview/chklaanhfefbnpoihckbnefhakgolnmc)

## Terminal

### [Fonts](http://www.webupd8.org/2010/07/7-of-best-ubuntu-terminal-fixed-width.html)

```shell
sudo apt-get install fonts-inconsolata fonts-liberation
```

### [Terminator](https://www.atareao.es/software/utilidades/terminator-un-meta-terminal-ubuntu/) - terminal emulator

```shell
# Cannot use this as insecure
# sudo add-apt-repository ppa:gnome-terminator
sudo apt-get update
sudo apt-get install terminator
```

### [Configure](https://www.linuxnov.com/the-complete-guide-to-configure-terminator-terminal-emulator-layouts/):

Which one terminator or default ubuntu terminal???

**TODO**

* Set Fonts
* Set Colors
* Screen layouts....
* Shortcuts

### [Tmux](https://hackernoon.com/a-gentle-introduction-to-tmux-8d784c404340)

Install:

```shell
sudo apt-get install tmux
tmux -V
```

**TODO** setup

## Keybase

**TODO**

## Virtualbox

**TODO** set up some environments, including windows edge test box, linux server??
