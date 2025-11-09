# Mana Ball Track Ball

[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)
[![QMK Firmware](https://img.shields.io/badge/Firmware-QMK-blue)](https://qmk.fm/)

A fully modular, open-source, 3D-printable trackball with customizable RGB lighting and swappable button modules. The Mana Ball features a translucent 50mm ball illuminated by 6 RGB LEDs, creating a glowing multicolor orb effect reminiscent of mana orbs in video games.

![Mana Ball Track Ball](images/mana-track-ball.jpg)

## Table of Contents

- [Features](#features)
- [Why Mana Ball?](#why-mana-ball)
- [Getting Started](#getting-started)
  - [Materials and Tools](#materials-and-tools)
  - [3D Printing Files](#3d-printing-files)
- [Build Guide](#build-guide)
  - [Common Parts](#common-parts)
  - [Body Options](#body-options)
  - [Button Modules](#button-modules)
  - [Recommended Setup](#recommended-setup)
- [Assembly](#assembly)
  - [Wiring Diagrams](#wiring-diagrams)
  - [Assembly Videos](#assembly-videos)
- [Firmware](#firmware)
- [Configuration](#configuration)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)

## Features

- **Modular Design**: Hot-swappable button modules and body configurations
- **High Precision**: PMW3360 optical sensor for accurate tracking
- **Smooth Movement**: Rexroth Ball Transfer Units (BTUs) for premium feel
- **Customizable RGB**: 6 RGB LEDs with configurable lighting effects
- **Low Profile**: Ergonomic design with low-profile keyboard switches
- **Drag Scrolling**: Configurable scroll feature
- **Universal Compatibility**: Works with all operating systems via USB-C
- **Open Source**: Fully 3D printable with no custom PCBs required
- **QMK Powered**: RP2040 microcontroller running QMK firmware
- **Adjustable Settings**: Pointer speed, scroll speed, and LED effects
- **Standard Components**: Uses any 50mm ball

## Why Mana Ball?

After years of testing various trackballs (documented in my [trackball comparison repository](https://github.com/ArtiomSu/artiomsu-trackball-comparisons-and-mods)), I found that none perfectly suited my needs. While the Ploopy Adept came close after modifications, its button layout still wasn't ideal. The Mana Ball is my solution—a trackball designed specifically for my workflow, with modularity built in so others can adapt it to theirs.

**Best used with**: A QMK-enabled keyboard or macro pad configured with [QMK RAW HID Router Software](https://github.com/ArtiomSu/QMK-Raw-HID-Router) for full customization capabilities. While the trackball can operate standalone with button modules, the HID Router unlocks features like real-time configuration.

## Getting Started

### Materials and Tools

See [materials.md](materials.md) for the complete parts list and required tools.

**What you'll need depends on your build**:
- Skip LEDs if you don't want lighting effects
- Skip hot-melt inserts if not using the optional sensor holder
- Skip keycaps/switches if building a button-less version

**Cost considerations**: The most expensive components are the Rexroth BTUs, which provide the smoothest tracking experience but are surprisingly expensive. All other parts are reasonably priced.

### 3D Printing Files

All STL files are in the [`finished stl/`](<finished stl/>) folder.

**Bambu Studio users**: A pre-configured `.3mf` project file is included with optimized print settings and bed arrangement.

## Build Guide

### Common Parts

These parts are required for all builds:

| Part | File | Notes |
| ---- | ---- | ----- |
| **Head** | [head.stl](<finished stl/head.stl>) | Main component holding the ball and sensor |
| **Shim** | [shim.stl](<finished stl/shim.stl>) | Secures the microcontroller inside the body |
| **Head Sensor Holder** | [head_sensor_holder.stl](<finished stl/head_sensor_holder.stl>) | Optional: Provides extra sensor security (requires hot-melt inserts in head) |

### Body Options

#### Button-Less Bodies

For use with an external keyboard for clicking:

| Part | File | Description |
| ---- | ---- | ----------- |
| **Body Medium** | [body_medium.stl](<finished stl/body_medium.stl>) | One-piece design with integrated controller placement. Clean aesthetics but taller profile |
| **Body Small** | [body_small.stl](<finished stl/body_small.stl>) | Compact design requiring [body_small_cap.stl](<finished stl/body_small_cap.stl>) |
| **Body Small Cap** | [body_small_cap.stl](<finished stl/body_small_cap.stl>) | Cap for small body, conceals wiring |
| **Body Small External** | [body_small_external.stl](<finished stl/body_small_external.stl>) | Compact with exposed controller. Lower profile but visible wires (test design) |

#### Bodies with Button Support

| Part | File | Description |
| ---- | ---- | ----------- |
| **Body Small for Buttons** | [body_small_for_buttons.stl](<finished stl/body_small_for_buttons.stl>) | Standard button-compatible body. Uses [body_small_cap.stl](<finished stl/body_small_cap.stl>) |
| **Body Small for Buttons (Wire Friendly)** | [body_small_for_buttons_bigger_more_wire_cutouts.stl](<finished stl/body_small_for_buttons_bigger_more_wire_cutouts.stl>) | Enhanced wire routing with larger cutouts. Uses [body_small_cap.stl](<finished stl/body_small_cap.stl>) |

### Button Modules

Located in [`finished stl/buttons/`](<finished stl/buttons/>).

**Note**: Button modules are functional but still WIP. Current designs provide working button positions but aesthetics are being refined.

**Compatibility**: Any button-compatible body works with any button module.

### Recommended Setup

**My current configuration**:
- Body: [body_small_for_buttons_bigger_more_wire_cutouts.stl](<finished stl/body_small_for_buttons_bigger_more_wire_cutouts.stl>)
- Buttons: [simple triple button test v2 higher.stl](<finished stl/buttons/simple triple button test v2 higher.stl>)
- Layout: Left click, right click, and drag scroll—perfect for my workflow

## Assembly

### Wiring Diagrams

#### Without Switches

![Wiring Diagram without Switches](images/mana-track-ball-wiring-diagram.jpg)

#### With Switches

![Wiring Diagram with Switches](images/mana-track-ball-wiring-diagram-with-keys.jpg)

**Important notes**:
- **No diodes required**: Single-row, five-column matrix supports n-key rollover without diodes
- **Expandable**: 9 additional free GPIO pins available for up to 14 total switches (requires firmware modification)
- **Flexible switch count**: Using fewer than 5 switches? Just populate the pins you need (starting with GP13/GP12). Unpopulated switches are simply ignored by firmware

### Assembly Videos

Follow these step-by-step video guides:

1. **[Head Assembly](https://youtu.be/o33xUQOpQcM)** - Start here, as this is the most complex and universal component
2. **LED Installation** - *TODO: Video coming soon*
3. **[Body Assembly](https://youtu.be/YjRsaHhR8Q8)** - Attach your chosen body
4. **[Button Module Assembly](https://youtu.be/1hGQQQpRfPQ)** - Add buttons (if applicable)

## Firmware

### Flashing QMK Firmware

**Prerequisite**: Set up QMK on your system following the [official QMK setup guide](https://docs.qmk.fm/#/newbs_getting_started).

```bash
# Clone the firmware repository
git clone https://github.com/ArtiomSu/qmk_firmware.git
cd qmk_firmware

# Switch to the Mana Ball branch
git checkout artiomsu_manaball

# Initialize submodules
qmk git-submodule

# Clean and flash
make clean
qmk flash -kb artiomsu_manaball -km default
```

**Tip**: Flash firmware before wiring to verify the microcontroller works correctly.

## Configuration

### Customizing Settings

Adjust pointer speed, scroll behavior, LED effects, and more using the [QMK RAW HID Router Software](https://github.com/ArtiomSu/QMK-Raw-HID-Router).

**Platform support**: Windows, Linux, and macOS

**Setup process**:
1. The Mana Ball is pre-configured for the HID Router
2. Configure your QMK keyboard/macro pad following the [video tutorial](https://github.com/ArtiomSu/QMK-Raw-HID-Router) at the bottom of the README
3. Control trackball settings via keyboard shortcuts

**Reference implementation**: See my [keyboard firmware](https://github.com/ArtiomSu/qmk_firmware/tree/artiom_dactyl/keyboards/artiomsu_dactyl/keymaps/linux_and_mac) for integration examples.

**Future plans**: Standalone configuration app (desktop or web-based) may be developed, but keyboard integration offers superior workflow integration with layers, macros, and synchronized settings.

## Troubleshooting

**Common Issues**:

- **Ball doesn't track smoothly**: Check BTU alignment and cleanliness
- **LEDs not lighting**: Verify LED wiring polarity and connections
- **Sensor not working**: Ensure sensor is properly seated and lens is clean
- **Buttons not responding**: Check switch wiring and verify GPIO pin connections
- **Firmware won't flash**: Ensure RP2040 is in bootloader mode (hold BOOTSEL while connecting)

**Need help?** Open an issue on GitHub with:
- Photos of your build
- Description of the problem
- What you've already tried

## Contributing

Contributions are welcome! Whether you've designed a new button module, improved a body design, or found a bug:

1. Fork the repository
2. Create a feature branch
3. Submit a pull request with clear descriptions

**Share your builds**: I'd love to see your custom modules and modifications!

## License

This project is licensed under the Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License (CC BY-NC-SA 4.0).

**This means**:
- ✅ You can use, modify, and share this design
- ✅ You must share any modifications under the same license
- ✅ You must give appropriate credit
- ❌ You cannot use this commercially without permission

See [LICENSE](LICENSE) for the full license text.

---

**Questions?** Open an issue on GitHub or check the [QMK RAW HID Router](https://github.com/ArtiomSu/QMK-Raw-HID-Router) documentation for configuration help.
