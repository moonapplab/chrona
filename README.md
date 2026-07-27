# Chrona — installable web app (for iPhone, works on Android too)

This folder is a complete PWA: fullscreen, offline-capable, home-screen icon,
plus the SEO-optimized public website for the app (title/description tags,
Open Graph, structured data, robots.txt, sitemap.xml) and its privacy policy.
It needs to be on an HTTPS site once; GitHub Pages is free.

## Nothing left to fill in — just host it
`privacy.html` already has the real date and support email
(MoonAppsLab@protonmail.com). Every URL in this folder (SEO tags,
`robots.txt`, `sitemap.xml`, and the app's own
`AD_CONFIG_URL`/`PRIVACY_POLICY_URL`) is already set to
`https://moonapplab.github.io/chrona/` — as long as you host this under a
repo named exactly `chrona` on the `moonapplab` account, no URL changes
are needed.

## Host it (about 5 minutes, once)
1. Sign in at github.com as **moonapplab**.
2. Create a new repository, name it exactly `chrona`, set it to Public, click **Create repository**.
3. Click **uploading an existing file**, drag in every file from this folder
   (index.html, privacy.html, manifest.webmanifest, sw.js, ad-config.json,
   robots.txt, sitemap.xml, icon-192.png, icon-512.png, apple-touch-icon.png),
   click **Commit changes**.
4. Repository **Settings → Pages** → under "Branch" choose `main` and `/ (root)` → **Save**.
5. After ~1 minute your app is live at: **https://moonapplab.github.io/chrona/**

## Install on iPhone
Open the URL in **Safari** → Share button → **Add to Home Screen** → Add.
The Chrona icon appears on the home screen and opens fullscreen, works offline.

## Install on Android (alternative to the APK)
Open the URL in **Chrome** → menu (⋮) → **Add to Home screen** / **Install app**.

## Updating
Run `powershell -File build.ps1` after editing `..\chrona-age-calculator\index.html`
— it rebuilds `index.html` with the SEO/PWA tags and automatically bumps the
service worker's cache version, so installed PWAs fetch the new build instead
of a stale cached copy. Then upload the changed files to your GitHub repo.

## Controlling ads in the Android app (no app update needed)
`ad-config.json` in this repo is fetched by the installed Android app on every
launch. Edit it on github.com (pencil icon) to change ads instantly:
- `adsEnabled`: false hides all ads
- `banner` / `interstitial`: your AdMob ad unit IDs (currently Google's test IDs)
- `interstitialEvery`: show a fullscreen ad after every Nth calculation (0 = never)
- `isTesting`: set false when using real ad unit IDs

Note: the AdMob **App ID** inside the APK is separate — switching from the test
App ID to your real one requires one rebuild of the app (see chrona-app README).
The ad UNIT ids above never require rebuilds.
