Last update: 2024/05/24<br>
# IRIX install guide
<img alt="REANIMATOR.jpg" src="REANIMATOR.jpg" align="middle">

<h3>1. Setting IP client address in Command Monitor</h3>
To enter Comand Monitor, boot your SGI computer and click on "Stop for Maintenance dialog" or press Esc. Click on "Enter Command Monitor" or press "5" (on Indy, numbers can change on other sgi model).<br>
Two IP client addresses are available:<br>
IRIS: <b>setenv netaddr 192.168.9.1</b><br>
or<br>
IRIS2: <b>setenv netaddr 192.168.9.2</b><br>
<br>
To reboot from disk 1 after the installation, run in Command Monitor:

```
>>setenv SystemPartition dksc(0,1,8)
>>setenv OSLoadPartition dksc(0,1,0)
>>setenv OSLoader sash
>>setenv OSLoadFilename unix
```
<br>
<h3>2. Starting the partition tool in Command Monitor</h3>
"Selecting the Correct fx/sash Version" on <a href=https://software.majix.org/irix/install-network.shtml target="_blank">https://software.majix.org/irix/install-network.shtml</a><br>
<br>
Check the documentation for your sgi model, several tested examples are provided:<br>
Indy:<br>
<b>bootp():IRIX/6.5.22/ovl1/stand/fx.ARCS -x</b><br>
<b>bootp():IRIX/irix53/1/stand/fx.ARCS -x</b><br>
<b>bootp():IRIX/irix62/1/stand/fx.ARCS -x</b><br>
<b>bootp():IRIX/irix650/1/stand/fx.ARCS -x</b><br>
<b>bootp():IRIX/irix657/1/stand/fx.ARCS -x</b><br>
<br>
Octane2:<br>
<b>bootp():IRIX/6.5.30/disc1/stand/fx.64 -x</b><br>
<b>bootp():IRIX/irix650/1/stand/fx.64 -x</b><br>
<b>bootp():IRIX/irix657/1/stand/fx.64 -x</b><br>
<br>
** tip **<br>
- define a "part" variable in Command Monitor:<br>
Indy: <b>setenv -p part "bootp():IRIX/6.5.22/ovl1/stand/fx.ARCS -x"</b><br>
Octane2: <b>setenv -p part "bootp():IRIX/6.5.30/disc1/stand/fx.64 -x"</b><br>
<br>
This way, you can run $part in Command Monitor to easily start the disk partitioning program<br>
<br>
<b>Troubleshooting</b><br>
If the disk partition program doesn't start, please check:<br>
&ensp;1. netaddr is properly configured in Command Monitor.<br>
&ensp;2. if the problem persists, connect your sgi computer to Reanimator using a straight-through cable, not a crossover.<br>
&ensp;3. in cases 1 and 2, you can try type the server name before ":", for example: "bootp()rbpi:IRIX/6.5.22/ovl1/stand/fx.ARCS -x".<br>
&ensp;This problem is described on "Bootpd server receives requests, but ignores them." <a href=http://techpubs.spinlocksolutions.com/irix/remote-irix-6.5-installation-from-linux.html target="_blank">http://techpubs.spinlocksolutions.com/irix/remote-irix-6.5-installation-from-linux.html</a> and is logged on /var/log/daemon.log<br>
<br>
<h3>3. Partitioning the hard disk</h3>
<a href=http://ibgwww.colorado.edu/~lessem/psyc5112/usail/peripherals/disks/adding/sgi.html target="_blank">http://ibgwww.colorado.edu/~lessem/psyc5112/usail/peripherals/disks/adding/sgi.html</a><br>
Warning: depending on the documentation used, the procedure can be slightly different. I assume that your drive is neither labeled nor partitioned.<br>
If you know what you are doing, you could skip some of these steps.<br>
Press Enter a couple of times to select the default system disk on SCSI controller 0, ID 1, lun 0<br>
fx> [l]abel<br>
fx/label> [c]reate<br>
fx/label/create> [a]ll<br>
fx/label/create> ..<br>
fx/label> [sy]nc<br>
fx/label> ..<br>
fx> [r]epartition<br>
fx/repartition> [ro]otdrive<br>
fx/repartition/rootdrive: type of data partition = (xfs)<br>
fx/repartition> /exit<br>
<br>
<h3>4. Starting the installer from network</h3>
- Enter System Maintenance menu, press 2 or click on "Install system software"<br>
- Press 2 or click on "From remote directory"<br>
- Enter "rbpi" or "debian" (according to the installation platform) as "server name", NOT the IP address<br>
- For example:<br>
Indy:<br>
IRIX/6.5.22/ovl1/dist<br>
<br>
Octane2:<br>
IRIX/6.5.30/disc1/dist for Octane2<br>
<br>
General table for each IRIX version:<br>
<table>
  <tr>
    <th>IRIX version</th>
    <th>Remote directory</th>
  </tr>
  <tr>
    <td>5.3</td>
    <td>IRIX/irix53/1/dist</td>
  </tr>
    <td>6.2</td>
    <td>IRIX/irix62/1/dist</td>
  </tr>
    <td>6.3</td>
   <td>IRIX/irix63/1/dist</td>
   </tr>
    <td>6.5.0</td>
    <td>IRIX/irix650/1/dist</td>
  </tr>
    <td>6.5.7</td>
    <td>IRIX/irix657/1/dist</td>
  </tr>
    <td>6.5.22</td>
    <td>IRIX/6.5.22/ovl1/dist</td>
  </tr>
    <td>6.5.30</td>
    <td>IRIX/6.5.30/disc1/dist</td>
  </tr>
