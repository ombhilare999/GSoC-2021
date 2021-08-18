---
sort: 1
---

# BeagleWire Examples

## File Structure:

```
.
├── arm_blink_leds 
├── bar_graph
├── blink_leds
├── vga
├── vga_pong
├── gpio
├── i2c
├── lcd
├── lcd_game
├── sdram
├── spi
├── stepper_motor
├── uart
├── Makefile
├── Makefile.beaglewire
├── pwm
├── README.md
```

## 1) Arm Bink Leds

- The LEDs are blink via ARM memory.
- GPMC has been used between ARM and FPGA for memory Transfer
- Further the GPMC protocol has been converted to Wishbone protocol
- [Detailed Steps](https://beaglewire.github.io/Examples/arm_blink_leds.html)

## 2) Bink Leds

- The LEDs are blink via simple counter logic
- [Detailed Steps](https://beaglewire.github.io/Examples/blink_leds.html)

## 3) Bar Graph

- This Example is the template for wishbone intercon
- The testcase consist of:
    1. Wishbone Slave 1: PMOD 3 (Bar Graph 0)
    2. Wishbone Slave 2: PMOD 4 (Bar Graph 1)
- Address Map
```
        Wishbone Memmap
        Slave 0:  0x0000
        Slave 1:  0x0040
```
- Wishbone intercon automatically routes signals and data to the appropriate slave depending on the memmap
- [Detailed Steps](https://beaglewire.github.io/Examples/bar_graph.html)

## 4) VGA

- In this example, I have displayed wishbone VGA Patterns on a monitor.
- For this Example we have used following PMOD: [Digilent-VGA-PMOD](https://www.tanotis.com/products/digilent-410-345-evaluation-board-pmod-trade-vga-video-graphics-array-12-bit-rgb444-colour-depth?gclid=CjwKCAjw092IBhAwEiwAxR1lRn8s2O1nUpSEIg9vGi8F0Ejb-Zt24NGQHJ1PMexA8tO4YbSnNggPlRoCW9sQAvD_BwE)
- VGA PMOD is connected to the beaglewire P3, P4 Pmods.
- pinmap can be found in pcf file.
- It is connected upside down to port3 and port4.
- [Detailed Steps](https://beaglewire.github.io/Examples/vga.html)
- VGA Pattern Table: 

| {SW3, USR1, USR 0} | Pattern on VGA |
| ----------- | ----------- |
|     000     | Disable       |
|     001     | All Red       |
|     010     | All GREEN       |
|     011     | All Blue        |
|     100     | Checkboard White/Black       |
|     101     | Color Bars       |

- Demo Video of VGA can be found here: [Imgur](https://imgur.com/sAeCMZ2)

## 5) Pong on the FPGA:

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



- Demo Video of VGA can be found here: [Imgur](https://imgur.com/V1f6uFf)