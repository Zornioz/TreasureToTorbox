# Treasure-Maps → TorBox

An Android app to browse [Treasure-Maps](https://treasure-maps.com) and send NZBs directly to [TorBox](https://torbox.app) with one tap.

![App Icon](app/src/main/res/mipmap-xxxhdpi/ic_launcher.png)

---

## Features

- 🔍 **Search** Treasure-Maps with category filters (Movies, TV, Music, PC, Books, Games, Mobile)
- 📦 **One-tap import** — downloads the NZB and posts it straight to TorBox via API
- 🔑 **API keys saved locally** via `localStorage` (persist across restarts)
- 🌙 **Dark mode** support (follows system setting)
- ↩️ **Back navigation** within the WebView

---

## Requirements

- Android 7.0+ (API 24)
- A [Treasure-Maps](https://treasure-maps.com) account with API key
- A [TorBox](https://torbox.app) account with API key

---

## Build

### Prerequisites

- [Android Studio](https://developer.android.com/studio) (Hedgehog or newer)
- JDK 17+

### Steps

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/treasure-maps-torbox.git
   cd treasure-maps-torbox
   ```

2. Open in Android Studio:
   - *File → Open* → select the project folder
   - Wait for Gradle sync to finish

3. Build the APK:
   - **Debug** (for testing): *Build → Build Bundle(s) / APK(s) → Build APK(s)*
   - **Release** (for distribution): *Build → Generate Signed APK*

The APK will be at:
```
app/build/outputs/apk/debug/app-debug.apk
```

---

## Installation 
- Install the APK file on your phone from /compiled-apk/TorToTreasure.apk

## Setup (Sideloading)

1. Transfer the APK to your Android device (USB, Google Drive, etc.)
2. On your device: *Settings → Apps → Special app access → Install unknown apps* → enable for your file manager or browser
3. Tap the APK file and install

---

## Setup in the App

1. Open the app and tap **⚙ Einstellungen**
2. Enter your **Treasure-Maps API key** (found at `treasure-maps.com/profile`)
3. Enter your **TorBox API key** (found at `torbox.app/settings`)
4. Tap **Speichern**

---

## Project Structure

```
app/src/main/
├── assets/
│   └── scenenzb-torbox.html   # The full app UI (HTML/CSS/JS)
├── java/com/scenenzb/torbox/
│   └── MainActivity.kt        # WebView wrapper
├── res/
│   ├── mipmap-*/              # Launcher icons (all densities)
│   └── values/styles.xml      # App theme (dark/light)
└── AndroidManifest.xml
```

The app is a native Android WebView wrapper around a single self-contained HTML file. All search and API logic lives in `assets/scenenzb-torbox.html`.

---

## API Details

| Service | Endpoint |
|---|---|
| Treasure-Maps | `https://treasure-maps.com/api?t=search&apikey=...` (Newznab-compatible) |
| TorBox | `POST https://api.torbox.app/v1/api/usenet/createusenetdownload` |

---

## License

MIT — do whatever you want with it.
