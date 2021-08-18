---
sort: 5
---

## VGA


- In this example, I have displayed wishbone VGA Patterns on a monitor.
- For this Example we have used following PMOD: [Digilent-VGA-PMOD](https://www.tanotis.com/products/digilent-410-345-evaluation-board-pmod-trade-vga-video-graphics-array-12-bit-rgb444-colour-depth?gclid=CjwKCAjw092IBhAwEiwAxR1lRn8s2O1nUpSEIg9vGi8F0Ejb-Zt24NGQHJ1PMexA8tO4YbSnNggPlRoCW9sQAvD_BwE)
- VGA PMOD is connected to the beaglewire P3, P4 Pmods.
- pinmap can be found in pcf file.
- It is connected upside down to port3 and port4.
- [Detailed Steps](https://beaglewire.github.io/Examples/bar_graph.html)
- VGA Pattern Table: 

| {SW3, USR1, USR 0} | Pattern on VGA |
| ----------- | ----------- |
|     000     | Disable       |
|     001     | All Red       |
|     010     | All GREEN       |
|     011     | All Blue        |
|     100     | Checkboard White/Black       |
|     101     | Color Bars       |

### Flash the FPGA with VGA example bitstream 

```
cd Beaglewire/examples/vga

# If the fpga tools present on BBB
make

# Else scp the .bin file in Beaglewire/examples/vga
# In host computer go to Beaglewire/examples/vga
# make
# Command to send it to FPGA: 
# scp vga.bin debian@192.168.6.2:/home/debian/Beaglewire/examples/vga

# Loading SPI flash after FPGA reset, it will be boot up on SPI.
make load_spi

# Reset the FPGA for running bitsream (RST Button on BeagleWire)
```

### Demo:

- Demo Video of VGA can be found here: [Imgur](https://imgur.com/sAeCMZ2)