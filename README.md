# Geniatech GTW360 nRF52840 ZBoss NCP firmware

This repo contains github actions files to build ZBoss firmware for GTW360 only.
It has differences from devboard and probably cannot be used on other nRF52840 boards.
Main differences:
- use nrf UART1 for communication
- DC/DC converter is disabled (doesn't start when it is enabled)

## Hardware depencencies
- ST-Link dongle

## Command to flash over SWD/SWC

Connect board to ST-Link: SWD,SWC,GND.
Run the command:

```sh
openocd -f interface/stlink.cfg -f target/nrf52.cfg -c "init" -c "reset init" -c "halt" -c "nrf5 mass_erase" -c "flash write_image ncp-nrf52840dk_nrf52840-v2.9.0-115200.hex" -c "reset" -c "exit"
```
