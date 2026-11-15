# microG RCS compatibility test build

[Download the tested APK and test guide](https://github.com/djamelghorab/GmsCore/raw/refs/heads/apk-download/microg-rcs-compatibility-candidate.zip) (ZIP, approximately 99 MiB).

Extract the ZIP before installation. It contains the exact universal APK, `TESTING.md`, checksums and validation results.

Archive SHA-256: `88e0d2a7d0b7bd4026713de611cedb2f7733f919a039c03887fee57f41234954`.
APK SHA-256: `bef5c7a730a5488ef61cbe4f385cd88d07f7329f73c46efac5c1c85eefbb36c5`.

[Source and detailed testing instructions](https://github.com/djamelghorab/GmsCore/blob/18a4c216b0b3178006727e16f8ac34e5ecc51aa4/play-services-constellation/README.md).

## Before testing

Use an existing microG-compatible OS, an already locked bootloader, a compatible signing/update setup, and a real active SIM. This debug package cannot replace preinstalled Google Play services on stock Samsung firmware or update differently signed microG. Keep the bootloader locked; no root is required.

1. Verify the archive checksum, extract it, and verify `SHA256SUMS` inside.
2. Follow `TESTING.md` to record phone/ROM/carrier, bootloader state and current official Google Messages version, then install on a compatible test setup with `adb install -r ./com.google.android.gms-254500037.apk`.
3. Enable microG device registration and Cloud Messaging. Opt into Phone Number Verification; separately opt into SMS verification if testing that path. Follow the ICC special-access instructions only if that carrier requires it.
4. Capture the full/focused logcat commands in `TESTING.md`, verify service dispatch, and activate RCS in Messages.
5. If Connected, exchange a text and image in both directions with a known-working RCS endpoint, with SMS fallback disabled. Reboot and repeat while keeping the bootloader locked.

The build, 153 unit tests, 15 instrumentation tests and seven permission UI checks passed. No current Google Messages binary or real SIM was tested. **End-to-end RCS remains unverified.** The separate RCS service action is still unimplemented; see the guide for known limitations.
