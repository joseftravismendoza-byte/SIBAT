# SiBATS app package

Contents: `www/` (the app: index.html, manifest, service worker, icons), `capacitor.config.json`, `package.json`.

## Option A: Install on a phone right now (PWA, no app store)
1. Upload the `www` folder to any HTTPS host (Netlify Drop, GitHub Pages, Cloudflare Pages, Firebase Hosting).
2. Open the link on the phone.
   - Android (Chrome): menu > Install app.
   - iPhone (Safari): Share > Add to Home Screen.
It opens full screen with the SiBATS icon and works offline after the first visit.

## Option B: Get an APK without coding (PWABuilder)
1. Host `www` over HTTPS (Option A step 1).
2. Go to pwabuilder.com, paste your link, choose Android, and download the package.
3. Install the generated APK on your phone (allow "install unknown apps"), or sign and upload the AAB to Google Play.

## Option C: Build the APK yourself (Capacitor + Android Studio)
Requirements: Node.js 18+, Android Studio.
```
npm install
npx cap add android
npx cap sync android
npx cap open android
```
In Android Studio: Build > Build Bundle(s) / APK(s) > Build APK(s). The file is in `android/app/build/outputs/apk/debug/`.
iOS needs a Mac with Xcode: `npm i @capacitor/ios && npx cap add ios && npx cap open ios`.

## Before you ship it
- Accounts are stored in the phone's browser storage, and fares, routes, and countdowns are sample data. Replace them with your server and database.
- Use a real map and GPS (for example the Google Maps SDK or Leaflet with OpenStreetMap) in place of the drawn map.
- Hash passwords on the server (bcrypt or Argon2), never only on the device.
