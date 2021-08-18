---
sort: 5
---

# Week 4 (28 June - 5 July)

- Created a wiki on BeagleWire Repo: [wiki](https://github.com/BeagleWire/BeagleWire/wiki)
- Added Docs for individual examples: [Docs](https://beaglewire.github.io/Examples/)
- Made changes in the gpmc to wishbone wrapper
- Wrote testbench for the gpmc to wishbone wrapper, also tested both write and read conditions.
- Waveforms of the simulation read and write tests:


<p align="center">
    <img src="https://raw.githubusercontent.com/BeagleWire/BeagleWire/master/assets/gpmc_to_wishbone.png">
</p>

- Tested GPMC to Wishbone Wrapper in the Hardware with arm blinks example.
- Createad Led Controller with wishbone bus for arm blink
> Verilog Code: [led_wb.v](https://github.com/BeagleWire/BeagleWire/blob/testing/examples/arm_blink_leds/leds_wb.v)s