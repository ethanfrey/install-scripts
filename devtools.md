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
* Open in Github (fabiospampinato.vscode-open-in-github)
* Better TOML (bungcip.better-toml)

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

Activate the "react dev" persona, and install the following:

* [Redux Dev Tools](https://chrome.google.com/webstore/detail/redux-devtools/lmhkpmbekcpmknklioeibfkpmmfibljd)
* [React Dev Tools](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi)
* [JSON View](https://chrome.google.com/webstore/detail/jsonview/chklaanhfefbnpoihckbnefhakgolnmc)

## Keybase

**TODO**

## Virtualbox

**TODO** set up some environments, including windows edge test box, linux server??
