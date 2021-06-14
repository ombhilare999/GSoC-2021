# Getting BBB Ready for BeagleWire

## 1) Flashing BeagleWire With New Image

- First of all download this image for beagleboard site: [AM3358 Debian 10.3 2020-04-06 4GB SD IoT](https://debian.beagleboard.org/images/bone-debian-10.3-iot-armhf-2020-04-06-4gb.img.xz)
- Find the micro-SD Card device (for example, mine is sdd). Type the following:
    > mount
- Decompress the .xz file
    > xz -d BBB*.xz
- This gives you the image file: BBB*.img. Write the image to the memory card 
    > sudo dd if=./BBB*.img of=/dev/sdX

### Flashing eMMC:
- To set up the standalone microSD image to automatically flash the eMMC on powerup. Login as debian (password = temppwd) and edit /boot/uEnv.txt with nano (sudo nano /boot/uEnv.txt) or your preferred editor.
- In /boot/uEnv.txt:
```
##enable BBB: eMMC Flasher:
#cmdline=init=/opt/scripts/tools/eMMC/init-eMMC-flasher-v3.sh
```
- Change to:
```
##enable BBB: eMMC Flasher:
cmdline=init=/opt/scripts/tools/eMMC/init-eMMC-flasher-v3.s
```
- Optional, update Flasher Scripts:
```
cd /opt/scripts/
git pull
```
- reboot  **(make sure to remove the microSD after flashing is complete, otherwise it'll just keep on re-flashing the eMMC)**
```
sudo reboot
```
- **Confirm you have flashed the BBB with new image**
```
debian@beaglebone:~$ uname -a
Linux beaglebone 4.19.94-ti-r64 #1buster SMP PREEMPT Fri May 21 23:57:28 UTC 2021 armv7l GNU/Linux
```
- For details steps once can follow below tutorials:
    1. [Derekmolly's tutorial](http://derekmolloy.ie/write-a-new-image-to-the-beaglebone-black/)
    2. [Adafruit tutorial](https://learn.adafruit.com/beaglebone-black-installing-operating-systems/flashing-the-beaglebone-black)

---
---

## 2) Upgrade the software on your Beagle

### Connect BeagleBoard to the internet
- For detailed steps you can follow this: [Get connected to the Internet](https://beagleboard.org/upgrade#:~:text=There%20are%204%20main%20steps,up%20scripts%20and%20Linux%20kernel&text=Update%20examples%20in%20the%20Cloud9%20IDE%20workspace)

### Update the boot-up scripts and Linux kernel
```
cd /opt/scripts
git pull
sudo tools/update_kernel.sh
sudo shutdown -r now
```
### Update distribution components
```
cd /opt/scripts
sudo apt update
sudo apt upgrade
```
### Addition References: [Upgrade the software on your Beagle](https://beagleboard.org/upgrade#:~:text=There%20are%204%20main%20steps,up%20scripts%20and%20Linux%20kernel&text=Update%20examples%20in%20the%20Cloud9%20IDE%20workspace)

---
---

## 3) Installing Linux Headers
```
sudo apt update
sudo apt install linux-headers-$(uname -r)
```
---
---
## 4) Getting BeagleWire Software:
```
git clone https://github.com/BeagleWire/BeagleWire 
```
---
---
## 5) Device Tree Overlay:
- Device Tree is required for enabling SPI and GPMC.
- Install the DTS compiler:
```
wget -c https://raw.githubusercontent.com/RobertCNelson/tools/master/pkgs/dtc.sh
chmod +x dtc.sh
./dtc.sh
```
- Compile the dts file:
```
dtc -O dtb -o DTS/BW-ICE40Cape-00A0.dtbo -b 0 -@ DTS/BW-ICE40Cape-00A0.dts
```
- Copy dtbo file to /lib/firmware on the BBB:
```
cp DTS/BW-ICE40Cape-00A0.dtbo /lib/firmware
```
- Adding device tree Overlay in boot files
```
sudo vim /boot/uEnv.txt
```
- Find the following part:
```
###Additional custom capes
#uboot_overlay_addr4=/lib/firmware/<file4>.dtbo
```
- Instead add this:
```
###Additional custom capes
uboot_overlay_addr4=/lib/firmware/BW-ICE40Cape-00A0.dtbo
```
- Reboot: `sudo reboot`

---
---
## 6) LED Blinking:
- Building Custom LKM module
    ```
    cd BeagleWire/load_fw/
    make    #This Make the LKM module for loading beaglewire with bitstream
    sudo modprobe ice40-spi
    ./bw-prog.sh blink.bin
    ```
- To check how programming is proceeding, use:
    ```
    dmesg
    ```
- Results Should Like this:
    ```
    [ 2427.827170] Starting FPGA loader 
    [ 2427.830561] fpga_manager fpga0: writing blink.bin to Lattice iCE40 FPGA Manager
    [ 2428.012162] Stopping FPGA loader     
    ```