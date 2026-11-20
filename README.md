# LiteTV releases

Download point for [LiteTV](https://github.com/abrakingoo/LiteTV) builds. This repository holds
no source code — only the installable APKs and the small file the app reads to notice that a
newer build exists.

## Installing

Take the newest `.apk` from [Releases](https://github.com/abrakingoo/litetv-releases/releases)
and install it on your Android TV box or phone. Installing over an existing copy keeps your
channels, saved links and Continue watching list.

## How the in-app update check works

The app reads `version.json` from the `main` branch of this repository:

```json
{
  "versionCode": 55,
  "versionName": "2.44",
  "apkUrl": "https://github.com/.../LiteTV-2.44.apk"
}
```

When `versionCode` here is higher than the installed one, the app offers the download at
`apkUrl`. Both this file and the release asset must stay publicly readable, or the check will
fail silently and nobody will be told there is an update.

## Publishing a new build

1. Create a release here tagged `vX.Y` and attach the APK to it.
2. Update `version.json` in the same commit style: raise `versionCode` to match the value in
   the app's `build.gradle.kts`, and point `apkUrl` at the new asset.

`versionCode` is what the comparison uses; `versionName` is only shown to people.
