# ed-journal-chat

A native Linux console reader for Elite Dangerous in-game chat, inspired by and based on the original Windows version by [LittleFool](https://github.com/LittleFool/ed-journal-chat).

## What it does

Tails your Elite Dangerous journal file in real time and displays incoming and outgoing chat messages in the terminal, colour-coded by channel. Also shows friend requests, wing invites, and game open/close events.

### Channels and colours

| Channel      | Colour  |
|--------------|---------|
| local        | Yellow  |
| direct (PM)  | Yellow  |
| team (wing)  | Cyan    |
| system       | Red     |
| squadron     | Green   |
| squad leaders| Green   |
| voicechat    | Magenta |
| multicrew    | Blue    |

## Requirements

- Python 3.10+
- `wl-clipboard` (Wayland) **or** `xclip` (X11/XWayland) — for clipboard features

Install clipboard support on Arch/CachyOS:

```bash
sudo pacman -S wl-clipboard   # Wayland (recommended)
# or
sudo pacman -S xclip          # X11 / XWayland
```

## Installation

Copy the script to somewhere on your `$PATH`:

```bash
cp ed-journal-chat ~/.local/bin/
chmod +x ~/.local/bin/ed-journal-chat
```

### Journal path

The journal directory is hardcoded near the top of the script:

```python
JOURNAL_PATH = Path.home() / "Nextcloud/Apps/Elite Dangerous/Journal Files/Elite Dangerous"
```

Change this to wherever your journals actually live. A common default for Steam/Proton installs is:

```
~/.steam/steam/steamapps/compatdata/359320/pfx/drive_c/users/steamuser/Saved Games/Frontier Developments/Elite Dangerous/
```

## Usage

```bash
ed-journal-chat
```

On launch you are shown the five most recent Live journals and the five most recent Legacy journals. Pick one by number and the watcher starts.

### Keybindings

| Key   | Action                                  |
|-------|-----------------------------------------|
| `h`   | Toggle this help screen                 |
| `q`   | Quit                                    |
| Space | Copy current FSD target system to clipboard |
| `s`   | Copy last **sent** message to clipboard |
| `r`   | Copy last **received** message to clipboard |

## Credits

Original Windows application by [LittleFool](https://github.com/LittleFool/ed-journal-chat). This is a from-scratch Linux port with no Windows or .NET dependencies.
