# Community Build (Android)

This fork ships a community build of the Notesnook Android app, built from source
under the terms of the GPL-3.0 license.

## Build

Release APKs are produced by `.github/workflows/android.preview.build.yml`, which
compiles an `arm64-v8a` release variant on every pull request that touches
`apps/mobile/**` or `packages/**`.

To build locally:

```sh
npm ci --ignore-scripts
npm run bootstrap -- --scope=mobile
cd apps/mobile/android
./gradlew assembleRelease -PreactNativeArchitectures=arm64-v8a
```

The output lands in `apps/mobile/android/app/build/outputs/apk/release/`.

## Signing

Community builds are signed with the repository's bundled `debug.keystore`. They
install on-device, but are not upgrade-compatible with the official Play Store
release, which uses a different signing key. Uninstall the official app first.

## Scope

`arm64-v8a` only, which covers essentially all Android devices from 2017 onward.
