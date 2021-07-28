## Week 5 (5 July - 16 July)

- Made changes in the gpmc to wishbone wrapper and arm blink wishbone example after mentor's review.
- Detailed Changes in PR thread: https://github.com/BeagleWire/BeagleWire/pull/3
- Closed the issue [#12](https://github.com/pmezydlo/BeagleWire/issues/12)
- Did Random memory read tests in the gpmc to wishbone wrapper
- Working on the Wishbone intercon with this [reference](https://github.com/boschmitt/wishbone/blob/master/RTL/WISHBONE/INTERCON/SHARED/wbi_shrd_08.vhd)
- Prepared two PMODs each having a bar graph LED. In wishbone intercon test each pmod will act as wishbone slave.
> [Bar Graph with Beaglewire video demo](https://imgur.com/PmR1hZg)
- Created platform for beaglewire in litex boards.
> [beaglewire.py](https://github.com/BeagleWire/litex-boards/blob/master/litex_boards/platforms/beaglewire.py)
- **Beaglewire yaml file for litedram:** https://github.com/BeagleWire/litedram/blob/master/examples/beaglewire.yml
- **Produced SDRAM IP:**
https://github.com/BeagleWire/litedram/blob/master/build/gateware/litedram_core.v
