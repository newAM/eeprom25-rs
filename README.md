# Rust 25x EEPROM Driver

[![Build Status](https://travis-ci.com/newAM/eeprom25x-rs.svg?branch=master)](https://travis-ci.com/newAM/eeprom25x-rs)

Inspired by [eeprom24x-rs](https://github.com/eldruin/eeprom24x-rs),
this is a driver for the 25x series SPI EEPROM,
based on the [`embedded-hal`](https://github.com/rust-embedded/embedded-hal) traits.

**Note:** This crate is still under active development!

## Supported Devices
At the moment this only supports the [25AA02E48](http://ww1.microchip.com/downloads/en/DeviceDoc/25AA02E48-25AA02E64-2K-SPI-Bus-Serial-EEPROM-Data%20Sheet_DS20002123G.pdf) EEPROM.

## FTDI Example

### Building
Instructions are provided for a Debian based OS.

1. Run `sudo apt install libclang-dev libftdi1-dev`.
2. Create a file `/etc/udev/rules.d/99-libftdi.rules`
3. Put the following test into the file:
```
SUBSYSTEMS=="usb", ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6001", GROUP="dialout", MODE="0660"
SUBSYSTEMS=="usb", ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6014", GROUP="dialout", MODE="0660"
```
4. Reload udev `sudo udevadm control --reload-rules && sudo udevadm trigger`.
5. Build the binary `cargo build --example ftdi`.

### Running
Get a FT232H breakout board.  I used the [adafruit FT232H breakout](https://www.adafruit.com/product/2264).

* Connect SCK to D0
* Connect MOSI to D1
* Connect MISO to D2
* Connect CS to C0
* Connect Vdd to 3.3V or 5V
* Connect Vss to GND

Run the example `target/debug/examples/ftdi`.
