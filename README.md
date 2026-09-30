# Liquid Glass UI

Original, privacy-first Android launcher for Android 11+ (`com.liquidglass.ui`). It uses Jetpack Compose and an original translucent glass visual system. It does not copy Apple assets or layouts.

## Important platform behavior

The app declares `MAIN/HOME/DEFAULT`, so Android can offer it as a Home app. On Android 10+, the app uses the official Home role request flow; otherwise it opens Home settings. It never silently changes the default launcher.

The control center deliberately opens Android Settings for protected toggles such as Wi-Fi, mobile data and airplane mode. This is expected behavior for a normal third-party app. Brightness is adjusted for the app window and media volume uses the public AudioManager API.

Notification cards are optional and only populate after the user grants Notification Access in Android Settings.

## Build requirements

- Android Studio with JDK 17
- Android SDK Platform 36
- Android Gradle Plugin 9.1.1 / Gradle 9.3.1
- Kotlin 2.2.10 Compose compiler plugin
- Android 11+ device/emulator

## Android Studio

1. Open this folder in Android Studio.
2. Let Gradle sync and install missing SDK Platform 36 if prompted.
3. Connect an Android 11+ phone with USB debugging enabled, or create an emulator.
4. Run `app`.
5. For an APK: **Build > Generate App Bundles or APKs > Generate APKs**.
6. Debug APK: `app/build/outputs/apk/debug/app-debug.apk`.
7. On the phone, install the APK, open it, then tap **Set as Home** in Liquid Glass UI or go to Android **Settings > Apps > Default apps > Home app** and select it.

## GitHub Codespaces

A Codespace needs JDK 17, Android SDK Platform 36 and Gradle 9.3.1. If `gradle` is unavailable, install/use the Gradle wrapper first. Then from the project root:

```bash
gradle wrapper --gradle-version 9.3.1
./gradlew :app:assembleDebug
```

APK: `app/build/outputs/apk/debug/app-debug.apk`.

For a fresh Ubuntu Codespace, make sure `ANDROID_HOME` points to an Android SDK containing platform 36 and build-tools 36.0.0. Android Studio is generally easier for the first build because it manages SDK components.

## Google AI Studio

Google AI Studio can generate/edit the source, but it is not itself an Android Gradle build environment. Upload/open the project files in a coding workspace that has JDK 17 + Android SDK + Gradle, then run:

```bash
./gradlew :app:assembleDebug
```

If the environment has no Android SDK, build the same project in Android Studio or a configured Codespace.

## Privacy

No network permission is declared. No location, contacts, microphone, camera, SMS or call-log permission is declared. Notification access is an explicit user-granted special access and is never read before that access is granted.
