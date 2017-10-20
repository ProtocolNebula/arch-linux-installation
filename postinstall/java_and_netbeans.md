# Java and NetBeans

We will install ```open jdk 8``` and ```netbeans``` for development.

The current version of netbeans is **8.2**, so we need open-jdk-8:

## Install Open JDK 8
```bash
pacaur -Suy jdk8-openjdk
```

## Changing the current JDK to 8
If we have an older version of JDK (7 for example), we have to run this command:
```bash
sudo archlinux-java set java-8-openjdk
```

If you don't need **netbeans**, you are done.


## Installing netbeans
I will install ```netbeans-es```, if you want to install the normal version, change it for ```netbeans```

```bash
pacaur -Suy netbeans-es
```

## Last steps with netbeans
Now you can launch netbeans.

I recommend the following plugins (install it from netbeans plugin manger **Tools --> Plugins**):

* Quick file chooser
* Darcula LAF
* Netbeans Use System Desktop
* LineLocator
* Copy and Paste History
* Show breadcrumbs at the top
* Show path in titlebar
* Markdown Support
* QuickOpener
* Show current GIT branch in statusbar
* JSHint - (for JavaScript developers)


That's all. Nice development!
