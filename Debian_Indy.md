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
<br>
<h3>2. Run on Command Monitor:</h3>

```
setenv netaddr 192.168.9.1
bootp():netboot-boot.img
```
** tip **<br>
- define a "debian" variable in Command Monitor:<br>
Indy: <b>setenv -p debian "bootp():netboot-boot.img"</b><br>
This way, you can run $debian in Command Monitor to easily start the Debian installation:<br>

```
setenv netaddr 192.168.9.1
$debian
```
(video) <a href=https://youtu.be/g21rlFwnXjY target="_blank">Indy booting Debian GNU/Linux 4.0 Etch installation</a><br>
<br>
<h3>3. Partitioning the hard disk</h3>
- reference: https://www.pvv.org/~pladsen/Indy/HOWTO.html<br>
- in my case:

```
dd if=/dev/zero of=/dev/sda count=1 bs=512
```
```
Use fdisk /dev/sda

Enter expert mode: x
Make disklabel: g
Leave expert mode: r
```
Cylinder size: cs=2048*512=1048576 bytes=1 MB<br>
The last cylinder: lc=8677<br>
<br>
Start of 	volume header = 0<br>
End of	volume header:	ev	= 50 / cs = 50<br>
Start of	Linux swap:	ss 	= lc - 128/cs = 8677-128/1 = 8549<br>
End of	Linux swap:	es	= lc = 8677<br>
Start of	Linux native:	sn	= ev + 1 = 51<br>
End of	Linux native:	en	= ss - 1 = 8548<br>

Make the Linux partition: d - 1 - n - 1 - sn - en<br>
Make the volume header: d - 9 - n - 9 - 0 - ev<br>
Make the swap partition: d - 2 - n - 2 - ss - es - t - 2 - 82<br>
--><br>
Make the Linux partition: d - 1 - n - 1 - 51 - 8548<br>
Make the volume header: d - 9 - n - 9 - 0 - 50<br>
Make the swap partition: d - 2 - n - 2 - 8549 - 8677 - t - 2 - 82<br>
Write the table to disk: w<br>
<br>
<h3>4. Selecting a mirror</h3>
- when asked, type a custom hostname for the mirror: archive.debian.org and accept "/debian/" as directory:<br>
<img src="Debian_mirror_hostname.jpg" align="middle"><br>
<img src="Debian_mirror_directory.jpg" align="middle"><br>
An Indy is a pretty slow machine, the installation process wil take <b>at least</b> 6 hours, please be patient.
<br>
<h3>5. Making it boot</h3>
- reference: Debian installation<br>
<img src="Debian_arcboot.jpg" align="middle"><br>
<img src="Debian_command_monitor.jpg" align="middle"><br>

```
setenv OSLoader arcboot
setenv OSLoadFilename Linux
setenv SystemPartition dksc(0,1,8)
setenv OSLoadPartition dksc(0,1,0)
```
<h3>6. Tips</h3>
- an Indy is a pretty slow machine, the installation process will take <b>at least</b> 6 hours, please be patient.<br>
- install some utilities after installation:<br>

```
indy:~# aptitude install openssh-server screen
```
- to avoid this error:

```
~$ ssh user@IP
Unable to negotiate with IP port 22: no matching key exchange method found. Their offer: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
```
- use this command:

```
~$ ssh -oKexAlgorithms=+diffie-hellman-group1-sha1 user@IP
```
