# Miku UI Snowland for dreamlte

Miku UI Snowland (Android 12L / SDK 32) for the Samsung Galaxy S8.

Tested on SM-G950N.

## Download

See [Releases](https://github.com/birowsi/MikuUI-dreamlte/releases).

GApps are included.

## Device

- Samsung Galaxy S8
- Codename: `dreamlte`
- SoC: Exynos 8895
- Tested model: `SM-G950N`
- Legacy A-only layout

## Working

- Boot
- Wi-Fi
- Bluetooth
- Camera
- Rotation
- Fingerprint
- Speaker / microphone
- Wired headset
- Wired charging
- Wireless charging
- USB MTP / ADB
- Google services

## Not verified

- GPS / GNSS fix
- NFC tags

SIM, calls, SMS and mobile data are not supported by this port.

## Installation

TWRP is required.

1. Back up your data.
2. Format Data.
3. Flash the ROM ZIP.
4. Reboot.

Do not flash a separate GApps package.

No repartitioning is required.

## Build

```bash
mkdir -p ~/miku
cd ~/miku

repo init -u https://github.com/Miku-UI/manifesto -b snowland

mkdir -p .repo/local_manifests
curl -L \
https://raw.githubusercontent.com/birowsi/MikuUI-dreamlte/main/miku-dreamlte.xml \
-o .repo/local_manifests/dreamlte.xml

repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags

source build/envsetup.sh
lunch miku_dreamlte-userdebug
m -j$(nproc) diva
```

Output:

```text
out/target/product/dreamlte/
```

## Source

- [Device tree](https://github.com/birowsi/android_device_samsung_dreamlte)
- [Exynos 8895 common tree](https://github.com/birowsi/android_device_samsung_universal8895-common)
- [Build patches](https://github.com/birowsi/platform_build)
- [SELinux patches](https://github.com/birowsi/platform_device_miku_sepolicy)

Dependency revisions are pinned in [`miku-dreamlte.xml`](./miku-dreamlte.xml).

## Credits

- Miku UI
- LineageOS
- 8890q
- AOSP
