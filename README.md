# Welcome to Arch install setup 

<img width="760" height="428" alt="image" src="https://github.com/user-attachments/assets/388c2a0b-7cf2-4ccf-8dd2-9f090c7ea0f6" />


## STEP0: ESTABLISHING A WIFI CONNECTION
1. Prompt specified for wifi
```
iwctl
```
2. Find your wifi station
```
station wlan0 get-networks
```
After that type `exit` 

3. Connect to wifi
```
iwctl --passpharse "Type your wifi password" station wlan0 connect "Type your SSID"
```
4. Check if it is connected
```
ping archlinux.org (or any website) 
```
## STEP1: Arch Install
Just type:

```
archinstall
```
---

## STEP2 i3WM Dot files

This README provides an overview of the i3 configuration setup, required applications, and all updated keyboard shortcuts.

---

### 1. Overview

This i3 configuration is designed for Arch Linux with the following features:

* Custom workspace management (10 workspaces)
* Floating and tiling window management
* Integrated i3status bar with CPU usage, temperature, battery, volume, brightness, and Wi-Fi
* App launchers and media control support
* Power management shortcuts
* Terminal: kitty, Browser: //Your preferred browser
* Wallpaper management via feh

Configuration file: `~/.config/i3/config`
i3status configuration: `~/.config/i3status/config`

---

### 2. Required Applications / Packages

To make this setup work properly, ensure the following applications are installed:

#### Essentials

* **i3**: Window manager
* **i3status**: Status bar manager
* **kitty**: Terminal emulator
* **Web browser** //firefox or any 

#### Utilities

* **dmenu**: Application launcher
* **dex**: For XDG autostart support
* **xss-lock** and **i3lock**: Screen locking
* **NetworkManager** and **nm-applet**: Network management
* **brightnessctl**: Brightness control
* **playerctl**: Media control
* **lm_sensors**: CPU temperature monitoring
* **feh**: Wallpaper management
* **flameshot**: Screenshot utility
* **xorg-xinput**: Tounchpad-setup
* **blueman**: Bluetooth
* **usbutilis**: USB

Install on Arch Linux:

```bash
sudo pacman -S i3 i3status kitty brave dmenu dex xss-lock i3lock networkmanager nm-applet brightnessctl playerctl lm_sensors feh flameshot xorg-xinput blueman usbutils
```

Run sensors detect:

```bash
sudo sensors-detect
```

---

### 3. Shortcuts

All shortcuts are documented in the file `i3_shortcuts.txt`. Quick summary:

#### Modifiers

* $mod = Mod4 (Super / Windows key)
* Alt = Mod1

#### Window Management

* Open terminal: $mod + Return → kitty
* Open browser: $mod + b → //opens a browser
* Close focused window: Alt + Shift + q
* Toggle fullscreen: Alt + f
* Toggle floating: Alt + Shift + Space
* Toggle tiling/floating focus mode: Alt + Space
* Focus parent container: Alt + a
* Move focused window to scratchpad: Alt + Shift + -
* Show/hide scratchpad window: Alt + -
* Split container horizontally: Alt + h
* Split container vertically: Alt + v
* Stacked layout: Alt + s
* Tabbed layout: Alt + w
* Toggle split layout: Alt + e

#### Window Movement & Resize

* Focus left: Alt + j or Alt + Left
* Focus down: Alt + k or Alt + Down
* Focus up: Alt + l or Alt + Up
* Focus right: Alt + ; or Alt + Right
* Move window left: Alt + Shift + j or Alt + Shift + Left
* Move window down: Alt + Shift + k or Alt + Shift + Down
* Move window up: Alt + Shift + l or Alt + Shift + Up
* Move window right: Alt + Shift + ; or Alt + Shift + Right
* Enter resize mode: Alt + r
* Resize with keys: h/j/k/; or arrow keys
* Exit resize mode: Enter or Escape or Alt + r

#### Workspaces

* Switch to workspace 1-10: $mod + 1..0
* Move container to workspace 1-10: $mod + Shift + 1..0

#### Volume

* Raise volume: XF86AudioRaiseVolume
* Lower volume: XF86AudioLowerVolume
* Mute/unmute: XF86AudioMute
* Mute/unmute microphone: XF86AudioMicMute

#### Brightness

* Brightness up: XF86MonBrightnessUp
* Brightness down: XF86MonBrightnessDown

#### Screenshots

* Flameshot GUI: Print

#### Media Controls

* Play/Pause: XF86AudioPlay / XF86AudioPause
* Next track: XF86AudioNext
* Previous track: XF86AudioPrev

#### Power / Session

* Suspend: $mod + Shift + s
* Hibernate: $mod + Shift + h
* Poweroff: $mod + Shift + p
* Reboot: $mod + Shift + m
* Exit i3: $mod + Shift + e

#### App Launcher

* dmenu / app launcher: $mod + d (dmenu_run)

#### Wallpaper

* Apply wallpaper on start: exec_always --no-startup-id ~/.fehbg

# Misc

## Fix USB Not Recognized on Arch Linux

If your Android phone is detected by USB (`lsusb`) but does not appear in the file manager, the issue is missing MTP support. Install the required packages below to enable proper Android file transfer on Arch Linux.

```bash
lsusb
sudo pacman -S android-file-transfer mtpfs gvfs gvfs-mtp
```
