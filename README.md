# prysm-gmscore

A mirror of [ReVanced GmsCore](https://github.com/ReVanced/GmsCore), pinned to a version known to
work with the YouTube build in [prysm-youtube](https://github.com/issac-xt/prysm-youtube).

Nothing here is modified. The APK is byte-for-byte ReVanced's release asset; this repo exists so
[Prysm](https://github.com/issac-xt/prysm) can install it during setup without depending on a third
party's release URLs staying available, and so the exact version is pinned rather than floating.

## What it is for

Prysm's YouTube is repackaged as `prysm.xt.youtube` and signed with Prysm's own key, because a
system-installed YouTube cannot be replaced by a re-signed APK. Google Play Services keys account
authentication on package name plus signing certificate, so neither of those matches any more and
Play Services will not serve the app.

GmsCore is a reimplementation of Play Services that fills that gap: it holds the Google account
itself, and the patched app borrows the sign-in from it. Upstream microG cannot be used here because
it takes the `com.google.android.gms` package name and so cannot coexist with real Play Services;
ReVanced's fork uses `app.revanced.android.gms` specifically so it can.

**Install this before installing Prysm's YouTube.** A build that first starts without GmsCore present
concludes it is absent and will not pick it up afterwards.

## Licence

GmsCore is Apache-2.0, as is microG upstream. See `LICENSE`. All credit to the
[microG](https://github.com/microg/GmsCore) and [ReVanced](https://github.com/ReVanced/GmsCore)
projects.
