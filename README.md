# 🚨 _One-Stop-Shop_ Sovol SV06 Klipper Configuration

This branch contains the Klipper configuration and firmware for the **Sovol SV06** 3D printer with the **BTT SKR-Mini-E3-V3.0** motherboard.

| Printer                     | Branch                                                                              |
| --------------------------- | ----------------------------------------------------------------------------------- |
| Sovol SV06                  | [master](https://github.com/bassamanator/Sovol-SV06-firmware/tree/master)           |
| Sovol SV06 Skr-Mini-E3-V3.0 | ✨**You are here**✨                                                                |
| Sovol SV06 Plus             | [sv06-plus](https://github.com/bassamanator/Sovol-SV06-firmware/tree/sv06-plus)     |
| All other printers          | [any-printer](https://github.com/bassamanator/Sovol-SV06-firmware/tree/any-printer) |

I am creating these files for my personal use and cannot be held responsible for what it might do to your printer. Use at your own risk.

🙏🏻🙌🏻 Big thanks to [transistor1](https://github.com/transistor1) for getting the `printer.cfg` up an running to begin with.

## Outline

- [Installation Instructions](#installation-instructions)
  - [Electronic Wiring](#electronic-wiring)
  - [⚠️ Important Note About Stepper Motor Current](#important-note-about-stepper-motor-current)
  - [Flash Firmware](#flash-firmware)
  - [Download Klipper Configuration](#download-klipper-configuration)
- [Initial Steps](#initial-steps)
- [Directory Structure](#directory-structure)
- [Support Me](#support-me)
- [Useful Resources](#useful-resources)
- [Sovol Official Links](#sovol-official-links)
- [Sources](#sources)

## Installation Instructions

### Electronic Wiring

Wire cables according to the following diagram:
<img src="./misc/skr-mini/skr-mini-e3-v3.0-v1678580296384.png" alt='skr-mini-e3-v3.0 installation instructions'/>

### Important Note About Stepper Motor Current

For the SKR-Mini-E3-V3.0, the `run_current` for x, y, z stepper motors has been reduced in the `printer.cfg`, because the standard current seems to make the steppers dangerously hot. You may have to increase the current, or if the motors are still too hot, you may have to decrease it.

💡 Although stepper motors can withstand upwards of 125C, they should at the most get hot to the touch (~55C), not _very hot_.

### Flash Firmware

💡 _If you have already flashed klipper onto your motherboard in the past, you can skip this step._

Please note:

- The firmware file **must** be named `firmware.bin`.
- The firmware files are located in `misc/skr-mini`.
- Many users have reported having issues flashing Klipper using the Sovol microSD card.

#### Select Your Firmware

- `klipper-USB.bin` compiled by BTT.
- `klipper-v0.11.0-198-g33b18fd6-latest-UNTESTED.bin` that I compiled, however, it is **untested**.

##### Build Your Own

Find instructions on how to build the firmware yourself [here](https://github.com/bigtreetech/BIGTREETECH-SKR-mini-E3/tree/master/firmware/V3.0/Klipper#build-firmware-image).

<img src="./misc/skr-mini/menuconfig.png" width="500" alt='ls output'/>

#### 1. Prepare the microSD Card for Flashing with These Parameters

- Size: `16GB` maximum.
- File system: `FAT32`.
- Allocation unit size: `4096 bytes`.
- Must not contain any files _except_ the firmware file.

#### 2. Flashing Procedure

1. Disconnect any USB cables that might be connected to the motherboard.
2. Copy `firmware.bin` to the microSD card.
3. Make sure the printer is off.
4. Insert the microSD card into printer.
5. Turn on the printer and wait a minute (usually takes 10 seconds).
6. Turn off the printer and remove the microSD.

### Download Klipper Configuration

You can choose _either_ of the 2 following methods.

#### Method 1: Clone the Repository

1. `cd ~/printer_data/config`
2. Empty entire `~/printer_data/config` folder.
   - In linux, you can delete files via `rm fileName` and directories via `rmdir directoryName`.
3. `git clone -b skr-mini-e3-v3 --single-branch https://github.com/bassamanator/Sovol-SV06-firmware.git .` ⚠️ Don't miss the period!

#### Method 2: Download the ZIP

1. [Download](https://github.com/bassamanator/Sovol-SV06-firmware/archive/refs/heads/skr-mini-e3-v3.zip) the `ZIP` file containing the Klipper configuration.
2. See Step 2 in Method 1.
3. The parent folder in the `ZIP` is `Sovol-SV06-firmware-skr-mini-e3-v3`. This is relevant in the next step.
4. Extract **only** the _contents_ of the parent folder into `~/printer_data/config`.

## Initial Steps

Once you've cloned or downloaded the configuration, please follow instructions found in [Initial Steps](https://github.com/bassamanator/Sovol-SV06-firmware#initial-steps).

## Directory Structure

This repository contains many files and folders. Some are _necessary_ for this Klipper configuration to work, others are not.

- **Necessary** items are marked with a ✅.
- Items that can _optionally_ be deleted are marked with a ❌.

```
├── cfgs ✅
│   ├── adxl-direct.cfg
│   ├── adxl-rp2040.cfg
│   ├── adxl-rpi-pico-2x.cfg
│   ├── MECHANICAL_GANTRY_CALIBRATION.cfg
│   ├── misc-macros.cfg
│   ├── PARKING.cfg
│   └── TEST_SPEED.cfg
├── CODE_OF_CONDUCT.md ❌
├── CONTRIBUTING.md ❌
├── .github ❌
│   ├── FUNDING.yml
│   └── ISSUE_TEMPLATE
│       ├── bug_report.md
│       └── feature_request.md
├── .gitignore ❌
├── images ❌
│   ├── cup-border.png
│   ├── githubstar.gif
│   ├── heart.gif
│   ├── logo_white_stroke.png
│   └── party_blob.gif
├── misc ❌
│   ├── M503-output.yml
│   ├── skr-mini
│   │   ├── klipper-USB.bin
│   │   ├── klipper-v0.11.0-198-g33b18fd6-latest-UNTESTED.bin
│   │   ├── ls-output.png
│   │   ├── menuconfig.png
│   │   └── skr-mini-e3-v3.0-v1678580296384.png
│   ├── sv06-buildPlate.png
│   ├── SV06-buildPlate.stl
│   └── SV06-texture.svg
├── moonraker.conf ✅
├── printer.cfg ✅
├── README.md ❌
└── .vscode ❌
    └── settings.json
```

## Support Me

Please ⭐ star ⭐ this repository!

If you found my work useful, please consider buying me a [<img src="./images/logo_white_stroke.png" height="20" alt='Ko-fi'/>](https://ko-fi.com/bassamanator).

## Useful Resources

- [Everything Sovol SV06](https://github.com/bassamanator/everything-sovol-sv06)
- [RP2040-Zero ADXL345 Connection Klipper](https://github.com/bassamanator/rp2040-zero-adxl345-klipper)
- ⭐⭐⭐⭐⭐ [Ellis' Print Tuning Guide](https://ellis3dp.com/Print-Tuning-Guide)
- [Simplify3D Print Quality Troubleshooting Guide](https://www.simplify3d.com/resources/print-quality-troubleshooting/)

## Sovol Official Links

- [SV06 Marlin Source Code](https://github.com/Sovol3d/Sv06-Source-Code)
- [SV06 Models](https://github.com/Sovol3d/SV06-Fully-Open-Source)
- [SV06 Plus Marlin Source Code and Models](https://github.com/Sovol3d/SV06-PLUS)

## Sources

- https://www.klipper3d.org
- https://ellis3dp.com/Print-Tuning-Guide
- https://github.com/strayr/strayr-k-macros
- https://docs.vorondesign.com/build/software/miniE3_v20_klipper.html
- https://github.com/spinixguy/Sovol-SV06-firmware
- https://www.printables.com/model/378915-sovol-sv06-buildplate-texture-and-model-for-prusas
- https://github.com/AndrewEllis93/Ellis-SuperSlicer-Profiles

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/H2H0HIHTH)
