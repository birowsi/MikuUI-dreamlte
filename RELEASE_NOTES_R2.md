This update adds the Google Photos Pixel XL profile and finishes the integrated
TWRP recovery for the Galaxy S8.

### Changes

- Google Photos reports a Pixel XL (`marlin`) profile. The profile is limited to
  the Photos process.
- Updated the bundled recovery to TWRP `3.7.1_12-miku`.
- Fixed battery percentage and charging status in TWRP.
- Fixed MTP after formatting data and reconnecting USB.
- Kept recovery persistent after the first Android boot.

### Verified

- Clean recovery installation and ROM boot
- Dirty update from r1 with user data preserved
- Google Photos unlimited backup display and a real backup without storage quota
  deduction
- TWRP ADB, bidirectional Windows MTP, battery status and SELinux Enforcing

### Files

- `MikuUI-SNOWLAND-dreamlte-2609232353-GAPPS-UNOFFICIAL.zip`
- `SHA256SUMS`

GApps are included. This build is for `dreamlte` only and has been tested on the
SM-G950N.
