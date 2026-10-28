# GridLens for Android

Run the Fleet dashboard directly on an Android phone. Both the interface and
its public-data service run on the phone; a laptop is not required. Internet
access is required for live data. Android 8.0 or newer, on arm64 phones, is supported
by this build; x86_64 is included for emulator testing. No iPhone app is provided.

## Install

1. [Download GridLens Android](https://github.com/MachoDrone/gridlens-android-releases/releases/latest/download/gridlens-android.apk).
2. Open the APK. Android may ask you to allow installations from your browser.
3. Open GridLens. Online GPU Hosts can discover public hosts immediately. Use
   **Hosts** to import your own public-address JSON list for Supplied Host Addresses
   or Real200. Lists stay in app-private storage.

## Update

Press **Update** in GridLens. When a newer release is available, choose to install
it and confirm Android's installer prompt. The first in-app update may require
allowing installations from GridLens. Updates preserve imported lists and settings.
Do not uninstall first: uninstalling removes app-local data.

The app checks the APK hash, size, application ID, version and signing identity
before opening Android's installer. There is no GitHub login or token in the app.
Current versions check on opening/resuming and every five minutes while the app
is in the foreground. **Update** also checks manually; provider-requested waits
still apply. Downloads and installation require your action. GitHub, the internet
and upstream public data services must be reachable; cached/unknown readings are
not live proof.

Android **0.2.10** repairs blank PC IP readings caused by saved node state or a
missing received cache record. PC IP checks use their own validated connection
state, independently of node bindings and optional sudo information. Cached IP
redelivery preserves the original measurement and provider waits. Explicit
PC-only monitoring approval remains available when node bindings cannot be
verified. Existing credentials, identity checks, manual pauses and denials remain
intact; no container renaming or host installation is required.

The six-mode IP toggle and direct host-curl collection from 0.2.9 remain included.

## Development and releases

[Android source](https://github.com/MachoDrone/gridlens-android) is separate from
[the desktop app](https://github.com/MachoDrone/gridlens-typescript). This repository
contains the release workflow and signed downloads; it holds no operator lists,
wallet credentials or signing keys in Git.

The release workflow checks public Android `main` for a new `version.json` on a
15-minute schedule and can also be run manually. GitHub may delay scheduled runs.
A version bump publishes only after the application checks and Android build pass.
Editing source without increasing the version does not replace an installed APK.
Signing credentials are restricted GitHub Actions secrets, independent of wallets.

The initial release is an early Android build. See the release notes for actual
automated/emulator verification and outstanding physical-phone checks.
