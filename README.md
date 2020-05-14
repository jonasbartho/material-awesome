## Material and Mouse driven theme for [AwesomeWM 4.3](https://awesomewm.org/)
### Original work by PapyElGringo, but fork comes from ChrisTitusTech (https://github.com/ChrisTitusTech/material-awesome)

Note: This fork is adjusted for fedora.

An almost desktop environment made with [AwesomeWM](https://awesomewm.org/) following the [Material Design guidelines](https://material.io) with a performant opiniated mouse/keyboard workflow to increase daily productivity and comfort.

[![](./theme/PapyElGringo-theme/demo.gif?raw=true)](https://www.reddit.com/r/unixporn/comments/anp51q/awesome_material_awesome_workflow/)
*[Click to view in high quality](https://www.reddit.com/r/unixporn/comments/anp51q/awesome_material_awesome_workflow/)*

| Tiled         | Panel         | Exit screen   |
|:-------------:|:-------------:|:-------------:|
|![](https://i.imgur.com/fELCtep.png)|![](https://i.imgur.com/7IthpQS.png)|![](https://i.imgur.com/rcKOLYQ.png)|



## Installation
### Note: the best transition is from gnome to material-awesome as KDE-plasma can break some indicators until plasma is purged entierly.

### 1) Get all the dependencies
- [AwesomeWM](https://awesomewm.org/) as the window manager - sudo dnf install awesome
- [Roboto](https://fonts.google.com/specimen/Roboto) as the **font** - sudo dnf install google-roboto-fonts.noarch
- [Rofi](https://github.com/DaveDavenport/rofi) for the app launcher - sudo dnf install rofi
- [Compton](https://github.com/tryone144/compton) for the compositor (blur and animations) - sudo dnf install compton
- [i3lock](https://github.com/meskarune/i3lock-fancy) the lockscreen application - needs to be compiled (no rpm package available)
- [xclip](https://github.com/astrand/xclip) for copying screenshots to clipboard - sudo dnf install xclip
- __gnome-keyring__ and a __policykit-agent__ (by default policykit-1-gnome is enabled)
- (Optional) "sudo dnf install qt5-qtstyleplugins" for making QT and KDE applications look the same as gnome applications
- (Optional) [Materia](https://github.com/nana-4/materia-theme) as GTK theme - sudo dnf install materia-gtk-theme
- (Optional) [Papirus Dark](https://github.com/PapirusDevelopmentTeam/papirus-icon-theme) as icon theme - sudo dnf install papirus-icon-theme
- (Optional) [lxappearance](https://sourceforge.net/projects/lxde/files/LXAppearance/) to set up the gtk and icon theme - sudo dnf install lxappearance
- (Optional) [light] for adjusting brightness on laptops - sudo dnf install light
- (Optional) [spectacle] my personal screenshot utility of choice, can be replaced by whichever you want, just remember to edit the screenshot utility script - sudo dnf install spectacle

### 2) Clone the configuration

```
git clone https://github.com/jonasbartho/material-awesome ~/.config/awesome
```

### 3) Set the themes
Start **lxappearance** to active the **icon** theme and **GTK** theme
Note: for cursor theme, edit `~/.icons/default/index.theme` and `~/.config/gtk3-0/settings.ini`, for the change to also show up in applications run as root, copy the 2 files over to their respective place in `/root`.

### 4) Same theme for Qt/KDE applications and GTK applications, and fix missing indicators
First install `qt5-qtstyleplugins` and add this to the bottom of your `/etc/environment`

```bash
XDG_CURRENT_DESKTOP=Unity
QT_QPA_PLATFORMTHEME=gtk2
```

The first variable fixes most indicators (especially electron based ones!), the second tells Qt and KDE applications to use your gtk2 theme set through lxappearance.

### 5) Important bindings

I have binded my own F-keys to change the volume and brightness. This can be adjusted to whatever you want:
[~/.config/awesome/configuration/keys/global.lua](./configurations/keys/global.lua)
```
Lower volume: Superkey+F8
Higher volume: Superkey+F9
Toggle mute: Superkey+F10
```
```
Lower brightness: Superkey+F5
Higher brightness: Superkey+F6
```
Handy:
```
Log out: Ctrl+Superkey+q
Show exit screen(shutdown/reboot/sleep/logout/lock): Alt+Space
```

cheat sheet for multiple bindings: Superkey+F1

### 6) Read the documentation
The documentation live within the source code.

The project is split in functional directories and in each of them there is a readme where you can get additionnal informations about the them.

Files that you will probably edit the most: ~/.config/awesome/configuration/apps.lua and ~/.config/awesome/configuration/keys/global.lua

* [Configuration](./configuration) is about all the **settings** available
* [Layout](./layout) hold the **disposition** of all the widgets
* [Module](./module) contain all the **features** available
* [Theme](./theme) hold all the **aestetic** aspects
* [Widget](./widget) contain all the **widgets** available
