# Space Blaster – Build & Play Store Guide

An arcade space shooter (HTML5) wrapped as an Android app with Capacitor.

## 1. Test the game right now
Open `www/index.html` in Chrome (phone or desktop). Drag to move; the ship fires automatically.

## 2. One-time setup (on your computer)
- Install **Node.js** (LTS) and **Android Studio**
- Install a **JDK 17+** (Android Studio bundles one)

## 3. Build the Android project
```bash
cd space-blaster
npm install
npx cap add android
npx cap sync android
npx cap open android
```
Before this, edit `appId` in `capacitor.config.json` to something unique, e.g. `com.alok.spaceblaster`. **It cannot be changed after you publish.**

## 4. Add app icon
In Android Studio: right-click `app/res` → New → Image Asset → choose a 512×512 icon.

## 5. Create a signed release bundle (.aab)
Android Studio → **Build → Generate Signed App Bundle / APK → Android App Bundle**
- Create a new keystore. **Back it up safely** (losing it means you can't update the app).
- Choose **release** and finish. The `.aab` is in `android/app/release/`.

## 6. Play Console
1. Create a developer account at play.google.com/console (one-time US$25 fee, ID verification required).
2. **Create app** → name, language, Game, Free.
3. Fill the required sections:
   - **Privacy policy URL** (required, even for simple games; free generators and GitHub Pages work)
   - **Data safety** form (this game collects nothing; say so unless you add ads)
   - **Content rating** questionnaire (mild cartoon violence)
   - **Target audience** (choose 13+ to avoid extra Families-policy requirements)
   - **Ads declaration** (No, unless you add AdMob)
4. **Store listing**: short description (80 chars), full description, 512×512 icon, 1024×500 feature graphic, at least 2 phone screenshots.
5. **Testing requirement**: new personal accounts must run a **closed test with 12+ testers for 14 days** before production access. Start this early.
6. Upload the `.aab` to a closed test → then apply for production.

## 7. Ideas to earn money later
- Google AdMob rewarded ads ("watch ad for an extra life")
- Remove-ads in-app purchase
- New ship skins, more boss types, online leaderboard

## Game tuning (in `www/index.html`)
- Fire rate: `fireT = .22`
- Enemies per level: `kills >= level*12`
- Lives: `lives = 3`
