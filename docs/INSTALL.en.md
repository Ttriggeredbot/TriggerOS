# Installing TriggerOS

[Русская версия](INSTALL.ru.md)

> ⚠️ Do this at your own risk. Partitioning the SD card **erases it completely**. Before you start, save everything you need
> from the card and back up the eMMC in hekate (Tools → Backup eMMC → eMMC BOOT0 & BOOT1 and eMMC RAW GPP).

## Requirements
- Nintendo Switch **OLED** with a modchip and the **hekate** bootloader (recent 6.x).
  Tested on the OLED model; other models have not been tested yet.
- **microSD of 64 GB or more** (128 GB recommended, A1/A2 class). Give Android at least 32 GB, 48 GB or more recommended —
  Ubuntu lives inside it too.
- A computer with **ADB** ([Android Platform Tools](https://developer.android.com/tools/releases/platform-tools)) and a USB-C cable.

## Release files
Download from [Releases](https://github.com/Ttriggeredbot/TriggerOS/releases/latest):

| File | What it is |
|---|---|
| `TriggerOS-0.7-20261114-nx_tab.zip` | the system itself (installed through recovery, **do not unzip**) |
| `TriggerOS-0.7-boot-sd.zip` | SD card boot kit (unzip to the root of the card) |
| `SHA256SUMS.txt` | checksums |

## Installing to the SD card

### 1. Partition the card
1. Boot hekate with the card inserted.
2. **Tools → Partition SD Card.**
3. Set the **Android (Dynamic)** slider (32 GB minimum, 48+ recommended). The rest stays FAT32 (hekate files).
   A **Linux (L4T)** partition is not needed — Ubuntu is already inside TriggerOS.
4. **Next Step → Start.** Wait until it finishes. hekate backs up and restores the card's files (up to 1 GB).

### 2. Boot kit
1. In hekate: **Tools → USB Tools → SD Card** — the card shows up on the computer as a USB drive.
2. Unzip `TriggerOS-0.7-boot-sd.zip` **to the root of the card** (the `bootloader` and `switchroot` folders merge with existing ones).
3. Safely eject the card on the computer and close USB mode in hekate.

### 3. Flash the boot partitions
1. In hekate: **Tools → Partition SD Card → Flash Android.**
2. hekate writes the kernel, recovery and dtb from `switchroot/install`. If it offers to reboot to recovery, accept.
   If it doesn't, see the next step.

### 4. Enter recovery
**Hold VOL+** and choose **More Configs → TriggerOS** in hekate. Keep holding VOL+ until the recovery menu appears.

### 5. Install the system
1. In recovery: **Factory reset → Format data/factory reset** (first install only).
2. **Apply update → Apply from ADB.**
3. Connect the console to the computer and run:
   ```
   adb sideload TriggerOS-0.7-20261114-nx_tab.zip
   ```
   The counter may stop at ~47% and print `Total xfer: 1.00x` — that is normal.
4. When recovery reports a successful install — **Reboot system now**.

The first boot takes a few minutes. Ubuntu unpacks the first time you start a Linux app (~10 seconds).

### Booting afterwards
hekate → **More Configs → TriggerOS** (you can set it as autoboot in hekate settings).

## Updating
Hold VOL+ at boot → recovery → **Apply from ADB** → `adb sideload <new zip>` → Reboot.
**Do not format data when updating** — your apps and files are kept.

## Installing to internal storage (eMMC)
TriggerOS can also run from internal storage — that's how we run it. It's faster than SD, but harder and riskier:
you need free space on the eMMC and Android partitions on it (`boot`, `recovery`, `dtb`, `misc`, `cache`,
`super`, `userdata`) **without touching** Nintendo's system partitions (PRODINFO etc.). Only do this if you know
GPT well and have a full eMMC backup.

Differences from the SD install:
- add the line `emmc=1` to `bootloader/ini/triggeros.ini` on the SD card;
- the SD card is still required — it holds hekate and `switchroot/android/*` for booting;
- hekate's built-in eMMC manager may hang on consoles without a HOS USER partition — if that happens,
  power off (hold the power button for 15 s); it doesn't get to write anything.

A detailed eMMC guide will come in a later version.

## Troubleshooting
- **Stuck at the logo** — enter recovery (VOL+) and run `adb sideload` again.
- **`adb` doesn't see the device** — on Linux add a udev rule for USB ID `057e`, on Windows install the Google USB driver.
- Going back to Horizon is easy: TriggerOS lives on its own partitions, booting HOS from hekate works as before.

Questions and bugs — [Issues](https://github.com/Ttriggeredbot/TriggerOS/issues).
