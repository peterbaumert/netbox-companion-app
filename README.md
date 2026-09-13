# netbox-companion

[![Latest release](https://img.shields.io/github/v/release/peterbaumert/netbox-companion-app)](https://github.com/peterbaumert/netbox-companion-app/releases/latest)

A mobile client for [NetBox](https://netbox.dev/) — look up and document
devices, racks, and cabling from a rack or site visit.

## Get the app

<!-- managed:ios:start -->
**iOS (TestFlight):** [testflight.apple.com/join/BXWN56ZJ](https://testflight.apple.com/join/BXWN56ZJ)

This version is awaiting Apple's beta review; external testers will see it once approved.
<!-- managed:ios:end -->

<!-- managed:android:start -->
**Android:** [netbox-companion-0.21.0.apk](https://github.com/peterbaumert/netbox-companion-app/releases/download/v0.21.0/netbox-companion-0.21.0.apk) — SHA-256 in [netbox-companion-0.21.0.apk.sha256](https://github.com/peterbaumert/netbox-companion-app/releases/download/v0.21.0/netbox-companion-0.21.0.apk.sha256). Sideload instructions and the update caveat are on the [release page](https://github.com/peterbaumert/netbox-companion-app/releases/tag/v0.21.0).
<!-- managed:android:end -->

## Installing and updating on Android

The Android build is distributed as an APK on the
[releases page](../../releases), not through Google Play.

1. Download `netbox-companion-<version>.apk` and its `.sha256` file from the
   release.
2. Check the download: `sha256sum -c netbox-companion-<version>.apk.sha256`
   on Linux/macOS, or `certutil -hashfile <file> SHA256` on Windows and
   compare with the value in the `.sha256` file.
3. Open the APK on the phone and allow installs from that app (browser or
   file manager) when Android asks.

Every release is signed with the same certificate; its SHA-256 fingerprint
is printed on each release page so you can compare it with what Android or
`apksigner` reports. Because the certificate never changes, later releases
install over earlier ones as normal updates and keep your data.

**One exception:** if you installed an earlier test build that was signed
with a different key (any build from before the first release-signed APK),
Android will refuse the update. Uninstall that build first. Uninstalling
deletes the app's data on that phone: stored instances, API tokens and
offline copies. Add the instances again afterwards.

The APK does not update itself. Watch the releases page, or subscribe to
this repository's releases, for new versions.

## Compatibility

Which app version requires which minimum NetBox server version. Tracked
going forward from v0.15.0 — earlier releases were not individually
verified against multiple NetBox versions, so no history is backfilled.

<!-- managed:compat:start -->
| App version | Minimum NetBox version | Notes |
|---|---|---|
| v0.21.0 (current) | 4.5 | Token validation uses /api/authentication-check/ (4.5+). VM type and host-device assignment shown from 4.6+. Verified against 4.6.9 and 4.7.0. |
| v0.20.0 | 4.5 | Token validation uses /api/authentication-check/ (4.5+). VM type and host-device assignment shown from 4.6+. Verified against 4.6.9 and 4.7.0. |
| v0.15.0 | 4.2 | Core features work from 4.2+; VM type assignment and generic cluster scoping require 4.6+. Actively tested against 4.6.8. |
<!-- managed:compat:end -->

## Reporting bugs / feature requests

The app's source code lives in a private repository. This public repo has
no code — it's a dedicated space for testers and users to
[file issues](../../issues) without needing access to the private source.

**Found a bug or have a feature request?** [Open a new issue](../../issues/new/choose).

Please include the app version (the release you installed; on Android the
APK file name carries it), your NetBox version, the platform, and the steps
that lead to the problem.

**Issues are public.** Never paste an API token, and redact hostnames, IP
addresses, tenant or customer names, and any object data from your NetBox
that you do not want visible to everyone. A screenshot with the instance
URL cropped out is fine; a raw API response usually is not.
