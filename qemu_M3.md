# Migrating VirtualBox image to qemu. Tested on a M3 Mac for Jamie Honnaker, thank you!
<img alt="REANIMATOR.jpg" src="REANIMATOR.jpg" align="middle"><br>
<br>
<h3>1. Convert the VDI to a raw file:</h3>

```
VBoxManage clonehd Debian_i386-IRIX_install.vdi Debian_i386-IRIX_install-qemu.img --format raw
```
<h3>2. Boot in qemu and use sudo to get a real IP address on your home network:</h3>

```
sudo qemu-system-x86_64 -M q35,vmport=off,hpet=off -m 2G -cpu max -accel tcg,thread=multi,tb-size=1024 -global ICH9-LPC.disable_s3=1 -smp cpus=4 -device virtio-blk-pci,drive=drive1,bootindex=0 -drive if=none,media=disk,id=drive1,file.filename=/Users/jhonnaker/Downloads/Debian_i386-IRIX_install-qemu.img,discard=unmap,detect-zeroes=unmap,format=raw -rtc base=localtime -device virtio-net-pci,netdev=net0 -netdev vmnet-bridged,id=net0,ifname=en0 -device cirrus-vga
```
<h3>3. Edit /etc/network/interfaces to change the interface name to what qemu presents and reboot. You can find out what the correct interface name is by logging in as root and typing:</h3>

```
ifconfig -a
```
You can even change it back to DHCP.<br>

<h3>4. When you update the OS and it updates grub, it will complain about the disk.  Just  choose to let it install grub on the root of the disk, which is the first selection in the list.</h3>

<h3>5. You also have to change /etc/hosts and /etc/bootptab with IPs for IRIX and IRIX2 for IPs on your home network.</h3>
