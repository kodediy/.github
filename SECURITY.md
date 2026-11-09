# Security

## Report a problem

**Do not open a public issue for a security problem.** Report it privately, in one of two ways:

- on GitHub: the repository's **Security** tab, then **Report a vulnerability**;
- by email: write to [hello@kode.diy](mailto:hello@kode.diy) with "Security" in the subject.

Say in your report:

- the repository, and the version or the commit;
- what an attacker can do, and what they need first (physical access, the same Wi-Fi network, a paired phone…);
- the steps to reproduce it, or a proof of concept;
- whether you want to be named when the fix is published.

Kode answers by email, keeps you informed while the fix is made, and publishes the fix with a note in the release.

## Supported versions

Only the latest release of kodeOS, of the SDK and of the firmware of the ESP32-C5 receives security fixes. Update first, then check whether the problem is still there.

## What is in scope

- kodeOS and the SDK: the console over the cable, Bluetooth and the Kode channel; the installer of apps and of kodeOS; the bootloader addition.
- The firmware of the ESP32-C5: the link to the main chip, the stored Wi-Fi networks, the Bluetooth keys and the identity of the board.

A problem that needs the board in your hands and a cable to flash it is usually out of scope: the Kode Dot is made to be reflashed by its owner.
