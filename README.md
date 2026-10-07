# Neon Player

A futuristic **neon / glassmorphism** redesign of the open-source [VLC for Android](https://code.videolan.org/videolan/vlc-android) media player.

> **Status:** work in progress (Stage 1 of the redesign). The playback engine is untouched, only the UI/UX layer is being modified.

This is an **independent, unofficial fork**. It is not affiliated with, endorsed by, or supported by VideoLAN. "VLC" and the VLC cone logo are trademarks of VideoLAN and are not used as branding here.

---

## What changed so far

- Electric cyan accent replaces the original orange across the whole app
- Near-black, blue-tinted AMOLED-friendly backgrounds
- Dark theme by default on fresh installs
- Neon hairline on the bottom navigation bar
- Cyan-to-purple gradient progress line on the mini-player
- New original launcher icon and app name ("Neon Player")
- GitHub Actions workflow that builds the APK in the cloud

Playback, codecs, subtitles, playlists, casting, background playback and settings are the same as upstream VLC for Android.

## Roadmap

- [x] Stage 1: neon color palette, dark default, icon, build pipeline
- [ ] Floating glass bottom navigation with animated indicator
- [ ] Redesigned Home screen and media cards
- [ ] Mini-player and music "Now Playing" screen
- [ ] Video player HUD, neon seekbar, seek/volume/brightness indicators
- [ ] Search, file browser and settings redesign
- [ ] Splash screen and page transitions
- [ ] Theme chooser (Purple, Blue, Magenta, Emerald, Sunset, AMOLED)
- [ ] Reduce Animations setting
- [ ] Optional music visualizer

## Build the APK with GitHub Actions

1. Open the **Actions** tab of this repository.
2. Select **Build Neon Player APK** and click **Run workflow**.
   - `debug`: installs alongside the normal VLC app (default)
   - `release`: optimized build, signed with a throw-away key
3. Wait about 15 to 30 minutes.
4. Open the finished run and download **NeonPlayer-APK** from the **Artifacts** section.
5. Unzip it and install the `.apk` on your phone (allow "Install unknown apps" if asked).

The build uses the prebuilt LibVLC and medialibrary from Maven, so the native engine is not compiled from source.

## Build locally

Requirements: JDK 17 or newer, Android SDK (API 36), Gradle 9.3.1.

```
echo "sdk.dir=/path/to/Android/Sdk" > local.properties
mkdir -p libvlcjni/libvlc
gradle :application:app:assembleDebug
```

The APK is created in `application/app/build/outputs/apk/debug/`.

## Project structure

| Path | Purpose |
|------|---------|
| `application/vlc-android` | Main app: screens, adapters, player, resources |
| `application/resources` | Shared colors, drawables, strings, icons |
| `application/app` | Application module and APK packaging |
| `medialibrary` | Media library module |
| `.github/workflows/build-apk.yml` | Cloud APK build |

## License

This project is a modified version of VLC for Android and is licensed under **GPLv2 or later**. See [COPYING](COPYING). The VLC engine (LibVLC) is licensed under LGPLv2.1. If you distribute this app, you must also make the corresponding source code available.

## Credits

- [VideoLAN](https://www.videolan.org/) and all VLC for Android contributors
- Upstream source: https://code.videolan.org/videolan/vlc-android
