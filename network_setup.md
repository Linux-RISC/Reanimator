# Network setup
<img alt="REANIMATOR.jpg" src="REANIMATOR.jpg" align="middle"><br>
<br>
Reanimator includes a "Network assistant menu" in the "Network configuration menu". It allows to choose the network configuration according to your network setup.
<br>
<br>
By default, Reanimator is configured to be connected directly to the client computer or to a network switch. This is the simplest configuration:<br>
<img src="Reanimator stand-alone.png">
<br>
If you download the full version, serveral IRIX versions are included and it's the <b>best</b> solution for beginners.<br>
<br>
But if you use the lite version and you want to download IRIX versions for the Internet, you must connect the RBPi to the Internet. There are two options:<br>
<br>
<h4>1. Wired network</h4>
You must use a switch to connect the RBPi and the client computer to your wired network and modify the IP addresses and gateway (/etc/hosts, /etc/bootptab, /etc/dhcpcd.conf or /etc/network/interfaces using the "Networking menu") according to your network configuration. This is an example for a 192.168.9.0/24 network:<br>
<img src="Reanimator wired.png">
<br>
This is the <b>fastest</b> setup to download IRIX versions from the Internet, but the configuration is <b>complex</b>.<br>
<br>
<h4>2. Wi-Fi network</h4> 
This is probably the most <b>common</b> case. If you use a Wi-Fi network to connect to the Internet, you can isolate the wired RBPi connection from the Wi-Fi network and use the RBPi as a router for your sgi computer. You must configure the Wi-Fi connection on the RBPi to connect to your Wi-Fi using the "Network assistant menu" in the "Network configuration menu":<br>
<img src="Reanimator Wi-Fi.png">
<br>
This is the <b>easiest</b> setup to download IRIX versions from the Internet and connect the sgi computer to the Internet, but the Internet speed is <b>limited</b> by the Wi-Fi connection.<br>
<br>
This setup <b>requires</b> RBPi model 3 or 4 (they include Wi-Fi interface), untested on early models using a Wi-Fi dongle.<br>
