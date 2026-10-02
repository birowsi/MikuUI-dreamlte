# Miku UI Snowland for Galaxy S8

Unofficial Android 12L port of Miku UI Snowland for the Exynos Galaxy S8
(`dreamlte`). I build and test it on a Korean SM-G950N.

XDA thread: [Miku UI Snowland for S8](https://xdaforums.com/t/rom-unofficial-12l-miku-ui-snowland-for-s8.4802675/)

## Downloads

Grab the ZIP and `SHA256SUMS` from
[Releases](https://github.com/birowsi/MikuUI-dreamlte/releases). GApps are
already in the ZIP, so don't flash another GApps package on top.

The ROM ships TWRP `3.7.1_12-miku` and keeps it as the recovery after Android
boots. If you just want the recovery without the Miku tag, use the standalone
build from
[`twrp_android_device_samsung_dreamlte`](https://github.com/birowsi/twrp_android_device_samsung_dreamlte).

## Supported device

Galaxy S8, Exynos 8895, codename `dreamlte`. Only the SM-G950N has been tested.

Not for `dream2lte` (S8+), Snapdragon S8 models or anything else. The partition
layout is the stock A-only one and nothing gets repartitioned.

## What works

Tested on my SM-G950N:

- Display, touch, brightness, auto-rotate, vibration
- Wi-Fi, Bluetooth
- Front and rear cameras, flash
- Fingerprint
- Speaker, microphone, wired headset
- Wired and wireless charging
- ADB and MTP
- GPS (position fix and heading)
- NFC tag reading
- TWRP: data access, ADB, MTP both ways, battery level

## Not tested yet

SIM detection, calls, SMS/MMS and LTE data. The radio stack is in the build,
I just haven't had a SIM in the phone on this release. If you try it, please
report back on XDA either way.

## Things to know

**This is a `userdebug` build.** `adb root` works whenever USB debugging is on,
which gives a root shell to any computer you've authorized for debugging. Keep
USB debugging off when you're not using it.

**Google Photos** sees the phone as a Pixel XL (`marlin`). This only applies
inside the Photos app, other Google apps get Snowland's usual Pixel profile.
Right now Photos shows unlimited backup and uploads don't count against storage.
That's up to Google, though, and could stop working after an app or server
update.

## Installing

Back up first.

Coming from another ROM:

1. Boot TWRP.
2. Format Data (the one where you type `yes`).
3. Flash the ROM ZIP.
4. Reboot.

Updating from an earlier build of this port: flash the new ZIP in TWRP without
formatting. The r1 → r2 dirty flash kept all my apps and data.

## Building

```bash
mkdir -p ~/miku && cd ~/miku
repo init -u https://github.com/Miku-UI/manifesto -b snowland

mkdir -p .repo/local_manifests
curl -L https://raw.githubusercontent.com/birowsi/MikuUI-dreamlte/main/miku-dreamlte.xml \
  -o .repo/local_manifests/dreamlte.xml

repo sync -c -j$(nproc) --force-sync --no-clone-bundle --no-tags

source build/envsetup.sh
lunch miku_dreamlte-userdebug
m -j$(nproc) diva
```

The ZIP ends up in `out/target/product/dreamlte/`.

## Sources

- [Device tree](https://github.com/birowsi/android_device_samsung_dreamlte)
- [universal8895 common tree](https://github.com/birowsi/android_device_samsung_universal8895-common)
- [Kernel](https://github.com/8890q/android_kernel_samsung_universal8895)
- [Vendor blobs](https://github.com/8890q/proprietary_vendor_samsung)
- [frameworks/base](https://github.com/birowsi/platform_frameworks_base)
- [hardware/samsung](https://github.com/birowsi/android_hardware_samsung)
- [build/make](https://github.com/birowsi/platform_build)
- [Miku sepolicy](https://github.com/birowsi/platform_device_miku_sepolicy)

Every repo is pinned to an exact commit in
[`miku-dreamlte.xml`](./miku-dreamlte.xml).

## Credits

Miku UI, LineageOS, TeamWin, 8890q, Ivan Meler, AOSP.
