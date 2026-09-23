# Miku UI Snowland for Galaxy S8

An Android 12L port of Miku UI Snowland for the Exynos Galaxy S8 (`dreamlte`).
The current release is built and tested on the Korean SM-G950N.

## Downloads

ROM packages and checksums are available on the
[Releases](https://github.com/birowsi/MikuUI-dreamlte/releases) page. GApps are
included; do not install another GApps package.

The ROM includes TWRP `3.7.1_12-miku`. A standalone build without Miku branding
is maintained in
[`twrp_android_device_samsung_dreamlte`](https://github.com/birowsi/twrp_android_device_samsung_dreamlte).

## Device support

- Samsung Galaxy S8
- Codename: `dreamlte`
- Tested model: `SM-G950N`
- Exynos 8895
- Legacy A-only partition layout

Do not install this build on `dream2lte`, Snapdragon models, or any device other
than `dreamlte`.

## Hardware status

Verified on the SM-G950N:

- Display, touch, brightness, rotation and vibration
- Wi-Fi and Bluetooth
- Front and rear cameras, including flash
- Fingerprint reader
- Speaker, microphone and wired headset
- Wired and wireless charging
- USB ADB and MTP
- TWRP decryption/data access, ADB, MTP and battery reporting

GPS and NFC have not received a complete field test. Cellular service is not
supported by this port.

## Google Photos

Google Photos receives a Pixel XL (`marlin`) identity inside the Photos process.
Other Google apps keep Snowland's standard Pixel profile. The current Google
Photos release shows the unlimited backup benefit, completes backups, and does
not deduct the uploaded photo from the account storage quota.

This behavior depends on Google Photos and can change after an app or server-side
update.

## Installation

Back up anything important before changing ROMs.

For a first installation:

1. Boot a compatible TWRP build.
2. Use **Format Data** and confirm the format.
3. Flash the ROM ZIP.
4. Reboot to Android.

For an update from an earlier build of this port, flash the new ZIP without
formatting data. The latest release was tested as a dirty flash and preserved
installed apps and user data.

No repartitioning is required.

## Building

```bash
mkdir -p ~/miku
cd ~/miku

repo init -u https://github.com/Miku-UI/manifesto -b snowland

mkdir -p .repo/local_manifests
curl -L \
  https://raw.githubusercontent.com/birowsi/MikuUI-dreamlte/main/miku-dreamlte.xml \
  -o .repo/local_manifests/dreamlte.xml

repo sync -c -j$(nproc) --force-sync --no-clone-bundle --no-tags

source build/envsetup.sh
lunch miku_dreamlte-userdebug
m -j$(nproc) diva
```

The completed ZIP is written to `out/target/product/dreamlte/`.

## Source

- [dreamlte device tree](https://github.com/birowsi/android_device_samsung_dreamlte)
- [Exynos 8895 common tree](https://github.com/birowsi/android_device_samsung_universal8895-common)
- [Miku frameworks/base](https://github.com/birowsi/platform_frameworks_base)
- [Samsung hardware support](https://github.com/birowsi/android_hardware_samsung)
- [Build system](https://github.com/birowsi/platform_build)
- [Miku SELinux policy](https://github.com/birowsi/platform_device_miku_sepolicy)

Exact source revisions are pinned in [`miku-dreamlte.xml`](./miku-dreamlte.xml).

## Credits

Miku UI, LineageOS, TeamWin, 8890q, Ivan Meler and the Android Open Source
Project.
