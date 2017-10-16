# Configuring date

If you have problems with date (maybe your computer battery don't work or something), you maybe need to autoconfigure the date with ```a remote server``` everytime you boot linux.

## Installing

```bash
pacaur -Sy ntpdate
```

## Testing: Sync time with a remote server
```bash
sudo ntpdate 0.es.pool.ntp.org
```

You can change ```es``` (or the full domain) if you need it, for example, you can use instead:
```bash
sudo ntpdate 0.us.pool.ntp.org
```

## Auto update date on boot
We will create a ```init``` script what will be executed in each boot.

```bash
vim /etc/init.d/sync_date
```

Insert the next code:

```bash
#!/bin/sh
sudo ntpdate 0.es.pool.ntp.org
```

Change permissions for the file and copy to ```rc.d``` (only required in some cases):

```bash
chmod a+x /etc/init.d/sync_date
ln -s /etc/init.d/sync_date /etc/rc.d/
```


Reboot your machine and test it!