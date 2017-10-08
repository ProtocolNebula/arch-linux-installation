# Installing Desktop - XFCE

## Thanks to
https://blog.desdelinux.net/instalacion-de-xfce-en-arch-linux

## Guide

### Minimal

#### Desktop enviornment
```bash
sudo pacman -S xfce4 xfce4-goodies
```

#### Boot manager (login window)
```bash
sudo pacman -S lightdm lightdm-gtk2-greeter
systemctl enable lightdm
```


### Recommended
```bash
sudo pacman -S gamin xfce4-notifyd network-manager-applet volumeicon
```
- **gamin**: File and directory monitor
- **notifyd**: Notification support
- **volumeicon**:  Audio settings


### Keyboard locale

If your locale is incorrect, open **Keyboard Settings** -> **Distribution** and change **Keyboard Distribution** (maybe you have to uncheck **Keyboard model**)