</table>
<br>
If asked for system name or IP, specify the name/IP according the netaddr variable in Command Monitor:<br>
IRIS for 192.168.9.1<br>
IRIS2 for 192.168.9.2<br>
<br>
<b>Troubleshooting</b><br>
If the installer program doesn't start, please check:<br>
&ensp;1. netaddr is properly configured in Command Monitor.<br>
&ensp;2. if the problem persists, connect your sgi computer to Reanimator using a straight-through cable, not a crossover.<br>
&ensp;3. if the problem persists again, you must try to boot the installer program using the "hard way", booting from Command Monitor.<br>
(pending review) Read this page <a href=https://software.majix.org/irix/install-network.shtml target="_blank">https://software.majix.org/irix/install-network.shtml</a> and select the right command according to your sgi model and IRIX version, for example:<br>
&ensp;- Indy, 6.5.22 and RBPi: bootp():IRIX/6.5.22/ovl1/dist/miniroot/unix.IP22 or bootp()rbpi:IRIX/6.5.22/ovl1/dist/miniroot/unix.IP22<br>
&ensp;- Indy, 6.2 and RBPi: bootp():IRIX/irix62/1/stand/sashARCS or bootp()rbpi:IRIX/irix62/1/stand/sashARCS<br>
&ensp;- Indy, 5.3 and RBPi: bootp():IRIX/irix53/1/stand/sashARCS or bootp()rbpi:IRIX/irix53/1/stand/sashARCS<br>
&ensp;- Octane2, 6.5.20 and RBPi: bootp():IRIX/6.5.30/disc1/stand/sash64 or bootp()rbpi:IRIX/6.5.30/disc1/stand/sash64<br>
&ensp;Check the directories of your IRIX version to find the right installer program.<br>
<br>
<h3>5. Formatting root partition using Inst installer program</h3>
Select option "13. admin" --> "11. mkfs" --> (y)es --> yes --> "21. return" (numbers can change depending on the Inst version)<br>
When formatting a partition, follow spinlocksolutions's advice:<br>
"If working with a new disk, the installer will ask to format partitions and the block size to use. Use 4096kB block size for disks larger than 4GB, 512B otherwise."<br>
<br>
<h3>6. Installing IRIX</h3>
Load the selections file according to the IRIX version installed. Check the right file on Reanimator's main menu, for example:<br>
Use "rbpi" or "debian" according to the installation platform<br>
6.5.22: Select option "13. admin" --> "15. load filename" --> irix@rbpi:i/6.5.22.txt --> "21. return"<br>
6.5.30: Select option "13. admin" --> "15. load filename" --> irix@rbpi:i/6.5.30.txt --> "21. return"<br>
6.5.7: Select option "13. admin" --> "15. load filename" --> irix@rbpi:i/6.5.7.txt --> "21. return"<br>
2024/05/24 update: It seems that NFS is not installed. After installation, reboot and install the source irix@IP_Reanimator:i/IRIX/irix65x/nfs/dist, for example:<br>
Reference: https://forums.sgi.sh/index.php?threads/nfs-weirdness.563/<br>

