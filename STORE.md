# Selling Orbitude: checklist

## Accounts and costs

| | Google Play | Apple App Store |
| --- | --- | --- |
| Developer account | US$25 once | US$99 per year |
| Computer needed | Any (Windows, Mac, Linux) | Mac with Xcode |
| Store commission on sales | 15% on your first US$1M per year | 15% with the Small Business Program (apply for it), otherwise 30% |
| Before you can sell | Payments profile + tax info in Play Console | Paid Apps Agreement + bank + tax forms in App Store Connect |
| Review time | Usually hours to a few days | Usually 1–3 days |

## Google Play: extra rule for new personal accounts

Personal developer accounts created after 13 November 2023 must run a **closed test with at least 12 testers,
opted in for 14 days in a row**, before the app can go public. Ask friends and family to join early.
(Organization accounts registered with a D-U-N-S number are exempt.)

You will also fill in: the **Data safety** form (see below), the **content rating** questionnaire (Everyone),
the target audience, and a link to your **privacy policy**.

## Apple: things reviewers check

- **Minimum functionality (guideline 4.2):** Apple rejects apps that are "just a website". Orbitude bundles all its
  data and 3D engine, works offline, and uses GPS, which helps. In the review notes, say it works fully offline and
  show the four 3D views.
- **Location wording:** the Info.plist text must say clearly why location is used (text is in README.md).
- **Privacy "nutrition label":** choose **Data Not Collected** (location stays on the device).

## Satellite close-ups: imagery licence (do this before selling)

The Close-up view shows Esri World Imagery (Esri, Maxar, Earthstar Geographics). Without a key, the app uses
Esri's public tile service, which is fine for trying it yourself but **not for a paid app**.

1. Create a free **ArcGIS Location Platform** account at https://location.arcgis.com
2. Create an **API key** with the **Basemaps** privilege.
3. Paste it into `www/config.js` as `imageryKey: "..."`, then run `npx cap sync`.
4. Keep the imagery credit visible (the app already shows it in the corner of the Close-up view).

The free tier includes a monthly allowance of basemap tiles; heavy use is billed per tile beyond that.
Check Esri's current pricing and terms when you sign up, and set a usage limit in your ArcGIS account.
Other satellite providers (Mapbox, MapTiler) also work: change the tile address in `www/index.html` (`esri(...)`).

**What people will and won't see:** in most cities the sharpest photos are about 30 cm per pixel: buildings, roads,
cars, boats and trees are clear, people are a dot or two. The photos are typically months to a few years old, not live.
Describe it that way in your store listing so reviewers and buyers aren't misled.

## Data safety / privacy answers

Orbitude does not collect data. Location is read on the device only to calculate the sky and is saved only in the
app's local storage. In the Close-up view the app downloads map images from Esri, which (like any website) sees the
device's IP address and which map area is requested. There are no accounts, ads, analytics or tracking.
- Google Data safety: "No data collected", "No data shared".
- Apple App Privacy: "Data Not Collected".
Host PRIVACY.md somewhere public (for example on the same Netlify site) and use that link in both stores.

## Pricing advice

Free astronomy apps (planetarium and sky-map apps) are strong competition, so a high upfront price will sell slowly.
Common options:
- **Low price:** US$1.99–2.99 one-off.
- **Free with a one-time unlock** (for example, time travel and the Milky Way view): usually earns more,
  but needs in-app purchase code added to the app.

## Before you upload

- [ ] Search both stores for "Orbitude" again to make sure nobody has taken the name.
- [ ] Confirm the app ID in `capacitor.config.json` (permanent after first upload).
- [ ] Take screenshots: phone (and tablet if you support it) of the Earth, Your sky, Solar System and Milky Way views.
- [ ] Feature graphic for Google Play: 1024×500.
- [ ] Privacy policy hosted at a public link.
- [ ] Signed release build (Android App Bundle / Xcode archive).

## Ready-to-paste store text

**Name:** Orbitude

**Subtitle / short description (max 30 / 80 characters):**
Your place in the universe, live
See where you are in the universe right now: Earth, sky, planets and galaxy in 3D.

**Full description:**

Where are you in the universe, right now?

Orbitude shows your exact place in the cosmos, calculated live from the clock and your location.

• A 3D Earth lit by the real Sun, with day and night, sunrise and sunset, and city lights on the night side
• Your sky: the Sun, Moon and every planet placed exactly where they are above your horizon, with the Moon's real phase
• When the Sun, Moon and planets next rise and set where you are, and how far away each one is
• The solar system in 3D with every planet in its real position
• The Milky Way in 3D, showing where our Sun sits in its spiral arm
• Live counters showing how far you have travelled through space since you opened the app
• Speed up time to watch day and night move and the planets orbit
• Close-up: zoom from space down to your street in satellite photos, sharp enough to see buildings, cars and boats
• Search over 10,000 cities and every state and province, or use GPS
• Everything except Close-up works offline. No account, no ads, no tracking.

Planet positions use NASA JPL orbital data. Place names from GeoNames (CC BY 4.0).

**Category:** Education (or Reference)
**Content rating:** Everyone / 4+
**Keywords (Apple, 100 characters):** astronomy,planets,sky,space,earth,moon,sun,solar system,galaxy,stars,location,universe
