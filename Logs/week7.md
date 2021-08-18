---
sort: 8
---

# Week 7 (25 July - 1 Aug)

- Closed Following Issues:
    - [#10](https://github.com/pmezydlo/BeagleWire/issues/10)
    - [#7](https://github.com/pmezydlo/BeagleWire/issues/7)
    - [#8](https://github.com/pmezydlo/BeagleWire/issues/8#issue-339423429)

- Added Helper scripts for dtc, spi flash.
- Explored way to tristate SPI pins without adding overlay for it.
- Adding Litex with gpmc to wishbone wrapper.

On-going blockers:
-  In beaglewire we had three dtc files as of now:
1. overlay with spi enabled.
2. overlay with spi tristated (0x37) (we wanted to tristate spi so that it doesn't interfer with fpga)
3. overlay with ice40 on spi.
- I wanted to change the pin mode of the pins in run time to avoid changing overlay and reboot process.
- config-pin utility requires the enable universal overlay which causes lots of pinmux issue with gpmc that we are using in beaglewire. So wanted some other way to change pinmode.