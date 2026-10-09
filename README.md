# Amiibo Dock (Chameleon Ultra)

Android app that turns a phone into an amiibo base for the **Chameleon Ultra**:
pick a slot, tap an amiibo from your `.bin` collection, and it is loaded into the
Chameleon over Bluetooth LE, ready to scan on a Switch.

## Stack
- Single-page web UI (`www/index.html`), plain HTML/CSS/JS
- [Capacitor 7](https://capacitorjs.com/) to package it as an Android app
- `@capacitor-community/bluetooth-le` for the Chameleon Ultra BLE link
- `jszip` to import a zipped amiibo folder (keeps sub-folders)
- Hardware: Chameleon Ultra (default BLE pairing code `123456`)

## Build the APK

### With GitHub Actions
Every push runs `.github/workflows/build-apk.yml`. Download the
`amiibo-dock-apk` artifact from the run and install `app-debug.apk`.

### Locally (JDK 21 + Android SDK 35)
```
npm install
npm run build          # bundles src/native.js into www/native.js
npx cap sync android
cd android
gradlew assembleDebug
```
Output: `android/app/build/outputs/apk/debug/app-debug.apk`

The `android/` project is committed because it holds the custom launcher icon
(`android/app/src/main/res`). Do not run `npx cap add android` again.

## Usage
- Grant Bluetooth and location permissions, then tap **Connect the Chameleon**.
- Load your amiibo as a `.zip` (keeps folders) or select several `.bin` files.
- Load `key_retail.bin` to enable a new random UID on every emulation.
- Bottom bar: previous amiibo, new UID, next amiibo.
- Loaded amiibo are saved on the device and reloaded every time the app opens.
- The gear button (top right) opens the settings: language (French / English) and clearing the saved amiibo list.
