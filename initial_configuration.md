# Initial configuration
<img alt="REANIMATOR.jpg" src="REANIMATOR.jpg" align="middle"><br>
<br>
1. Default IP address<br>
- Raspberry Pi: rbpi, 192.168.9.100<br>
- VirtualBox: debian, 192.168.9.101<br>
<br>
2. Users and passwords<br>
<table>
  <tr>
    <th style="color:white">user</th>
    <th style="color:white">password</th>
    <th style="color:white">comment</th>
  </tr>
  <tr>
    <td style="color:white">root</td>
    <td style="color:white">reanimator</td>
    <td style="color:white">ssh login disabled</td>
  </tr>
  <tr>
    <td style="color:white">pi</td>
    <td style="color:white">reanimator</td>
    <td style="color:white">Debian on Raspberry Pi, log in to configure this server</td>
  </tr>
  <tr>
    <td style="color:white">sgi</td>
    <td style="color:white">reanimator</td>
    <td style="color:white">Debian on VirtualBox, log in to configure this server</td>
  </tr>
</table>
<br>
3. Log in and use the menu to configure network<br>
<br>
4. Download IRIX versions using Reanimator menu or copy through the network your own downloads, these services are enabled:<br>
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
<br>
If you avoid Reanimator IRIX downloads, you can download your own IRIX versions, uncompress and upload them to Reanimator using a similar directory structure. For example, use <a href=http://ftp.irixnet.org/sgi-irix/ target="_blank">http://ftp.irixnet.org/sgi-irix/</a> as download site.<br>
