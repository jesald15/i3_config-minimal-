# Arch-Minimal-Install

A **minimal Arch Linux installation** using **archinstall** and **i3 Window Manager**, designed for **low-end, aging, or nearly-dead laptops**. This setup prioritizes performance, simplicity, and a clean workflow with sane defaults.

---
<img width="939" height="534" alt="image" src="https://github.com/user-attachments/assets/0c38a7ec-f6da-41ac-9ed9-50c4723ac69f" />

## Screenshots

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/030b5b14-0679-41f3-b9df-ebe2104dc0fc" />
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/fa541471-dc04-426a-98ef-3ffb696c2947" />

---

## STEP 0: Establish a Wi‑Fi Connection (Live ISO)

If you are installing Arch on a wireless network, connect first using `iwctl`.

```bash
iwctl
```

List available Wi‑Fi networks:

```bash
station wlan0 get-networks
```

Connect to your Wi‑Fi:

```bash
iwctl --passphrase "YOUR_WIFI_PASSWORD" station wlan0 connect "YOUR_SSID"
```

Exit `iwctl`:

```bash
exit
```

Verify internet connectivity:

```bash
ping archlinux.org
```

---

## STEP 1: Install Arch Linux

Once internet is working, start the guided installer just type:

```bash
archinstall
```

> Recommended choices:
>
> * Minimal profile
> * PipeWire audio
> * NetworkManager
> * EFI system (if supported)
> * User account creation

---

##  STEP 2: i3 Window Manager Setup

### First Login Important Step ⚠️

##  Required Applications / Packages

### Essentials

* i3 – Window manager
* i3status – Status bar
* kitty – Terminal emulator
* Web browser (Firefox / Brave)

### Utilities

* dmenu – App launcher
* dex – XDG autostart
* xss-lock + i3lock – Screen locking
* NetworkManager + nm-applet – Network
* brightnessctl – Brightness control
* playerctl – Media control
* lm_sensors – Temperature monitoring
* feh – Wallpaper management
* flameshot – Screenshot tool
* xorg-xinput – Touchpad configuration
* blueman – Bluetooth
* usbutils – USB utilities

### Install all packages

```bash
sudo pacman -S i3 i3status kitty brave dmenu dex xss-lock i3lock \
networkmanager nm-applet brightnessctl playerctl lm_sensors feh \
flameshot xorg-xinput blueman usbutils
```

Enable NetworkManager:

```bash
sudo systemctl enable --now NetworkManager
```

Detect sensors:

```bash
sudo sensors-detect
```

---

When you **log into i3 for the first time**, you will be prompted to:

1. **Create a default i3 configuration** → choose **Yes**
2. **Select a modifier key** → choose **Win (Mod4)**

This creates:

```text
~/.config/i3/config
```

You must allow this step before replacing the config with dotfiles.

---

##  STEP 3: Apply i3 Dotfiles

This repository provides:

* i3 configuration → `~/.config/i3/config`
* i3status configuration → `~/.config/i3status/config`

After first login, copy the configs:

```bash
mkdir -p ~/.config/i3 ~/.config/i3status
cp config ~/.config/i3/config
cp i3status ~/.config/i3status/config
```

Reload i3:

```bash
Mod + Shift + C
```

---

## Overview of the i3 Setup

This i3 configuration includes:

* 10 custom workspaces
* Tiling & floating window management
* i3status bar with:

  * CPU usage & temperature
  * Memory & disk usage
  * Battery status
  * Volume & brightness
  * Wi‑Fi status
  * Clock
* Media control shortcuts
* Power management shortcuts
* Terminal: **kitty**
* Browser: **user choice (Firefox / Brave / etc.)**
* Wallpaper management via **feh**

---

##  Keyboard Shortcuts

All keyboard shortcuts are documented in: `i3_shortcuts.md`

---

##  Fix: USB Not Detected

If your USB appears in `lsusb` but not in the file manager, MTP support is missing.

Install required packages:

```bash
sudo pacman -S android-file-transfer mtpfs gvfs gvfs-mtp
```

Reconnect your phone and enable **File Transfer (MTP)** mode.

---
**It's good to have a fallback distro other i3**

## ❤️ Support My Work

If this setup helped you revive an old machine or learn Arch Linux, consider supporting the project.

Even a ⭐ on the repository helps a lot.

[<img width="120" height="120" alt="buymeacoffee" src="https://github.com/user-attachments/assets/3fb313a4-17ec-484a-9df5-11ff6056d0c0" />
](buymeacoffee.com/jesald)

---


