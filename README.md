<a href="https://www.buymeacoffee.com/rbpiuserf" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>

Last update: 2023/08/13
# Reanimator
<img alt="REANIMATOR.jpg" src="REANIMATOR.jpg" align="middle"><br>
<br>
Reanimator allows Silicon Graphics IRIX network installation using a Raspberry Pi or VirtualBox<br>
<br>
Download link: https://mega.nz/folder/7jJGlSSS#d25XyA8RhKJyoU2uSrlasw<br>
<br>
Select version to download:<br>
Lite (Reanimator-Pi-server-SD16GB-no-images.img.tar.gz): ~740 MB, no IRIX images included, automatically download the images you need or customize your own IRIX installation. Versions available for downloading: 5.3, 6.2, 6.5.0, 6.5.7, 6.5.22 and 6.5.30.<br>
Full (Reanimator-Pi-server-SD16GB-IRIX-included.img.tar.gz): ~9.7 GB, includes several IRIX versions for offline installation: 5.3, 6.2, 6.5.22 and 6.5.30.<br>
If you don't have a Raspberry Pi, please try using the VirtualBox version (Debian i386-IRIX install.vdi.tar.gz), ~550 MB, it's much slower but still functional.<br>

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
<a href=alpha_systems.md target="_blank">Support for Alpha systems</a><br>
<a href=https://youtu.be/g21rlFwnXjY target="_blank">Indy booting Debian GNU/Linux 4.0 Etch installation</a><br>

Change log:<br>
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
