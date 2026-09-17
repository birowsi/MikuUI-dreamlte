# Miku UI Snowland for Samsung Galaxy S8 (dreamlte)

Unofficial Miku UI Snowland Android 12L port for the Samsung Galaxy S8.

## Device

- Device: Samsung Galaxy S8
- Codename: `dreamlte`
- Tested model: `SM-G950N`
- SoC: Exynos 8895
- Android: 12L / SDK 32
- Partition layout: legacy A-only
- GApps included

## Status

Working and tested:

- Boot / System UI
- Wi-Fi
- Bluetooth
- Rear camera
- Front camera
- Automatic rotation
- Fingerprint
- Speaker
- Microphone
- Wired headset audio
- Wired charging
- Wireless charging
- USB MTP / ADB
- Google SetupWizard
- Google Play Store / GMS / GSF
- Touch sounds disabled by default

Not fully verified:

- GPS / GNSS fix
- NFC tag operation

Cellular functionality is intentionally outside the scope of this port:

- SIM
- Calls
- SMS
- Mobile data

## Downloads

Tested flashable ROM builds are available from the GitHub Releases section of this repository.

## Build from source

### 1. Initialize Miku UI Snowland

```bash
mkdir -p ~/miku
cd ~/miku

repo init -u https://github.com/Miku-UI/manifesto -b snowland
```

### 2. Add the dreamlte local manifest

```bash
mkdir -p .repo/local_manifests

curl -L \
https://raw.githubusercontent.com/birowsi/MikuUI-dreamlte/main/miku-dreamlte.xml \
-o .repo/local_manifests/dreamlte.xml
```

### 3. Sync sources

```bash
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags
```

### 4. Build

```bash
source build/envsetup.sh
lunch miku_dreamlte-userdebug
m -j$(nproc) diva
```

The flashable ZIP will be generated under:

```text
out/target/product/dreamlte/
```

## Installation

A clean installation with TWRP is recommended.

1. Back up important data.
2. Boot into TWRP.
3. Format Data.
4. Flash the Miku UI ZIP.
5. Reboot to system.

This ROM does not require repartitioning.

The ROM package is not intended to replace:

- modem
- EFS
- recovery
- device firmware

## Source

### Device tree

https://github.com/birowsi/android_device_samsung_dreamlte

### Exynos 8895 common tree

https://github.com/birowsi/android_device_samsung_universal8895-common

### Miku UI build compatibility changes

https://github.com/birowsi/platform_build

### Miku UI SELinux compatibility changes

https://github.com/birowsi/platform_device_miku_sepolicy

The remaining dependencies and exact pinned revisions are defined in:

```text
miku-dreamlte.xml
```

## Notes

This port uses compatibility changes for legacy Samsung Exynos 8895 hardware,
including camera, display/HWC, legacy boot image generation, and SELinux
integration required by the LineageOS-based device tree.

Modified Samsung proprietary binaries are not published in the source
repositories. Required compatibility changes are applied through the
device extraction scripts.

## Credits

- Miku UI
- LineageOS
- 8890q
- Android Open Source Project
