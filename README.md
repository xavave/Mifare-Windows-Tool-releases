# Mifare Windows Tool – Releases

[![Latest release](https://img.shields.io/github/v/release/xavave/Mifare-Windows-Tool-releases?label=latest%20release)](https://github.com/xavave/Mifare-Windows-Tool-releases/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/xavave/Mifare-Windows-Tool-releases/total)](https://github.com/xavave/Mifare-Windows-Tool-releases/releases)
![Platform](https://img.shields.io/badge/platform-Windows%2010%2F11%20x64-blue)
[![License: Freeware](https://img.shields.io/badge/license-freeware-green.svg)](LICENSE)

**Mifare Windows Tool (MWT)** is a Windows desktop application for reading, writing, analysing and cloning **MIFARE Classic** cards, built on top of the open-source [libnfc](https://github.com/nfc-tools/libnfc) toolchain and an **ACR122U** (PC/SC) reader.

> This repository only hosts the **public binary releases** of MWT.
> The application source code is developed in a private repository.

---

## Download

Grab the latest build from the **[Releases page](https://github.com/xavave/Mifare-Windows-Tool-releases/releases/latest)**.

Each release provides a ZIP archive containing the application and its bundled NFC command-line tools.

## Installation

1. Download the latest `.zip` from the [Releases page](https://github.com/xavave/Mifare-Windows-Tool-releases/releases/latest).
2. Extract it to a folder of your choice (for example `C:\Program Files (x86)\AVXTEC\MWT`).
3. Plug in your reader and run `MifareWindowsTool.exe`.

## Requirements

- Windows 10 / 11 (64-bit)
- A supported NFC reader:
  - **ACS ACR122U** (PC/SC) – recommended
  - **PN532-based modules** (for example the Elechouse NFC Module V3) connected through a USB-to-serial adapter (UART, e.g. CP2102)
- For the ACR122U: the ACS driver (https://www.acs.com.hk/download-driver-unified/9840/ACS-Unified-MSI-4280.rar) or the standard Windows smart-card driver
- For a PN532 module: the USB-to-serial adapter driver (https://www.silabs.com/documents/public/software/CP210x_Universal_Windows_Driver.zip), and the module set to UART mode
- MIFARE Classic cards (1K / 4K). "Magic" cards (gen1a) are supported for full-card cloning, including UID changes.

## Features

- Read and dump MIFARE Classic cards (keys, sectors, blocks)
- Write dumps back to a card, with control over the **start and end block** of the write
- Recover unknown keys using bundled attacks (`mfoc`, hardnested)
- Static-nonce diagnostic to detect cards with a constant nonce (typical of some clone / magic chips)
- Set or clone the UID on compatible "magic" cards
- Self-contained: the NFC tools are bundled in the `nfctools_pcsc` folder, nothing else to install

> Feature list reflects the current releases; see each release's notes for details.

## Usage

1. Connect the reader and place a card on it.
2. Launch MWT – the reader is detected automatically.
3. Read the card to produce a dump, or load an existing dump and write it to a blank / magic card.

For detailed walkthroughs, see the [Wiki](https://github.com/xavave/Mifare-Windows-Tool-releases/wiki).

## Support the project

MWT is free to use and developed in my spare time. If it saved you some time, you can support its development:

<a href="https://www.paypal.com/donate/?hosted_button_id=V5ZP47AVFHRVY" target="_blank"><img src="https://www.paypalobjects.com/en_US/i/btn/btn_donate_LG.gif" alt="Donate with PayPal" /></a>

## Documentation

Guides, FAQ and troubleshooting tips are available in the **[Wiki](https://github.com/xavave/Mifare-Windows-Tool-releases/wiki)**.

## Bug reports and feature requests

Please use the [Issues](https://github.com/xavave/Mifare-Windows-Tool-releases/issues) tab and include:

- your Windows version and MWT version
- your reader model
- the card type (and whether it is a "magic" card)
- the exact steps to reproduce, plus any error output

## Credits

MWT relies on the work of the open-source NFC community:

- [libnfc](https://github.com/nfc-tools/libnfc) and `nfc-mfclassic`
- [mfoc / mfoc-hardnested](https://github.com/nfc-tools/mfoc-hardnested)
- [libusb](https://libusb.info/)

## Legal notice

MWT is intended for **educational purposes, security research and the backup of cards you own or are authorised to access**. Do not use it to access or copy systems or cards without the owner's permission. You are solely responsible for how you use this software, which is provided **"as is", without warranty of any kind**.

## License

Mifare Windows Tool is **proprietary freeware**: free to use and to redistribute unmodified, but **closed source**. See [LICENSE](LICENSE) for the full terms.

Third-party components bundled with MWT remain under their own licenses. The full license texts are in the [`licenses`](licenses) folder, and the component list with links to the corresponding source code is in [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md). In short:

- libnfc and its tools: <https://github.com/xavave/libnfc_with_extra_tools> (upstream: <https://github.com/nfc-tools/libnfc>)
- mfoc-hardnested (with static-nonce diagnostic): <https://github.com/xavave/mfoc-hardnested-and-static-nonce> (upstream: <https://github.com/nfc-tools/mfoc-hardnested>)
