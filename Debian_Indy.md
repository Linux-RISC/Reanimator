# Installing Debian GNU/Linux on SGI Indy
<img alt="REANIMATOR.jpg" src="REANIMATOR.jpg" align="middle"><br>
<br>
<h3>1. Download the file netboot-boot.img and store it on Reanimator's directory /home/irix/i/h3>
http://archive.debian.org/debian/dists/etch/main/installer-mips/current/images/r4k-ip22/netboot-boot.img
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
https://youtu.be/cjAT91gEH6k<br>
https://youtu.be/1uvcMV_5HZc<br>

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
