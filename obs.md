# Open Broadcasting Software

For capture and live streaming....

## Install

Info from [offical site](https://github.com/obsproject/obs-studio/wiki/Install-Instructions#linux)

Also set up [Audacity](https://www.audacityteam.org/) as a audio toolkit.

```shell
sudo apt install audacity
```

### Prep

Ensure that you have OpenGL 3.2 or newer
(Question: I see three different versions there.. which one matters????)

```shell
sudo apt install mesa-utils
glxinfo | grep "OpenGL"
```

### Packages

```shell
sudo apt-get install ffmpeg
sudo snap install vlc

sudo add-apt-repository ppa:obsproject/obs-studio
sudo apt-get update
sudo apt-get install obs-studio
```

## Setup

1. Run it with `obs` from the shell, and then click on "Add to favorites" in the side bar for visual launch ability.
2. Go through "Auto-configuration wizard"
3. Check out some settings from https://www.youtube.com/watch?v=XllRHuCe07A

```shell
mkdir -p ~/obs/recordings
```

Settings:
* Set output > recording path to `~/obs/recordings`
* Set output > recording format to mp4

