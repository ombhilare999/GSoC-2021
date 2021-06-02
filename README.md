---
sort: 1
---

## GSoC 2021

### Introduction

- The BeagleWire is an FPGA development platform that has been designed for use with BeagleBone boards. BeagleWire is a cape on which there is an FPGA device (Lattice iCE40HX). The software support for BeagleWire is still in the development phase.
- In this project, I'm developing and testing the existing software support of Beaglewire. The known primary issue in Beaglewire is the interface between 32MB SDRAM and ICE40HX4K. For this Solution, I'm going to try options like LiteDRAM(a small footprint and configurable DRAM core).

#### Testing and Improvement of Subsystem Like I2C, SPI, PWM, UART

- In this project I'm going to test all the subsystems like I2C, SPI, PWM, UART in Hardware and the primary goal will be to debug the issues related to them and fix them accordingly. Along with the driver code ready to use solutions will be added in software support.

#### Others

- There are current Issues open on BeagleWire Repository, These will be solved during this project.
- More PMODs will be interfaced with the BeagleWire.
- Increase the Documentation and also add getting started guide for BeagleWire.

---

[ [18-05-2021] Community Bonding Period Logs](Logs/week_0.1.md)

---

[Blogs: Getting Started BeagleWire](Blogs/Linux_Kernel_for_FPGA.md)

{% include list.liquid all=true %}