```
# inst
1. from [source ...]
Install software from: irix@192.168.9.100:i/IRIX/irix65x/nfs/dist
Inst> conflicts

nfs.sw.nis (1274627335) is incompatible with eoe.sw.base (1289434520)
  1a. Do not install nfs.sw.nis (1274627335)
  1b. Open new distribution to resolve conflict

nfs.sw.nfs (1274627335) is incompatible with eoe.sw.base (1289434520)
  2a. Do not install nfs.sw.nfs (1274627335)
  2b. Open new distribution to resolve conflict
...
Inst> conflicts 1b
Install software from: irix@192.168.9.100:i/IRIX/6.5.22/ovl1/dist

Install software from: done

Inst> go
```
<br>
If there is no selections file for your IRIX version, you must write the sources manually: select option "1. from [source]" and add the right sources, you can type "rbpi" or "debian" for server name, <b>SKIP</b> "/" before "i". For example:<br>
<br>
Indy: use "rbpi" or "debian" according to the installation platform<br>
irix@rbpi:i/IRIX/6.5.22/ovl1/dist<br>
irix@rbpi:i/IRIX/6.5.22/ovl2/dist<br>
irix@rbpi:i/IRIX/6.5.22/ovl3/dist<br>
irix@rbpi:i/IRIX/6.5.22/apps/dist<br>
irix@rbpi:i/IRIX/irix65x/f1/dist<br>
irix@rbpi:i/IRIX/irix65x/f2/dist<br>
irix@rbpi:i/IRIX/irix65x/nfs/dist<br>
(optional) irix@rbpi:i/IRIX/irix65x/devl/dist<br>
(optional) irix@rbpi:i/IRIX/irix65x/devf13/dist<br>
<br>
Octane2: use "rbpi" or "debian" according to the installation platform<br>
irix@rbpi:i/IRIX/6.5.30/disc1/dist<br>
irix@rbpi:i/IRIX/6.5.30/disc2/dist<br>
irix@rbpi:i/IRIX/6.5.30/disc3/dist<br>
irix@rbpi:i/IRIX/6.5.30/apps/dist<br>
irix@rbpi:i/IRIX/6.5.30/capps/dist<br>
irix@rbpi:i/IRIX/irix65x/f1/dist<br>
irix@rbpi:i/IRIX/irix65x/f2/dist<br>
irix@rbpi:i/IRIX/irix65x/nfs/dist<br>
(optional) irix@rbpi:i/IRIX/irix65x/devl/dist<br>
(optional) irix@rbpi:i/IRIX/irix65x/devf13/dist<br>
<br>
For IRIX 6.5.7: use "rbpi" or "debian" according to the installation platform<br>
irix@rbpi:i/IRIX/irix657/1/dist<br>
irix@rbpi:i/IRIX/irix657/2/dist<br>
irix@rbpi:i/IRIX/irix657/apps/dist<br>
(optional) irix@rbpi:i/IRIX/irix65x/devf/dist<br>
(optional) irix@rbpi:i/IRIX/irix65x/devl/dist<br>
irix@rbpi:i/IRIX/irix65x/f1/dist<br>
irix@rbpi:i/IRIX/irix65x/f2/dist<br>
irix@rbpi:i/IRIX/irix65x/nfs/dist<br>
<br>
Depending on the IRIX version and computer model, the installation procedure can be slightly different. Search videos on Youtube or documentation about IRIX installation on your model.<br>
<br>
<h3>7. Tested IRIX versions using Reanimator</h3>
6.5.22 on Indy<br>
6.5.7 on Indy<br>
6.5.30 on Octane2<br>
<br>
 inst> install maintenance<br>
 inst> conflicts<br>
 inst> conflicts 1a 2a ... until no conflicts<br>
 inst> go<br>
