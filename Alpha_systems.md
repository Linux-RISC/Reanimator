# Support for Alpha systems
<img alt="REANIMATOR.jpg" src="REANIMATOR.jpg" align="middle"><br>
<br>
<h3>Edit /etc/booptab using Reanimator's menus</h3>
- download and save the boot file on /home/irix/i<br>
- specify the MAC of your Alpha system<br>
- optionally, customize IP and subnet mask<br>
- run on SRM:<br>

```
set ewa0_protocols bootp
boot ewa0
```
- if you want to load a different file, run on SRM:<br>

```
set ewa0_protocols bootp
boot -file my_boot_filename ewa0
```
<a href=https://youtu.be/cjAT91gEH6k target="_blank">AlphaStation DS10 booting Debian 5.0.10 lenny installation using network boot on Reanimator</a><br>
<a href=https://youtu.be/1uvcMV_5HZc target="_blank">AlphaStation DS10 booting Tru64 vmunix1 (generated on RIS) using network boot on Reanimator</a><br>

```
# configuration to netboot an Alpha system
# run on SRM:
# set ewa0_protocols bootp
# boot ewa0
Alpha:\
# OS		file name	link
# Debian	boot.img	http://archive.debian.org/debian/dists/lenny/main/installer-alpha/current/images/netboot/
# NetBSD	netboot		https://cdn.netbsd.org/pub/NetBSD/NetBSD-9.2/alpha/installation/netboot/
# OpenBSD	netboot		https://cdn.openbsd.org/pub/OpenBSD/7.1/alpha/
bf=boot.img:\
# IP address assigned to Alpha
ip=192.168.9.14:\
sm=255.255.255.0:\
# write here your Alpha MAC address
ha=c60000000001:
```
