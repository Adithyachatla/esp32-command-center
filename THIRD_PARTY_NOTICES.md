# Third-party notices

This project's own code has **no license selected yet** (see [README](README.md#license)). The components below
are third-party and keep their own licenses. This is a good-faith summary, **not legal advice** — check each upstream
project before redistributing.

## Fonts bundled in `data/fonts/` (SIL Open Font License 1.1)

The four `.woff2` files are byte-identical to the web-optimised (Latin subset) files published in the
[Fontsource](https://fontsource.org/) npm packages. Full license texts are in [`third_party/fonts/`](third_party/fonts/).

| File | Font | Copyright | License text |
|---|---|---|---|
| `pressstart2p.woff2` | Press Start 2P | 2012 The Press Start 2P Project Authors (cody@zone38.net) | [OFL-PressStart2P.txt](third_party/fonts/OFL-PressStart2P.txt) |
| `silkscreen-bold.woff2` | Silkscreen Bold | 2001 The Silkscreen Project Authors | [OFL-Silkscreen.txt](third_party/fonts/OFL-Silkscreen.txt) |
| `jbmono-400.woff2`, `jbmono-700.woff2` | JetBrains Mono | 2020 The JetBrains Mono Project Authors | [OFL-JetBrainsMono.txt](third_party/fonts/OFL-JetBrainsMono.txt) |

The OFL permits bundling and redistribution provided the copyright notice and license text accompany the fonts and the fonts are
not sold on their own. Some of these fonts declare a *Reserved Font Name*; the files here are the unmodified Fontsource builds.

## Fonts used only in `docs/JARVIS_Documentation.pdf` (embedded, not distributed as font files)

| Font | License |
|---|---|
| Caveat | SIL OFL 1.1 |
| Patrick Hand | SIL OFL 1.1 |
| Permanent Marker | Apache License 2.0 |
| Special Elite | Apache License 2.0 |

The notebook-style artwork in the PDF is original to this project!.

## Libraries (downloaded by PlatformIO, **not** included in this repository)

| Library | Source | License (per upstream — please verify) |
|---|---|---|
| AsyncTCP | `esp32async/AsyncTCP` | LGPL-3.0 |
| ESPAsyncWebServer | `esp32async/ESPAsyncWebServer` | LGPL-3.0 |
| Arduino core for ESP32 / ESP-IDF | `espressif32` platform | LGPL-2.1 (Arduino core), Apache-2.0 (ESP-IDF) |

The compiled firmware links these libraries. If you distribute **firmware binaries**, read the LGPL obligations of the libraries
you link. Distributing only this source code does not redistribute the libraries.

## Trademarks

ESP32 and Espressif are trademarks of Espressif Systems. Arduino is a trademark of Arduino AG. PlatformIO, Visual Studio Code,
Chrome, Windows, GitHub and Instagram belong to their respective owners. This project is not affiliated with or endorsed by them.
"JARVIS" is used here as the name of a hobby project; it is not affiliated with Marvel or Disney.
