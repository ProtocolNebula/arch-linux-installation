# Install arch linux UEFI and/or GPT disks

Original guide: https://github.com/p4block/Yet-another-Arch-install-guide

**CURRENT THIS IS A COPY PASTE WITH SOME MODIFICATIONS**


Let's start. 

This assumes your target disk is /dev/sda, you are running UEFI, you want rEFInd because it's cool, you are wired into ethernet for the install process, you use US keyboard, and mostly understand english


## Keyboard

If need to change keyboard distribution execute: (change **es** to your locale)
```bash
loadkeys es
```

## Network

If you can connect to network via wifi/ethernet, link your Android Phone via usb

After 10/20 seconds try to ```ping 8.8.8.8```

If not working...

```bash
ip addr
```

You will see some connections, the first will be ```lo```, one of them will be like ```enp0...``` (**enp0s29u1u1** in my case)

```
dhcpcd enp0s29u1u1
```


## Partitioning

```bash
cgdisk /dev/sda
```
### 1.1. If disk clean / you have NOT other EFI partition

	/dev/sda1 /boot 100M
	/dev/sda2 /     $CUSTOM_SPACE

### 1.2. Install with another EFI partition

	/dev/sdaX ...
	/dev/sdaX EFI (already working)
	...
	/dev/sda5 /boot 100M - OUR EFI (wi will have 2 EFI, this will be the main)
	/dev/sda6 /		$CUSTOM_SPACE - Arch installation

### 2. Formatting partitions

**IMPORTANT:** Change `sda1` and `sda2` with the corresponding partitions.

If you installing over an existing windows EFI, this should be `sda5` and `sda6`.

```bash
mkfs.vfat -F 32 /dev/sda1
mkfs.ext4 /dev/sda2

mount /dev/sda2 /mnt
mkdir /mnt/boot
mount /dev/sda1 /mnt/boot
```

## Actual install
Install all packages needed (add what you need!)

```bash
pacstrap -i /mnt base base-devel refind-efi xorg-server gnome gnome-extra firefox networkmanager htop zsh grml-zsh-config

genfstab -U /mnt >> /mnt/etc/fstab 
```

## Get in there to configure

```bash
arch-chroot /mnt /bin/zsh

echo "en_US.UTF-8 UTF-8" > /etc/locale.gen
echo LANG=en_US.UTF-8 > /etc/locale.conf

locale-gen

echo arch > /etc/hostname
```

## Users

```bash
passwd
chsh root -s /bin/zsh

useradd -m -G wheel -s /bin/zsh user
passwd user
``` 
## Enable services

```bash
systemctl enable NetworkManager
systemctl enable gdm
```

## Bootloader

```bash
refind-install 
```

## Kernel cmdline
Basically edit your boot options to be 'rw root=/dev/sda2', as sometimes rEFInd doesn't make this automatically

```bash
nano /boot/refind_linux.conf 
```

## Rebooting to new installed system

```bash
exit
reboot
```

## Disabling Beep on "error" keyboard key press

Put this in `.basrc`

```bash
xset b off 
```

## Next steps
You should see **[postinstall](postinstall/)** folder to install things such "Desktop enviornment" (like [xfce](postinstall/Desktop-xfce.md))

