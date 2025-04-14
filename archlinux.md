# Archlinux

## Install
[How to Install Arch Linux: Step-by-Step Guide](https://www.youtube.com/watch?v=FxeriGuJKTM&t)

[Arch Linux One Of The Easiest Distros To Install](https://www.youtube.com/watch?v=y9nKjTfDHLA&t)

### How to manage the wifi in the terminal

`iwctl` Network manager

`station wlan0 get-networks` How to list all available networks

`iwctl --passphrase"pass" station wlan0 connect network-name`

## Windows Manager

### Awsome
I'm using a tile windows manager

## Tools

### Kitty 
Powerfull termina

### File Manager
#### Terminal base - Ranger
`sudo pacman -S ranger`

`ranger --copy-config=all`

Open `~/.config/ranger/rc.conf`

```
set preview_images true
set preview_images_method kitty
```

`ranger` to open in the terminal

#### GUI - Thunar

### Usb
Enable auto-mounting

`sudo pacman -S udiskie`

In the awesome config add `awful.spawn.with_shell("udiskie &")`
