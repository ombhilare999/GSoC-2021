---
sort: 2
---

## Blink LEDs


- Example Directory: [blink_leds](https://github.com/BeagleWire/BeagleWire/tree/master/examples/blink_leds)
- The LEDs are blink via simple counter logic

### Flash the FPGA with blink_leds bitstream 
```
cd examples/blink_leds

# If the fpga tools present on BBB
make

# Else scp the .bin file in Beaglewire/examples/blink_leds
# In host computer go to Beaglewire/examples/blink_leds
# make
# Command to send it to FPGA: 
# scp blink.bin debian@192.168.6.2:/home/debian/Beaglewire/examples/blink_leds

# Loading SPI flash after FPGA reset, it will be boot up on SPI.
make load_spi

# Reset the FPGA for running bitsream (RST Button on BeagleWire)
```
