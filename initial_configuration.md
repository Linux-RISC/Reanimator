# Initial configuration
<img alt="REANIMATOR.jpg" src="REANIMATOR.jpg" align="middle"><br>
<br>
<h3>1. Default IP address</h3>
- Raspberry Pi: rbpi, 192.168.9.100<br>
- VirtualBox: debian, 192.168.9.101<br>
<br>
<h3>2. Users and passwords</h3>
<table>
  <tr>
    <th>user</th>
    <th>password</th>
    <th>comment</th>
  </tr>
  <tr>
    <td>root</td>
    <td>reanimator</td>
    <td>ssh login disabled</td>
  </tr>
  <tr>
    <td>pi</td>
    <td>reanimator</td>
    <td>Debian on Raspberry Pi, log in to configure this server</td>
  </tr>
  <tr>
    <td>sgi</td>
    <td>reanimator</td>
    <td>Debian on VirtualBox, log in to configure this server</td>
  </tr>
</table>

<h3>3. Log in and use Reanimator's menu to configure network</h3>
- Windows: use <a href="https://www.putty.org/" target="_blank">putty</a> to connect to Reanimator and use the table above to select user and IP address.<br>
- GNU/Linux: run on a shell <b>ssh pi@192.168.9.100</b> for Rasberry Pi or <b>ssh sgi@192.168.9.101</b> for VirtualBox.<br>
<br>
Example of Reanimator's menu:<br>

```
 --------------------------------------------------- 
| REANIMATOR server v1.2.1 - http://irix.mersisl.com/ |
 --------------------------------------------------- 

* enabled services *
sudo, ntp client, bootp, tfptp, rsh, ssh, sftp, anonymous FTP, NFS (versions 2, 3, 4, 4.1, 4.2), Samba, AppleTalk

* selections file templates *
selection file                    system software path            common partition command
irix@rbpi:i/MIPSPro.txt
irix@rbpi:i/5.3.txt               IRIX/irix53/1/dist            bootp():IRIX/irix53/1/stand/fx.ARCS
irix@rbpi:i/6.2.txt               IRIX/irix62/1/dist            bootp():IRIX/irix62/1/stand/fx.ARCS or fx.64
irix@rbpi:i/6.5.0.txt             IRIX/irix650/1/dist           bootp():IRIX/irix650/1/stand/fx.ARCS or fx.64
irix@rbpi:i/6.5.7.txt             IRIX/irix657/1/dist           bootp():IRIX/irix657/1/stand/fx.ARCS or fx.64
irix@rbpi:i/6.5.22.txt            IRIX/6.5.22/ovl1/dist         bootp():IRIX/6.5.22/ovl1/stand/fx.ARCS or fx.64
irix@rbpi:i/6.5.30.txt            IRIX/6.5.30/disc1/dist        bootp():IRIX/6.5.30/disc1/stand/fx.ARCS or fx.64

name of the server: rbpi(Raspberry Pi 192.168.9.100) or debian(VirtualBox 192.168.9.101)
Default clients defined in /etc/bootptab and /etc/hosts: IRIS:ip=192.168.9.1 and IRIS2:ip=192.168.9.2

0. Show changelog.txt
1. Network configuration menu
2. Download menu
3. Automount ISO images menu
4. Mount /dev/sda1 menu (Raspberry Pi only)
5. tcpser menu - emulate a Hayes compatible modem
6. Diskless workstation menu

10. Get Reanimator scripts updated from the Internet
11. Update this system
12. Reboot this system
13. Shut down this system

99. Exit
enter your selection:
```
<h3>4. Download IRIX versions using Reanimator menu or copy through the network your own downloads, these services are enabled:</h3>
sudo, ntp client, bootp, tfptp, rsh, ssh, sftp, anonymous FTP, NFS (versions 2, 3, 4, 4.1, 4.2), Samba, AppleTalk, tcpser<br>
<br>
This is the directory structure under /home/irix used by Reanimator when downloading IRIX versions:<br>
/i<br>
&ensp;/6.5.22<br>
&ensp;&ensp;/ovl1<br>
&ensp;&ensp;/ovl2<br>
&ensp;&ensp;/ovl3<br>
&ensp;&ensp;/apps<br>

&ensp;/6.5.30<br>
&ensp;&ensp;/disc1<br>
&ensp;&ensp;/disc2<br>
&ensp;&ensp;/disc3<br>
&ensp;&ensp;/apps<br>
&ensp;&ensp;/capps<br>

&ensp;/MIPSPro<br>
&ensp;&ensp;/...<br>

&ensp;/irix53<br>
&ensp;&ensp;/...<br>

&ensp;/irix62<br>
&ensp;&ensp;/...<br>

&ensp;/irix650<br>
&ensp;&ensp;/...<br>

&ensp;/irix657<br>
&ensp;&ensp;/...<br>

&ensp;/irix65x<br>
&ensp;&ensp;/...<br>

If you avoid Reanimator IRIX downloads, you can download your own IRIX versions, uncompress and upload them to Reanimator using a similar directory structure. For example, use <a href=http://ftp.irixnet.org/sgi-irix/ target="_blank">http://ftp.irixnet.org/sgi-irix/</a> as download site.<br>
