# Orbitude

**Your place in the universe, live.** A 3D globe lit by the real Sun, the Sun, Moon and planets in your sky,
the solar system and the Milky Way. Zoom from space down to street level in satellite photos. Search 10,986 cities and 3,865 states and provinces, or use your phone's GPS.
Everything except the satellite close-ups works offline.

- App name: **Orbitude**
- App ID (Android package / iOS bundle ID): **com.orbitude.app**. Change it in `capacitor.config.json` *before* your first store upload if you want a different one; it can never change afterwards.

---

## 1. Install as a web app (iPhone and Android, about 10 minutes, free)

1. Put the `www` folder on any free HTTPS host, for example **Netlify Drop** (https://app.netlify.com/drop): drag the `www` folder onto the page.
2. Open the address it gives you on your phone.
   - **iPhone (Safari):** Share → **Add to Home Screen**.
   - **Android (Chrome):** ⋮ → **Install app**.

To try it on your computer first: `npm run serve`, then open http://localhost:8080

## 2. Android app

Needs **Android Studio** (https://developer.android.com/studio) and **Node.js 18+**.

```bash
npm install
npx cap sync android
npx cap open android
```

- Test on your phone: plug it in (USB debugging on) and press **Run**.
- Build for Google Play: **Build → Generate Signed App Bundle / APK → Android App Bundle**. Keep the keystore file and its passwords safe forever; you need them for every future update.

Location permission, app name, icons and splash screen are already set up.

## 3. iPhone app

Needs a **Mac with Xcode**.

```bash
npm install
npm run add:ios
npx cap open ios
```

In Xcode:
1. In `App/App/Info.plist` add **Privacy - Location When In Use Usage Description** with:
   "Orbitude uses your location to show the sky and your place in the universe from where you are."
2. **Signing & Capabilities** → choose your team.
3. Run on your iPhone, or **Product → Archive** to upload to App Store Connect.

## Satellite close-ups

The Close-up view loads Esri World Imagery over the internet. For your own testing nothing is needed.
**Before selling the app**, put your own ArcGIS API key in `www/config.js` (steps in STORE.md), then `npx cap sync`.

## After changing the web files

```bash
npx cap sync
```

---

## Selling it on Google Play and the App Store

See **STORE.md** for the full checklist, ready-to-paste store text, and **PRIVACY.md** for a privacy policy you can host.

## Credits and licenses (keep these in the app and store listing)

- Place names: **GeoNames** (geonames.org), CC BY 4.0. Commercial use is allowed with credit; the credit is in the app footer.
- Coastlines and borders: **Natural Earth**, public domain, via world-atlas (ISC).
- 3D engine: **three.js** r128, MIT. Map engine: **Leaflet** 1.9.4, BSD-2-Clause.
- Close-up imagery: **Esri World Imagery** (Esri, Maxar, Earthstar Geographics, and the GIS User Community). Needs your own ArcGIS key for commercial use.
- Orbital elements: NASA JPL (Standish); Moon and Sun formulas: Astronomical Almanac.
