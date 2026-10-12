# Flashforge Monitor

A lightweight native Linux desktop monitor for Flashforge Creator 5-series printers, built with Python, PySide6 and an external `mpv` executable for the camera.

**Release status:** RC1 candidate. Tested on an Arch Linux/XFCE/X11 system with a Creator 5 Pro. Other desktop environments and printers are not yet verified.

## Features

- Printer status, temperatures, material slots and progress
- Embedded live camera using the separate `mpv` command-line program and an X11 window ID
- Pause, resume and cancel controls
- Printer-specific artwork for Creator 5 and Creator 5 Pro
- File → Open Configuration to switch printer configuration

## Dependencies

- Python 3
- PySide6 (Qt for Python)
- `mpv` executable on `PATH`
- X11 desktop session for camera embedding (`--wid`); Wayland is untested

## Install from source (Linux)

The application is not yet packaged as a distribution-specific package. Install the dependencies through your distribution, then install the files using appropriate permissions:

```sh
sudo install -Dm755 flashforgemonitor /usr/local/bin/flashforgemonitor
sudo install -Dm644 Artwork/creator_5.png /usr/share/flashforgemonitor/Artwork/creator_5.png
sudo install -Dm644 Artwork/creator_5_pro.png /usr/share/flashforgemonitor/Artwork/creator_5_pro.png
sudo install -Dm644 flashforgemonitor.svg /usr/share/icons/hicolor/scalable/apps/flashforgemonitor.svg
sudo install -Dm644 flashforgemonitor.desktop /usr/share/applications/flashforgemonitor.desktop
```

Copy `config.example.json` to `~/.config/flashforgemonitor/config.json`, edit its values for your printer, and protect the file (for example `chmod 600 ~/.config/flashforgemonitor/config.json`). Never commit your real serial/access code to Git.

Run `flashforgemonitor`, or launch it from the desktop menu. A configuration file can also be selected using `--config /path/to/config.json`.

## Timing note

The remaining-time display is indicative, not an exact countdown. It is calculated using the initial estimated duration and printer-reported print progress; it may advance unevenly or fluctuate, particularly during tool changes and near the end.

## Licence

Copyright © 2026 Texman Productions. Flashforge Monitor is licensed under **GNU GPL-3.0-or-later**; see `LICENSE`. Third-party Python/PySide6/mpv dependencies are not bundled. Printer product names and marks belong to their respective owners; this project is not presented as an official Flashforge application.

## Development status

RC1 packaging preparation only. Functional printer behaviour has not been modified in this repository candidate.
