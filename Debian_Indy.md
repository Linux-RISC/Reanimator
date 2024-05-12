# Installing Debian GNU/Linux on SGI Indy
<img alt="REANIMATOR.jpg" src="REANIMATOR.jpg" align="middle"><br>
<br>
According to my experience, installing Debian GNU/Linux on Indy using netinstall CD or net boot has these issues:<br>
9, 10, ... : for specific motherboards, incompatible with Indy<br>
8: strange chars are shown on boot and freezes https://www.youtube.com/watch?v=pADq72n-V_0<br>
7, 6, 5: error copying kernel to disk: "WARNING: the following packages cannot be authenticated". The package is kernel_version-r4k-ip22<br>
4: installation Ok<br>
<br>
<h3>1. Download the file netboot-boot.img and store it on Reanimator's directory /home/irix/i</h3>
- download link: http://archive.debian.org/debian/dists/etch/main/installer-mips/current/images/r4k-ip22/netboot-boot.img<br>
<h3>2. Run on Command Monitor:</h3>

```
setenv netaddr 192.168.9.1
bootp():netboot-boot.img
```

** tip **<br>
- define a "Debian" variable in Command Monitor:<br>
Indy: <b>setenv -p Debian "bootp():netboot-boot.img"</b><br>
<br>
This way, you can run $Debian in Command Monitor to easily start the disk partitioning program<br>
<br>

```
setenv netaddr 192.168.9.1
$Debian
```


tip: to 
setenv netaddr 192.168.9.1
bootp():netboot-boot.img

- define a "part" variable in Command Monitor:<br>
Indy: <b>setenv -p part "bootp():IRIX/6.5.22/ovl1/stand/fx.ARCS -x"</b><br>

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