----------<br>
<br>
6.5.0 on Indy<br>
In this case, selections file <b>won't work</b>, so you must write the sources manually: select option "1. from [source]" and add the right sources, you can type "rbpi" or "debian" for server name, <b>SKIP</b> "/" before "i". For example:<br>
<br>
Use "rbpi" or "debian" according to the installation platform. These are the sources:<br>
irix@rbpi:i/IRIX/irix650/1/dist<br>
irix@rbpi:i/IRIX/irix650/apps/dist<br>
(optional) irix@rbpi:i/IRIX/irix65x/devf/dist<br>
(optional) irix@rbpi:i/IRIX/irix65x/devl/dist<br>
irix@rbpi:i/IRIX/irix65x/f1/dist<br>
irix@rbpi:i/IRIX/irix65x/f2/dist<br>
irix@rbpi:i/IRIX/irix65x/nfs/dist<br>
<br>
You will be asked for:<br>
Do you whish to run the optional installation startup script? --> select option 1<br>
Do you want to check for kernel crash files ... ? --> answer yes<br>
<br>
For this version, "install maintenance" <b>won't work</b>, so use the commands specified on <a href=http://www.sgidepot.co.uk/6.5inst.html target="_blank">http://www.sgidepot.co.uk/6.5inst.html</a>:<br>
inst> keep *<br>
inst> install standard<br>
inst> install prereqs<br>
inst> conflicts 1a 2a ... until no conflicts<br>
inst> go<br>
----------<br>
<br>
6.3 (for O2 R5k/R10k) on O2 R5k (tested by kikems). This procedure is similar to IRIX 6.5.0 installation<br>
- select option "1. from [source]" and add the right sources, you can type "rbpi" or "debian" for server name, <b>SKIP</b> "/" before "i". For example:<br>
<br>
Use "rbpi" or "debian" according to the installation platform. These are the sources:<br>
irix@rbpi:i/IRIX/irix63/1/dist<br>
irix@rbpi:i/IRIX/irix63/apps/dist<br>
(optional) irix@rbpi:i/IRIX/irix63/devlib/dist<br>
(optional) irix@rbpi:i/IRIX/irix63/devf/dist<br>
irix@rbpi:i/IRIX/irix63/nfs/dist<br>
<br>
The required disk space is ~500 MB and ~890 MB if your include the development sources.<br>
<br>
After the installation process:<br>
- select option "12. quit"<br>
- reboot the system<br>
- configure the network with IP address 192.168.9.1 using System --> System Manager --> Network Setup on Toolchest<br>
- add "rbpi 192.168.9.100" to /etc/hosts (I used vi)<br>
- check the rest of directories on /home/irix/i/IRIX/irix63 for patches and additional software:<br>
/home/irix/i/IRIX/irix63/patches/dist<br>
You can install this patch running inst or swmgr as root and the source irix@rbpi:i/IRIX/irix63/patches/dist<br>
----------<br>
<br>
5.3 on Indy<br>
WARNING: there are several IRIX versions depending on the sgi model, if this version doesn't work, please check other versions on <a href=http://ftp.irixnet.org/sgi-irix/irix-5.3/ target="_blank">http://ftp.irixnet.org/sgi-irix/irix-5.3/</a> or <a href=http://jrra.zone/sgi/#pg-7 target="_blank">http://jrra.zone/sgi/#pg-7</a><br>
- for every source in /home/irix/i/5.3.txt: select option "1. from [source]", add the source and run "go". These are the sources:<br>
irix@rbpi:i/IRIX/irix53/1/dist<br>
irix@rbpi:i/IRIX/irix53/dev53/dist<br>
irix@rbpi:i/IRIX/irix53/gzip/dist<br>
irix@rbpi:i/IRIX/irix53/nfs/dist<br>
<br>
After the installation process:<br>
- select option "12. quit"<br>
- reboot the system<br>
- configure the network with IP address 192.168.9.1 using System --> System Manager --> Network Setup on Toolchest<br>
- add "rbpi 192.168.9.100" to /etc/hosts (I used vi)<br>
- check the rest of directories on /home/irix/i/IRIX/irix53 for patches and additional software:<br>
/home/irix/i/IRIX/irix53/patches/dist<br>
/home/irix/i/IRIX/irix53/y2k<br>
----------<br>
<br>
6.2 on Indy. This procedure is similar to IRIX 5.3 installation<br>
- for every source in /home/irix/i/6.2.txt: select option "1. from [source]", add the source and run "go". These are the sources:<br>
irix@rbpi:i/IRIX/irix62/1/dist<br>
irix@rbpi:i/IRIX/irix62/2/dist<br>
irix@rbpi:i/IRIX/irix62/apps/dist<br>
irix@rbpi:i/IRIX/irix62/nfs62/dist<br>
(optional) irix@rbpi:i/IRIX/irix62/devf<br>
(optional) irix@rbpi:i/IRIX/irix62/devlibs<br>
<br>
After the installation process:<br>
- select option "12. quit"<br>
- reboot the system<br>
- configure the network with IP address 192.168.9.1 using System --> System Manager --> Network Setup on Toolchest<br>
- add "rbpi 192.168.9.100" to /etc/hosts (I used vi)<br>
- check the rest of directories on /home/irix/i/IRIX/irix62 for patches and additional software:<br>
/home/irix/i/IRIX/irix62/patches/dist<br>
/home/irix/i/IRIX/irix62/y2k_patch<br>
<br>
<h3>8. External references</h3>
----------<br>
6.5.30 Octane <a href=https://wiki.preterhuman.net/IRIX_6.5.x_Install_on_Octane target="_blank">https://wiki.preterhuman.net/IRIX_6.5.x_Install_on_Octane</a><br>
 inst> keep *<br>
 inst> install standard<br>
 inst> go<br>
