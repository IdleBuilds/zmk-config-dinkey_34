# ZMK Config — Dinkey 34

ZMK firmware configuration for the **Dinkey 34**, a 34-key low-profile wireless split keyboard by [Idle Builds](https://idlebuilds.com).

<div align="center">
<img src="docs/images/dinkey_34_zmk.png" alt="Dinkey 34" width="800"/>
</div>

---

## About the Dinkey 34

The Dinkey 34 is a column-staggered split keyboard built around Kailh Choc V1 switches and the Nice!Nano v2 wireless controller. It features 3 pinky column keys per side and 2 thumb keys per side, making it a comfortable entry point into the Dinkey keyboard lineup.

The Dinkey 34 shares its keymap structure and firmware logic with the Dinkey 32|30 — the difference between the two boards is in the PCB design and hardware pin assignments, not the keymap or ZMK behavior layer.

### Specs

| | |
|---|---|
| **Keys** | 34 |
| **Layout** | 3×5 column stagger + 2 thumb keys per side |
| **Switches** | Kailh Choc V1 (PG1350), hot-swap |
| **Controller** | Nice!Nano v2 |
| **Display** | Nice!View (SPI) |
| **Firmware** | ZMK (this repo) + QMK / Vial (wired, see main repo) |
| **Connectivity** | Bluetooth 5.0 / USB-C |
| **Battery** | 110mAh LiPo |
| **Split** | Wireless BLE (no TRRS required) |

---

## Gallery

<div align="center">

| ZMK Build | QMK Build |
|:---:|:---:|
| <img src="docs/images/dinkey_34_zmk.png" width="420"/> | <img src="docs/images/dinkey_34_qmk.png" width="420"/> |

| PCB (back) |
|:---:|
| <img src="docs/images/dinkey_34_naked.png" width="600"/> |

</div>

---

## Getting Started

### Option 1 — Fork and build (recommended for customization)

1. Fork this repository
2. GitHub Actions will automatically build firmware on every push
3. Go to the **Actions** tab → select the latest run → download the `firmware` artifact
4. Extract the zip — you'll find `.uf2` files for left half, right half, and ZMK Studio

### Option 2 — Download pre-built firmware

Pre-built firmware is available from the [Releases](../../releases) page.

---

## Flashing

1. Double-tap the reset button on your Nice!Nano — it will appear as a USB drive named `NICENANO`
2. Drag and drop the appropriate `.uf2` file onto the drive
3. The drive will disconnect automatically when flashing is complete

Flash the **left** `.uf2` to the left half and the **right** `.uf2` to the right half.

> **First flash or pairing issues?** Flash `settings_reset` to both halves first to clear stale pairing data, then reflash left and right firmware.

---

## ZMK Studio

This config includes a ZMK Studio enabled build for real-time keymap editing over USB — no reflashing required.

To use ZMK Studio:
1. Flash the `studio` `.uf2` to the **left half** (the right half uses regular firmware)
2. Connect the left half to your PC via USB-C
3. Open [zmk.studio](https://zmk.studio) in Chrome or download the desktop app
4. Select your keyboard and start remapping

> ZMK Studio changes are stored on the keyboard. Reflashing firmware will reset the keymap to the defaults defined in `config/dinkey34.keymap`.

---

## Customizing Your Keymap

Edit `config/dinkey34.keymap` to change your layout. After saving, commit and push to trigger a new GitHub Actions build.

Refer to the [ZMK documentation](https://zmk.dev/docs/keymaps) for keymap syntax and available behaviors.

---

## Build Guide

Full assembly instructions are available at [idlebuilds.com/build-guide](https://idlebuilds.com/build-guide).

---

## File Structure

```
zmk-config-dinkey_34/
├── build.yaml                        # GitHub Actions build matrix
├── config/
│   ├── dinkey34.keymap               # Keymap definition
│   ├── dinkey34.conf                 # Firmware configuration
│   └── west.yml                      # ZMK dependency manifest
├── boards/shields/dinkey34/
│   ├── Kconfig.defconfig             # Shield Kconfig defaults
│   ├── Kconfig.shield                # Shield detection
│   ├── dinkey34.dtsi                 # Matrix transform + kscan base
│   ├── dinkey34-layouts.dtsi         # Physical key layout (ZMK Studio)
│   ├── dinkey34_left.overlay         # Left half pin assignments
│   └── dinkey34_right.overlay        # Right half pin assignments
└── .github/workflows/build.yml       # GitHub Actions workflow
```

---

## Purchasing

The Dinkey 34 is available as a kit or complete build from [Idle Builds](https://idlebuilds.com).

| Option | Price |
|---|---|
| Kit — Wired | from $80 |
| Kit — Wireless | from $195 |
| Complete Build — Wired | from $175 |
| Complete Build — Wireless | from $275 |

---

## Related

- [zmk-config-dinkey_32_30](https://github.com/IdleBuilds/zmk-config-dinkey_32_30) — ZMK config for the Dinkey 32|30
- [Idle Builds Dinkey](https://github.com/IdleBuilds/Dinkey) — Hardware files, QMK, Vial, and build guides
- [ZMK Documentation](https://zmk.dev/docs)
- [Idle Builds](https://idlebuilds.com)

---

## Contact

Questions about the build, firmware, or purchasing? Reach out at [eldi@idlebuilds.com](mailto:eldi@idlebuilds.com)

---

## License

MIT © Idle Builds
