# Arduino-u-blox-NINA-B1

u-blox NINA-B3 Arduino example + SHT31 temperature and humidity + Bluetooth BLE ~~Long Range with coded PHY S=8~~

[![GitHub version](https://img.shields.io/github/release/ldab/Arduino-u-blox-NINA-B3.svg)](https://github.com/ldab/Arduino-u-blox-NINA-B3/releases/latest)
[![Build Status](https://travis-ci.org/ldab/Arduino-u-blox-NINA-B3.svg?branch=master)](https://travis-ci.org/ldab/Arduino-u-blox-NINA-B3)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://github.com/ldab/Arduino-u-blox-NINA-B3/blob/master/LICENSE)

[![GitHub last commit](https://img.shields.io/github/last-commit/ldab/Arduino-u-blox-NINA-B3.svg?style=social)](https://github.com/ldab/Arduino-u-blox-NINA-B3)

[![EVK-NINA-B3](https://www.u-blox.com/sites/default/files/styles/product_full/public/products/EVK-NINA-B3-CI_0.png)](https://www.u-blox.com/en/product/evk-nina-b3)

## How to build PlatformIO based project

1. [Install PlatformIO Core](http://docs.platformio.org/page/core.html)
2. Download [development platform with examples](https://github.com/platformio/platform-nordicnrf52/archive/develop.zip)
3. Extract ZIP archive
4. Run these commands:

```
# Change directory to example
> cd platform-nordicnrf52/examples/Arduino-u-blox-NINA-B3

# Build project
> platformio run

# Upload firmware
> platformio run --target upload

# Build specific environment
> platformio run -e nina_B3

# Upload firmware for the specific environment
> platformio run -e nina_B3 --target upload

# Clean build files
> platformio run --target clean
```

## Known limitations

* Some pins mapped on GPIO Port 1 are not yet supported, mainly affects Blue RGB and Serial UART.
https://github.com/arduino-org/arduino-core-nrf52/issues/68

* `attachInterrupt()` locks conflicts with BLE lib.
https://github.com/sandeepmistry/arduino-BLEPeripheral/issues/205

## Why?

This example tries to implement some key functions and key PIN atributes in order to get you started with using Arduino and the NRF52840 BLE board u-blox NINA-B3.

Timer functionas are implemented intead of `delay()` and the PINs have been re-mapped on the `#define` section

## Bluetooth iOS and Android app 

You can download the sample Bluetooth low energy app - BLE App straight from u-blox wesite: [https://www.u-blox.com/en/product/bluetooth-ios-and-android-app](https://www.u-blox.com/en/product/bluetooth-ios-and-android-app)

![App example](./extras/Screenshot_20190328-130832_u-blox%20BLE.jpg)

## fatal error: ble_gatts.h: No such file or directory

The arduino-nRF5x core **REQUIRES** a SoftDevice in order to successfully use this library. Please see [Flashing a SoftDevice](https://github.com/sandeepmistry/arduino-nRF5#selecting-a-softdevice).

On PlatformIO and when using this example you don't need to do anything special as the `build_flags = -DNRF52_S132` has already been included on `platform.ini` file.

SoftDevices contain the BLE stack and housekeeping, and must be downloaded once before a sketch using BLE can be loaded. The SD consumes ~5k of Ram + some extra based on actual BLE configuration.

* SoftDevice S132 v2.0.1 supports nRF52 in peripheral and central role. It is 112k in size.

## Credits

Github Shields and Badges created with [Shields.io](https://github.com/badges/shields/)

Sandeep Mistry's [Arduino BLE library](https://github.com/sandeepmistry/arduino-BLEPeripheral)

Adafruit [SHT31 Library](https://www.adafruit.com/product/2857)
