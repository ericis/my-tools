# My Tools

I currently run insider Windows 10 Professional with Windows Subsystem for Linux 2 enabled.

[Setup a Linux development environment](https://nickjanetakis.com/blog/a-linux-dev-environment-on-windows-with-wsl-2-docker-desktop-and-more).

## WSL and VxXsrv

Get started with [VxXsrv](https://sourceforge.net/p/vcxsrv/wiki/VcXsrv%20%26%20Win10/) to [run graphical programs from WSL](https://sourceforge.net/p/vcxsrv/wiki/VcXsrv%20%26%20Win10/).

You can test the graphical integration by starting `XLaunch` from Windows, installing `gedit` in WSL (`sudo apt update && sudo apt install gedit`), and running it from WSL (`gedit`).

Follow the instructions in [this answer](https://askubuntu.com/a/1127013/1101219), if you see the following errors in output:

```
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
```

## WSL and xfce4 and xrdp

For Ubuntu 18, we're going to install a graphical interface for WSL and use Windows Remote Desktop to login.

To get an overview, watch how this person [installed xfce4 on Kali for Linux on WSL](https://www.youtube.com/watch?v=dAoIEoszHa0). _We'll follow some slightly different steps._

### New `xrdp` Steps

1. Follow the steps outlined in Griffin's IT Library for ["Easy install xRDP on Ubuntu"](https://c-nergy.be/blog/?p=14888).
2. For sound to work in Remote Desktop, you can append the pulseaudio command to your xsession (e.g. `echo pulseaudio --start >> ~/.xsession`)

### Old `xrdp` Steps

_You will see `/etc/init.d/xrdp start` used instead of `systemctl start xrdp`. This is because `systemd` is [not installed on WSL](https://github.com/MicrosoftDocs/WSL/issues/457#issuecomment-511495846)._

We are going to modify [these instructions](https://linuxize.com/post/how-to-install-xrdp-on-ubuntu-18-04/) a little for WSL.

```
$ sudo apt update
 ...
$ sudo apt install xfce4 xfce4-goodies xorg dbus-x11 x11-xserver-utils
 ...
$ sudo apt install xrdp
 ...
$ sudo adduser xrdp ssl-cert
$ sudo /etc/init.d/xrdp start
 * Starting Remote Desktop Protocol server
$ sudo service xrdp status
 * xrdp-sesman is running
 * xrdp is running
```

Now, we need to configure xrdp and the xfce4

$ hostname -I
 xxx.xx.xxx.xx
```

Copy the IP address from `hostname -I`.

Now, open Windows Remote Desktop and paste the IP in "Computer", but append `:3389` for the xrdp port.

## WSL Example Files

- [~/.bashrc](./linux/.bashrc) *runs for every terminal session
- [~/.xsession](./linux/.xsession) *runs for every remote desktop session
