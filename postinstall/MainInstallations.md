# Main installations for Arch Linux (after install)

**Is recommended to use ```pacaur```**, so the first thing that we will install is "pacaur":

## Pacaur
Pacaur is an alternative to ```pacman``` (include pacman repository).

**IMPORTANT**: Pacaur must be used **without** root.

```bash
git clone https://github.com/p4block/yet-another-pacaur-installer.git
cd yet-another-pacaur-installer
sh install.sh
```

# Other installations
From now I only explain the main packages that I use, to install ALL (and maybe another more), you can run:

**REMEMBER:** Execute this with your user, NOT WITH ROOT (sudo)
```bash
pacaur -Suy pulseaudio gedit banshee qt4 file-roller p7zip zip unzip unrar
```

## Information packages
This section only explain some previous packages

### Fix sound (pulseaudio)
To fix sound we will install ```pulseaudio```

### Banshee
Media player

### Gedit
A graphical text editor

### xarchiver
Compressed file manager (tar, zip...)

### qt4 (libqtgui4)
Graphical library
