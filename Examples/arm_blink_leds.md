---
sort: 3
---

## Arm Blink LEDs

- Example Directory: [arm_blink_leds](https://github.com/BeagleWire/BeagleWire/tree/master/examples/arm_blink_leds)
- The LEDs blink via ARM memory.
- GPMC has been used between ARM and FPGA for memory Transfer

### Flash the FPGA with arm_blink bitstream 
```
cd examples/arm_blink_leds

# If the fpga tools present on BBB
make

# Else scp the .bin file in Beaglewire/examples/arm_blink_leds
# In host computer go to Beaglewire/examples/arm_blink_leds
# make
# Command to send it to FPGA: 
# scp arm_blink.bin debian@192.168.6.2:/home/debian/Beaglewire/examples/arm_blink_leds

# Loading SPI flash after FPGA reset, it will be boot up on SPI.
make load_spi

# Reset the FPGA for running bitsream (RST Button on BeagleWire)
```

### Running arm blink script for transferring the memory words from ARM to FPGA (LEDs)

- Before running the arm blink script ensure that bridge libs are compiled.
```
cd Beaglewire/bridge_lib/
make
```
- Once the bridge libs are compiled:
```
cd Beaglewire/examples/arm_blink_leds
chmod +x arm_blink.sh
sudo ./arm_blink.sh
```

### TO DO
- [ ]  Generalize C code with the help of memmap