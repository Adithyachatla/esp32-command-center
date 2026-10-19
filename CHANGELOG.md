# Changelog

All notable changes to this project are documented here. The format follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/); versions are the firmware version in `include/config.h`.

## [Unreleased]

## [1.0.0] — Initial public release

### Added
- ESP32-WROOM-32 firmware (PlatformIO, Arduino, ESPAsyncWebServer + AsyncTCP, LittleFS): Wi-Fi access point, static frontend, JSON API.
- Login with credentials verified in firmware, `HttpOnly`/`SameSite=Strict` session cookie, idle expiry, per-IP lockout.
- Four-screen desktop UI: login → ACCESS GRANTED → ESP32 boot animation → command center, in a phosphor-green terminal style
  with locally served pixel/mono fonts (no external requests).
- Dashboard panels: system info, Wi-Fi status and TX power, BLE advertising on/off, GPIO outputs/inputs for configured pins,
  I2C scanner, two-step reboot, logout.
- Safe-output-pin allow-list; `include/config.h` for pins and limits; `include/secrets.example.h` template.
- Small fixed `BUILT BY ADITECHSMITH` creator credit on every screen.
- Documentation: README, installation/hardware/architecture/features/development/troubleshooting guides, security policy,
  contributing guide, code of conduct, third-party notices, styled PDF edition, `tools/mock-server.js`.

### Known limitations
- Desktop layout only; plain HTTP; credentials compiled into the firmware; no OTA; BLE advertising only; Classic Bluetooth unused.
- UI verified against a simulated API. Firmware compile/flash and the Wi-Fi access point are reported working by the author;
  GPIO, BLE, I2C, TX-power and reboot are **untested on hardware**.
- No license selected yet.
