# Arch Linux (post install) in my HP Pavilion dv5

## Packages in installation process (can be installed after OS installation)
```bash
pacstrap xfce4 xfce4-goodies gvfs polkit-gnome
```

```bash
git clone https://github.com/p4block/yet-another-pacaur-installer.git
cd yet-another-pacaur-installer
sh install.sh
pacaur -Suy ntpdate pulseaudio gedit banshee qt4 file-roller p7zip zip unzip unrar jdk8-openjdk netbeans-es
sudo archlinux-java set java-8-openjdk
```
