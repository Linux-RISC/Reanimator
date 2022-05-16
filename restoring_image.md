# Restoring Reanimator image
<img alt="REANIMATOR.jpg" src="REANIMATOR.jpg" align="middle"><br>
<br>
<h3>1. Restoring Reanimator to a SD Card or in VirtualBox</h3>
<h4>1.1 Uncompress the .tar.gz file using for example 7-Zip in Windows or "tar xzvf file.tar.gz" in GNU/Linux</h4>
<h4>1.2 Restoring to a SD Card (16 GB or more) for Raspberry Pi</h4>
Restore the .img file extracted, you can use these tools:<br>
Windows: <a href=https://www.raspberrypi.org/downloads/ target="_blank">Raspberry Pi Imager</a><br>
GNU/Linux:<br>
- open a terminal<br>
- check your SD device, for example /dev/mmcblk0<br>
- sudo dd if=reanimator-Pi-server-SD8GB-no-images.img of=/dev/mmcblk0 bs=4M<br>

<h4>1.3 Restoring to VirtualBox</h4>
- File -> Virtual media manager -> Add .vdi file extracted<br>
Create a new VirtualBox virtual machine:<br>
- Machine -> New. Name "Debian i386-Reanimator", type "Linux" and version "Debian (32-bit)"<br>
- Memory size: 512 MB<br>
- Use existing virtual hard disk file -> select .vdi file extracted<br>
- When the virtual machine has been created, select "Configuration", "Network" and select "Connected to:" -> "Bridge adapter". Select the specific adapter name of your computer.<br>
