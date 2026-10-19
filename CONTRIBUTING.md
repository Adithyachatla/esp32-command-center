# Contributing to JARVIS Command Center

Thanks for helping! This is a small hobby/portfolio project, so the process is light. By taking part you agree to the
[Code of Conduct](CODE_OF_CONDUCT.md). Read the [README](README.md) first — especially the honest status table.

## Privacy rules (important)

This is a public repository. In code, commits, issues, logs and screenshots **never include**:

- real Wi-Fi names or passwords, dashboard logins, tokens or cookies
- your network details, device MAC addresses or personal file paths such as `C:\Users\<you>\…`
- `include/secrets.h` (it is git-ignored — keep it that way; check `git status` before every push)

Redact serial logs and screenshots. Use placeholders such as `YOUR_WIFI_SSID`.

## Reporting a bug

Open an issue with:

1. What you expected and what happened.
2. Board model, Windows version, PlatformIO version, and `platformio.ini` changes if any.
3. The **redacted** serial log from boot and the exact error text.
4. Steps to reproduce, and whether it happens with the unmodified repository.

Security problems: do **not** open a public issue — see [SECURITY.md](SECURITY.md).

## Suggesting a feature

Open an issue describing the problem it solves and how it fits the existing design (offline, ESP32-hosted, green terminal look,
explicit hardware allow-list). Small, focused ideas are easiest to accept.

## Development setup

Follow [docs/INSTALLATION.md](docs/INSTALLATION.md) to build and flash, and [docs/DEVELOPMENT.md](docs/DEVELOPMENT.md) for the
project structure and how to extend it. You can work on the UI without hardware using `node tools/mock-server.js`.

## Submitting a pull request

1. Fork the repository and create a branch (`feature/short-name` or `fix/short-name`).
2. Keep the change focused; do not mix refactoring with new features.
3. Checklist:
   - [ ] `pio run` builds without new warnings you introduced.
   - [ ] UI changes keep the phosphor-green terminal look and desktop-first layout, and make no external requests.
   - [ ] New hardware goes through `include/config.h` and the safe-pin allow-list.
   - [ ] Slow work (BLE, I2C, reboot) stays out of the web-server task — queue it for `loop()`.
   - [ ] Docs updated; anything you could not test on hardware is **labelled untested** in the PR description and docs.
   - [ ] No secrets, personal paths or real network details anywhere in the diff.
4. Describe what you tested and on which board.

## Style

- C++: match the existing formatting (2-space indent, one namespace per module).
- JS/CSS: no external requests (the access point has no internet); fonts are served from `data/fonts/`.
- Short, descriptive commit messages.

## Credits

Please keep the `BUILT BY ADITECHSMITH` credit and creator link in forks that remain recognisably this project.
