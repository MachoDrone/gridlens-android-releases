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

Android **0.2.11** adds a direct IP check and repairs SSH key selection. Tap the
PC’s IP value, then **Check / repair this PC’s IP**. The native screen verifies the
saved SSH connection and uses host curl without inspecting containers. Missing or
paused PC-IP approval requires native confirmation and verification of the saved
key; node monitoring and wallet permissions remain separate.

When a server offers multiple SSH key types, GridLens now prefers the type of its
existing pinned key. Actual key replacement still fails verification. Cache source
times, provider waits and credential-denial controls remain intact. No container
renaming or host installation is required. The six-mode IP toggle is unchanged.

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
