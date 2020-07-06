# My Tools

I currently run insider Windows 10 Professional with Windows Subsystem for Linux 2 enabled.

[Setup a Linux development environment](https://nickjanetakis.com/blog/a-linux-dev-environment-on-windows-with-wsl-2-docker-desktop-and-more).

Get started with [VxXsrv](https://sourceforge.net/p/vcxsrv/wiki/VcXsrv%20%26%20Win10/) to [run graphical programs from WSL](https://sourceforge.net/p/vcxsrv/wiki/VcXsrv%20%26%20Win10/).

You can test the graphical integration by starting `XLaunch` from Windows, installing `gedit` in WSL (`sudo apt update && sudo apt install gedit`), and running it from WSL (`gedit`).

Follow the instructions in [this answer](https://askubuntu.com/a/1127013/1101219), if you see the following errors in output:

```
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
```