----------<br>
6.5.30 Octane2 <a href=https://www.youtube.com/watch?v=5u6yylUXcIo target="_blank">https://www.youtube.com/watch?v=5u6yylUXcIo</a><br>
6.5.30 <a href=https://github.com/unxmaal/booterizer/tree/pi_support target="_blank">https://github.com/unxmaal/booterizer/tree/pi_support</a><br>
keep *<br>
install standard<br>
keep incompleteoverlays<br>
remove java_dev*<br>
remove java2_plugin*<br>
----------<br>
6.5.30<br>
<a href=http://techpubs.spinlocksolutions.com/irix/remote-irix-6.5-installation-from-linux.html#install-2 target="_blank">http://techpubs.spinlocksolutions.com/irix/remote-irix-6.5-installation-from-linux.html#install-2</a><br>
After you have loaded all the distributions, run the following:<br>
keep *<br>
install standard<br>
install prereqs<br>
rem java_dev.*<br>
(It is OK if "install prereqs" reports that no prereqs were found.)<br>
At this point, you should run conflicts to check if there are any important unresolved dependencies.<br>
If everything went as planned, there should be only one, for java2_plugin.sw.mozilla_freeware, which you remove from installation by typing conflicts 1a<br>
<br>
The response from the above should finally be "no conflicts", and then you can type go to start the software installations and quit when they are done.<br>
<br>
You can remove conflicts using "conflicts" command or using "remove" command.<br>
----------<br>
<br>

<h3>9. Sample videos</h3>
https://www.youtube.com/watch?v=Y5GE6yKwDuI&list=PL7fOFTpu7rt0pGycf3D7yzQoeMjlup-tz

# Enjoy your IRIX installation!
