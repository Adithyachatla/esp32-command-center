# JARVIS — ESP32 Command Center

A retro phosphor-green command center that an ESP32-WROOM-32 serves from its **own Wi-Fi network**.
No internet, router or cloud needed.

`LOGIN → ACCESS GRANTED → ESP32 BOOT ANIMATION → COMMAND CENTER`

**BUILT BY ADITECHSMITH** · [@aditechsmith](https://www.instagram.com/aditechsmith?obrf=MXZlOWpub2k2M3RrbQ==)

![Dashboard](docs/images/04-dashboard.png)

## Features
- Own Wi-Fi access point, login checked in the firmware
- Boot animation using real chip, flash and heap data
- System info, Wi-Fi status, BLE on/off, GPIO control, I2C scan, reboot
- Works fully offline (fonts are served from the board)

## Quick start (Windows + PlatformIO)
```bat
copy include\secrets.example.h include\secrets.h
```
Edit `include/secrets.h` and set your own Wi-Fi name, Wi-Fi password and login. Never commit this file.

```bat
pio run
pio run -t upload
pio run -t uploadfs
```
Join the ESP32's Wi-Fi and open `http://192.168.4.1/`.

## Status
The UI is tested against a mock API. Firmware compile, flash and Wi-Fi are reported working by the author. GPIO, BLE, I2C and reboot are **untested on hardware**.

## Security
Plain HTTP, hobby-grade access control, not for production. Details in [SECURITY.md](SECURITY.md).

## Docs
[Setup](docs/SETUP.md) · [Troubleshooting](docs/TROUBLESHOOTING.md) · [PDF guide](docs/JARVIS_Documentation.pdf)

## License
Not selected yet.
