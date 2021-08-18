---
sort: 2
---

                                  __   _ __      _  __    ___                   __
                                 / /  (_) /____ | |/_/___/ _ )___  ___ ________/ /__
                                / /__/ / __/ -_)>  </___/ _  / _ \/ _ `/ __/ _  (_-<
                               /____/_/\__/\__/_/|_|   /____/\___/\_,_/_/  \_,_/___/

                                              LiteX boards files

                                     Copyright 2012-2020 / LiteX-Hub community

# BeagleWire UART Crossover Wishbone Example:

- The BeagleWire is an FPGA development platform that has been designed for use with BeagleBone boards. BeagleWire is a cape on which there is an FPGA device - Lattice iCE40HX.
- BeagleWire has **32 MB SDRAM**, in this example we have used litex core with LiteDRAM + uart crossover bridge over wishbone.


# Crossover UART:

- For crossover UART we use wishbone tool:
- wishbone-tool is useful for interacting with the internal Wishbone bridge on a device.
- Some of the things you can use wishbone-tool for:

```
    Peeking and poking memory, similar to using devmem2
    Testing memory and bridge link quality
    Exposing a Wishbone bridge to Ethernet
    Attaching a GDB server to a softcore
```

- If your bridge is over a UART, then that means your UART is already in use, and isn’t available for use as a console. Or if you’re connecting via some other medium and you only have a single cable connecting the two devices. 
- LiteX supports creating a “crossover” UART that wishbone-tool can interact with and present a local terminal on.

# Install the Litex Toolchains:


1. Install Python 3.6+ and FPGA vendor's development tools and/or [Verilator](http://www.veripool.org/).
2. Install Migen/LiteX and the LiteX's cores:

```sh
$ wget https://raw.githubusercontent.com/enjoy-digital/litex/master/litex_setup.py
$ chmod +x litex_setup.py
$ ./litex_setup.py init install --user (--user to install to user directory)
```
  Later, if you need to update all repositories:
```sh
$ ./litex_setup.py update
```
# On Host Computer:

```
$ git clone https://github.com/BeagleWire/litex-boards
$ git checkout uart_crossover_litex
```

- This repo is not currently upstream with litex repo, so as of now we need to manually copy platform file of beaglewire which is under platform directory to the platform folder of litex 
- Copy this file [platforms/beaglewire.py](https://github.com/BeagleWire/litex-boards/blob/uart_crossover_litex/litex_boards/platforms/beaglewire.py) to the `litex/platform` folder.

# Generate the Litex Core and send bitsream to the BBB:

```
# This will produce a litex core with serv, SDRAM Core and uart crossover bridge.

$ ./litex_boards/targets/beaglewire.py --build --cpu-type=serv
$ cd build/gateware
$ cp beaglewire.bin beaglewire_bios.bin  &&  truncate beaglewire_bios.bin -s 4194304   && dd if=../software/bios/bios.bin of=beaglewire_bios.bin bs=1 seek=393216 conv=notrunc
$ scp beaglewire_bios.bin debian@192.168.6.2:/home/debian
$ scp ../csr.csv debian@192.168.6.2:/home/debian
```
# On BeagleBone Black:

- **Connect the UART 4 Terminal to the BeagleWire PMOD 1**
```
 P9_11 --> pmod1_0
 P9_13 --> pmod1_1
```
- Download the wishbone tool on beaglebone black: 
```
$ wget https://github.com/litex-hub/wishbone-utils/releases/download/v0.7.8/wishbone-tool-v0.7.8-armv7-unknown-linux-gnueabihf.tar.gz
```
- Connection Image:

    <p align="center">
        <img width="420" height="380" src="https://imgur.com/a6DR9tH.png">
    </p>

```
$ sudo su
$ source .bashrc 
$ config-pin P9_11 uart
$ config-pin P9_13 uart
$ sudo chmod 777 /dev/ttyO4
$ bw-spi.sh beaglewire_bios.bin
```

# Wishbone tool for terminal

```
$ ./wishbone-tool -u /dev/ttyO4 -s terminal --csr-csv csr.csv 
```
# Wishbone tool read and write

```
$ ./wishbone-tool -u /dev/ttyO4 0x40000000 0x55555555
$ ./wishbone-tool -u /dev/ttyO4 0x40000000 
```
# Demo:

- Demo of Litex core with serv + litedram + crossover bridge: [video](https://www.youtube.com/watch?v=mx4KWYq29I0)