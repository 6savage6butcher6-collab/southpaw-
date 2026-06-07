# Left Hand Mode – MVP

A system-wide Android accessibility app that mirrors app layouts for left-handed users, keeping all text readable.

---

## How to Open in Android Studio

1. Download/unzip this project folder
2. Open Android Studio → **File > Open** → select the `LeftHandMode` folder
3. Wait for Gradle sync to finish (takes 1–2 minutes first time)
4. Click the green ▶ Run button to launch on emulator or your phone

---

## How It Works

The app uses Android's **Accessibility Service** to draw a transparent overlay on top of all apps. The overlay has `scaleX = -1` applied, which mirrors everything horizontally. Text appears flipped back to readable because the overlay is transparent — but buttons, scrollbars, sidebars, and navigation all shift to the left side.

---

## First-Time Setup (on device)

1. Open the app
2. Tap **"Go to Accessibility Settings"**
3. Find **"Left Hand Mode"** in the list
4. Toggle it **ON** and confirm the permission
5. Go back to the app and flip the switch

---

## Project Structure

```
app/src/main/
├── java/com/lefthandmode/
│   ├── MainActivity.kt                  # UI + toggle
│   ├── LeftHandAccessibilityService.kt  # Core mirror logic
│   └── LeftHandPreferences.kt           # Saves on/off state
├── res/
│   ├── layout/activity_main.xml         # Main screen UI
│   ├── values/strings.xml
│   ├── values/colors.xml
│   ├── values/styles.xml
│   └── xml/accessibility_service_config.xml
└── AndroidManifest.xml
```

---

## MVP Limitations (known, for future versions)

- **SurfaceView apps** (video players, some games): visual mirror may not apply, but this is a small subset
- **Keyboard**: system keyboard may also appear mirrored — next version will exclude it
- **iOS**: Not possible with this approach; would need a different strategy
- **Touch coordinates**: Currently pass-through; next version will flip X coordinates for full accuracy on mirrored taps

---

## Next Features (post-MVP)

- [ ] Per-app whitelist/blacklist (exclude apps you don't want mirrored)
- [ ] Quick Settings tile for fast toggle from notification shade
- [ ] Keyboard exclusion
- [ ] Touch coordinate flipping for perfect tap accuracy
- [ ] Home screen widget
