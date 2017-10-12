# Install arch linux in MBR/BIOS computer

This process is very similar to UEFI method, but changing 2 things:

We will use ```fdisk``` instead ```cgdisk``` and will install ```grub``` for bootloader.



## Keyboard

If need to change keyboard distribution execute: (change **es** to your locale)
```
loadkeys es
```

Full guide (in process of transcode to here with my settings and edit steps):

https://blog.m157q.tw/posts/2013/12/30/arch-linux-quick-installation-with-gpt-in-bios/




## Lasts steps

### Other partitions

If we have Windows or another system which is not recognized by grub, we have to edit the file:

```bash
sudo vim /etc/grub.d/40_custom
```

And add this at the **end** of file (edit with your configurations):
```bash
menuentry "Windows 7" {  
     insmod ntfs  
     set root='(hd0,1)'  
     #search --no-floppy --fs-uuid --set a3f1ea41fc67a3f1  
     chainloader +1  
}
```


## Next steps
You should see **[postinstall](postinstall/)** folder to install things such "Desktop enviornment" (like [xfce](postinstall/Desktop-xfce.md))
