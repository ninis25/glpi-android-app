# GLPI Android App

Native Android app that wraps a [GLPI](https://glpi-project.org/) / ITSM web interface in a clean, full-screen WebView, giving technicians and users an app-like experience on their phone.

## Features

- Splash screen with logo and loading animation
- **First-run setup**: choose HTTP or HTTPS and enter the server address (IP or domain), saved locally for next launches
- Full-screen WebView with no address bar and no action bar
- Automatic rebranding of "GLPI" labels to "ITSM" in the interface
- Floating settings button, always accessible to change the server

## Tech stack

- Kotlin / Java, Android SDK (min API 21, target API 33)
- AndroidX, Material Components, ViewBinding
- Gradle 7.5, JDK 11

## Configuration

The GLPI API App-Token is not stored in the code. Add it to `local.properties` at the project root (this file is git-ignored):

```properties
glpi.appToken=YOUR_GLPI_APP_TOKEN
```

It is injected at build time as `BuildConfig.GLPI_APP_TOKEN`. The GLPI server address and user credentials are entered in the app on first launch.

## Build

```bash
./gradlew assembleDebug      # app/build/outputs/apk/debug/
./gradlew assembleRelease    # requires a signing configuration, see below
```

Or open the project in Android Studio and use **Build > Build APK(s)**.

## Release signing

Release builds are signed only if a `keystore.properties` file exists at the project root (it is not committed):

```properties
storeFile=your-release.keystore
storePassword=********
keyAlias=your-alias
keyPassword=********
```

Without this file, the project still builds, and release APKs are simply left unsigned.

## Install on a device

Copy the APK to the phone, open it and allow installation from unknown sources if prompted.

## License

MIT
