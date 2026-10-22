# CAPS Physics Tutor — App Store Ready

This package turns the web tutor into a native iOS and Android app that can be submitted to the **Apple App Store** and **Google Play Store**.

## Folder Structure

```
appstore/
├── capacitor.config.json   ← Capacitor config
├── package.json            ← Dependencies
├── manifest.json           ← PWA manifest
├── service-worker.js       ← Offline support
├── www/                    ← Put the final HTML here (rename to index.html)
└── README.md               ← This file
```

## Quick Start (Local Development)

1. Copy the HTML app into the web folder:
   ```bash
   mkdir -p www
   cp ../caps_physics_tutor.html www/index.html
   ```

2. Install Capacitor:
   ```bash
   npm install
   npx cap init "CAPS Physics Tutor" "za.caps.physicstutor" --web-dir=www
   ```

3. Add platforms:
   ```bash
   npx cap add ios
   npx cap add android
   ```

4. Sync and open:
   ```bash
   npx cap sync
   npx cap open ios      # Opens Xcode
   npx cap open android  # Opens Android Studio
   ```

## Preparing for the App Store

### 1. Required Assets
- **App Icon**: 1024×1024 PNG (no transparency for Apple)
- **Splash Screen**: 2732×2732 (or use Capacitor splash generator)
- Place icons in `www/` and update `manifest.json` paths.

### 2. Apple App Store (iOS)
1. Enroll in the **Apple Developer Program** ($99/year).
2. In Xcode:
   - Set Bundle ID: `za.caps.physicstutor`
   - Add signing team
   - Set deployment target (iOS 14+)
3. Create App Store Connect listing:
   - Name: CAPS Physics Tutor
   - Subtitle: Grade 10–12 Physics Tutor
   - Category: Education
   - Age Rating: 4+
   - Privacy Policy URL (required)
   - Screenshots (6.7", 6.5", 5.5" iPhones + iPad)
4. Archive → Upload → Submit for Review.

### 3. Google Play Store (Android)
1. Create a **Google Play Developer** account ($25 one-time).
2. In Android Studio:
   - Generate a signed AAB (Android App Bundle)
   - Version code / version name
3. In Play Console:
   - Create app
   - Content rating questionnaire
   - Privacy policy
   - Store listing (screenshots, feature graphic 1024×500)
   - Upload AAB and submit for review.

### 4. Recommended Production Changes
- Move API key handling to a secure backend (never ship keys in the app).
- Add in-app purchases or subscription (RevenueCat recommended) if selling access.
- Add analytics (e.g. Firebase) and crash reporting.
- Implement proper user accounts if you want multi-device progress.
- Add Afrikaans language toggle.
- Expand practice questions with real NSC past papers (with proper licensing).

### 5. Monetization Options
- Free with limited daily questions + subscription
- One-time purchase
- School / bulk licensing
- Freemium (demo mode free, full AI requires subscription)

## Privacy & Compliance
- Add a Privacy Policy (required by both stores).
- Declare data collection (chat logs, progress) in App Store Connect and Play Console.
- For students under 13: follow COPPA / POPIA requirements (South Africa).

## Next Commands

```bash
cd appstore
npm install
npx cap add ios
npx cap add android
npx cap sync
```

You now have a store-ready hybrid app. Open the native projects and follow the platform-specific submission guides above.
