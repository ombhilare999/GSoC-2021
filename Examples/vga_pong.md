---
sort: 6
---

## VGA_pong

- For this Example also we have used following PMOD: [Digilent-VGA-PMOD](https://www.tanotis.com/products/digilent-410-345-evaluation-board-pmod-trade-vga-video-graphics-array-12-bit-rgb444-colour-depth?gclid=CjwKCAjw092IBhAwEiwAxR1lRn8s2O1nUpSEIg9vGi8F0Ejb-Zt24NGQHJ1PMexA8tO4YbSnNggPlRoCW9sQAvD_BwE)
- VGA PMOD is connected to the beaglewire P3, P4 Pmods.
- pinmap can be found in pcf file.
- It is connected upside down to port3 and port4.
- [Detailed Steps](https://beaglewire.github.io/Examples/vga_pong.html)
- Switches Information: 

| Switch | Description |
| ----------- | ----------- |
|     Start Button    | USR0       |
|     Player1_Paddle_UP     | PMOD1_0       |
|     Player1_Paddle_Down     | PMOD1_1       |
|     Player2_Paddle_UP     | PMOD1_2     |
|     Player2_Paddle_Down    | PMOD1_3       |


### Flash the FPGA with VGA example bitstream 

```
cd Beaglewire/examples/vga_pong

# If the fpga tools present on BBB
make

# Else scp the .bin file in Beaglewire/examples/vga_pong
# In host computer go to Beaglewire/examples/vga_pong
# make
# Command to send it to FPGA: 
# scp vga.bin debian@192.168.6.2:/home/debian/Beaglewire/examples/vga_pong

# Loading SPI flash after FPGA reset, it will be boot up on SPI.
make load_spi

# Reset the FPGA for running bitsream (RST Button on BeagleWire)
```

## Demo:

<p align="center">
<video  width="520" height="320" controls>
  <source src="https://user-images.githubusercontent.com/40693854/129450815-3e51923c-16e7-4065-a337-7529dd66d2c2.mp4" type="video/mp4">
</video>
</p>

