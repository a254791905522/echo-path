# Publish Checklist - Echo Path

## Identity
- [x] App name: Echo Path
- [x] Bundle ID: com.rosewood.echopath.game
- [x] Bundle ID contains `rosewood`.
- [x] PRODUCT_NAME: EchoPath
- [x] CFBundleDisplayName / CFBundleName: Echo Path
- [x] Version: 1.0

## Source-Grounded Gameplay
- [x] Gameplay facts extracted from `SSEchoPathScene.m`.
- [x] Metadata describes sonar pulse reveal, dark cave navigation, and shadow creature avoidance.
- [x] Metadata mentions pulse quota, 50 levels, and exit-reaching win condition.
- [x] Metadata avoids generic puzzle claims not supported by code.

## Template Residue / 4.3 Spam Risk
- [x] No `tw_*` resource names found.
- [x] Inherited template labels (`scoreLabel`, `timerLabel`) are explicitly hidden.
- [x] No visible FPS/node debug overlay is enabled.
- [x] Asset names are Echo-Path-specific (`ep_*`, `echo_reveal_fx`, `background_dark_cave`).
- [x] App Store copy is written for this game, not copied from a previous title.

## iPhone Only
- [x] `TARGETED_DEVICE_FAMILY: '1'` in project-level settings.
- [x] `TARGETED_DEVICE_FAMILY: '1'` in target-level settings.
- [x] Final archive must show `UIDeviceFamily = (1)`.
- [x] Portrait orientation only is acceptable because the final app is iPhone-only.

## App Icon
- [x] `ASSETCATALOG_COMPILER_APPICON_NAME = AppIcon`.
- [x] `CFBundleIconName = AppIcon`.
- [x] Required icon PNG files exist: 120x120, 180x180, 152x152, 167x167, 1024x1024.
- [x] App icons are opaque with `hasAlpha: no`.
- [x] Re-check final archive for `Assets.car` and emitted `AppIcon*.png` after archive.

## Launch Screen
- [x] `UILaunchStoryboardName = LaunchScreen`.
- [x] `Base.lproj/LaunchScreen.storyboard` exists.
- [x] Re-check final archive for `Base.lproj/LaunchScreen.storyboardc`.

## App Store Metadata
- [x] `appstore-review-text.html` generated with textarea fields.
- [x] `keywords.txt` generated (under 100 characters).
- [x] `README.md` generated.
- [x] `privacy.html` generated.
- [x] `index.html` generated with screenshots and section structure.

## Screenshots
- [x] 5 screenshots generated for 1284x2778 (screenshots_65/).
- [x] 5 screenshots generated for 1242x2208 (screenshots_55/).
- [x] Screenshots show main menu, pulse reveal, dark navigation, shadow avoidance, and level clear.
- [x] Screenshot filenames: 01_main_menu.png, 02_pulse_reveal.png, 03_navigate_dark.png, 04_avoid_shadows.png, 05_level_clear.png.

## Archive Verification
Run from `/Users/wxj/888ios/batch-game`:

```bash
xcodebuild \
  -project EchoPath-ReleaseProject/EchoPath.xcodeproj \
  -scheme EchoPath \
  -configuration Release \
  -sdk iphoneos \
  -archivePath /Users/wxj/888ios/batch-game/EchoPath-Release/EchoPath.xcarchive \
  CODE_SIGNING_ALLOWED=NO \
  archive
```

Then inspect:

```bash
APP=/Users/wxj/888ios/batch-game/EchoPath-Release/EchoPath.xcarchive/Products/Applications/EchoPath.app
/usr/libexec/PlistBuddy -c 'Print :CFBundleIdentifier' "$APP/Info.plist"
/usr/libexec/PlistBuddy -c 'Print :CFBundleDisplayName' "$APP/Info.plist"
/usr/libexec/PlistBuddy -c 'Print :UIDeviceFamily' "$APP/Info.plist"
find "$APP" -maxdepth 3 \( -name 'Assets.car' -o -name 'AppIcon*.png' -o -name 'LaunchScreen.storyboardc' \) -print | sort
```

## Privacy / Export Compliance
- [x] App is fully offline with no data collection.
- [x] No account login required.
- [x] No ads, no IAP, no analytics, no tracking.
- [x] `ITSAppUsesNonExemptEncryption = false` (no custom encryption).
- [x] Privacy Policy URL configured: https://echo-path.vercel.app/privacy.html

## Deployment
- [x] Commit and push publish site to GitHub.
- [x] Deploy to Vercel.
- [x] Verify live URL: https://echo-path.vercel.app/
- [x] Verify privacy URL: https://echo-path.vercel.app/privacy.html

## Review Submission
- [x] App Store Connect app record created with Bundle ID com.rosewood.echopath.game.
- [x] All metadata fields populated in `appstore-review-text.html`.
- [x] Promotional text under 170 characters.
- [x] Review notes mention offline, no accounts, no ads, no IAP, and ITSAppUsesNonExemptEncryption=false.
- [x] Screenshots uploaded for required device sizes.
- [x] Age rating questionnaire completed (4+).
- [ ] Submit for App Review.
