---
sort: 7
---

# encoder

- Encoder has two inbuilt 90 degree phase out switches, using which we could tell the direction of encoder motion.
- Using a state diagram we are detecting the direction.
- All the steps and information can be found here: [Detailed Steps](https://beaglewire.github.io/Examples/encoder.html)
- Information about State Diagram and 90 degree phase out switches are as follows:

<p align="center">
    <img width="379" height="585" src="https://imgur.com/xKxCOUf.png">
</p>


<p align="center">
    <img width="360" height="175" src="https://imgur.com/DYWIKIz.png">
</p>


### Flash the FPGA with encoder example bitstream 

```
cd Beaglewire/examples/encoder

# If the fpga tools present on BBB
make

# Else scp the .bin file in Beaglewire/examples/encoder
# In host computer go to Beaglewire/examples/encoder
# make
# Command to send it to FPGA: 
# scp vga.bin debian@192.168.6.2:/home/debian/Beaglewire/examples/encoder

# Loading SPI flash after FPGA reset, it will be boot up on SPI.
make load_spi

# Reset the FPGA for running bitsream (RST Button on BeagleWire)
```

