<a href="https://www.buymeacoffee.com/rbpiuserf" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>

Last update: 2024/05/22
# Reanimator
<img alt="REANIMATOR.jpg" src="REANIMATOR.jpg" align="middle"><br>
<br>
Reanimator allows Silicon Graphics IRIX network installation using a Raspberry Pi or VirtualBox<br>
<br>
Download link: https://mega.nz/folder/7jJGlSSS#d25XyA8RhKJyoU2uSrlasw<br>
<br>
Select a version to download:<br>
<ul>
<li>Lite (Reanimator-Pi-server-SD16GB-no-images.img.tar.gz): ~740 MB, no IRIX images included, automatically download the images you need or customize your own IRIX installation. Versions available for downloading: 5.3, 6.2, 6.5.0, 6.5.7, 6.5.22 and 6.5.30.</li>
<li>Full (Reanimator-Pi-server-SD16GB-IRIX-included.img.tar.gz): ~9 GB, includes several IRIX versions for offline installation: 5.3, 6.2, 6.5.22 and 6.5.30.</li>
<li>Experimental (Reanimator-Pi-server-SD16GB-no-images-netatalk-2.1.6.img.tar.gz): ~1 GB, the Little image but including support for AppleTalk 2, protocol used on old Mac computers.</li>
<li>If you don't have a Raspberry Pi, please try using the VirtualBox version (Debian i386-IRIX install.vdi.tar.gz), ~550 MB, it's much slower but still functional.</li>
</ul>
<br>
Tested sgi models:
<table>
  <tr>
    <th>sgi model</th>
    <th>IRIX versions</th>
    <th>tester</th>
  </tr>
  <tr>
    <td>Indy R4400 150 MHz, 24-bit graphics</td>
    <td>5.3 6.2 6.5.0 6.5.7 6.5.22</td>
    <td>Linux-RISC</td>
  </tr>
    <td>Octane2 R12000 400 MHz, ODYSSEY V6</td>
    <td>6.5.30</td>
    <td>Linux-RISC</td>
  </tr>
    <td>Indy R4400 200 MHz, 24-bit graphics<br>Indy R4400 150 MHz, 8-bit graphics</td>
    <td>5.3 6.2 6.5.x</td>
    <td>kikems</td>
   </tr>
    <td>O2 R5000 180 MHz</td>
    <td>6.3</td>
    <td>kikems</td>
  </tr>
    <td>O2 R5000 180 MHz<br>O2 R12000 400 MHz</td>
    <td>6.5.4 6.5.7 6.5.22</td>
    <td>kikems</td>
  </tr>
    <td>Octane R10000 250 MHz</td>
    <td>6.5.22</td>
    <td>kikems</td>
  </tr>
    <td>Indigo 2 R4400 250 MHz, Extreme Impact</td>
    <td>5.3 6.2 6.5.4</td>
    <td>kikems</td>
  </tr>
    <td>Crimson</td>
    <td>5.3</td>
    <td>kikems</td>
  </tr>
</table>
<br>
Tested non-sgi computers or non-IRIX OS:
<table>
  <tr>
    <th>model</th>
    <th>OS</th>
    <th>file</th>
  </tr>
  <tr>
    <td>AlphaStation DS10</td>
    <td>Debian<br>NetBSD<br>OpenBSD<br>Tru64</td>
    <td>http://archive.debian.org/debian/dists/lenny/main/installer-alpha/current/images/netboot/<br>
        https://cdn.netbsd.org/pub/NetBSD/NetBSD-9.2/alpha/installation/netboot/<br>
        https://cdn.openbsd.org/pub/OpenBSD/7.1/alpha/<br>
        vmunix1 (generated using RIS)
    </td>
  </tr>
    <td>Indy R4400 150 MHz, 24-bit graphics</td>
    <td>Debian GNU/Linux 4.0 Etch</td>
    <td>http://archive.debian.org/debian/dists/etch/main/installer-mips/current/images/r4k-ip22/netboot-boot.img</td>
</table>

<a href=restoring_image.md target="_blank">Restoring Reanimator image</a><br>
<a href=initial_configuration.md target="_blank">Initial configuration</a><br>
<a href=accessing_files.md target="_blank">Accessing files</a><br>
<a href=install_guide.md target="_blank">IRIX install guide</a><br>
<br>
Advanced topics:<br>
<a href=network_setup.md target="_blank">Network setup</a><br>
<a href=https://github.com/Linux-RISC/IRIX-diskless-workstation target="_blank">IRIX diskless workstation documentation</a><br>
<a href=https://github.com/Linux-RISC/IRIX-diskless-workstation/blob/main/classic-IRIX-diskless-workstation.md target="_blank">(classic and limited) sgi IRIX diskless workstation documentation</a><br>
<br>
Support for other systems:<br>
<a href=Alpha_systems.md target="_blank">Support for Alpha systems</a><br>
<a href=Debian_Indy.md target="_blank">Installing Debian GNU/Linux on SGI Indy</a><br>
<br>
Change log:<br>
1.2.4<br>
- Custom menu support<br>
<br>
1.2.3<br>
- support for Raspberry Pi TNFS Server Package (FujiNet https://fujinet.online/download/)<br>
<br>
1.2.1<br>
- return to tftpd: Octane (among others) won't boot with tftpd-hpa. Please, download the image again.<br>
<br>
1.2<br>
- IRIX 6.3 available for download, tested by kikems (thanks!)<br>
- automatic checking and creation of directories under /home/irix and /diskless<br>
- update from 1.1: just update Reanimator scripts from the Internet<br>
- updated install guide<br>
<br>
1.1<br>
- tftpd replaced by tftpd-hpa<br>
- pub directory for ftp<br>
- simplified paths for tftp: removed heading "i/"<br>
- Alpha systems netboot template (check /etc/bootptab)<br>
- updated documentation and videos<br>
<br>
1.0<br>
- Diskless workstation support, visit this page for instructions.<br>
- NFS v4 disabled<br>
- IPv6 disabled<br>
<br>
0.9<br>
- Raspberry Pi: network assistant to select wired or Wi-Fi connection to the Internet. The RBPi will work as a router for your sgi computer, allowing access to the Internet through your Wi-Fi network<br>
<br>
0.8<br>
- IRIX downloads from the Internet<br>
- added Midnight Commander to browse directories<br>
- update Reanimator scripts from the Internet<br>
<br>
