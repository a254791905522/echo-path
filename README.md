# Echo Path Publish Package

This folder contains App Store review copy, privacy page, support page, and standard screenshots for Echo Path.

## App Information
- **App Name**: Echo Path
- **Bundle ID**: com.rosewood.echopath.game
- **Version**: 1.0
- **Platform**: iOS (iPhone only), iOS 15.0+
- **Framework**: SpriteKit + Objective-C
- **Orientation**: Portrait only
- **Age Rating**: 4+
- **Network**: Fully offline, no ads, no IAP, no analytics, no tracking

## Device Support
- iPhone only (`TARGETED_DEVICE_FAMILY: '1'`)
- Requires iOS 15.0 or later
- Portrait orientation only

## Gameplay Summary
Echo Path is a sonar exploration puzzle set in pitch-black caves. The player controls a glowing light point and must reach the exit on the right side of each cavern. Walls, shadow creatures, and the exit are invisible in the dark — the only way to see them is to fire a sonar pulse that briefly illuminates the cave.

- Drag to move the light point through the dark
- Tap PULSE to reveal walls, shadow creatures, and the exit for 1.4 seconds
- Avoid shadow creatures that patrol and chase when you get close
- Bump into walls to reveal them locally without spending a pulse
- Manage a limited pulse quota (3–8 per level)
- 50 progressively challenging levels with increasing walls and monsters

## Screenshot Sets
- `screenshots_65/`: 1284x2778 screenshots (iPhone 6.5")
  - 01_main_menu.png
  - 02_pulse_reveal.png
  - 03_navigate_dark.png
  - 04_avoid_shadows.png
  - 05_level_clear.png
- `screenshots_55/`: 1242x2208 screenshots (iPhone 5.5")
  - 01_main_menu.png
  - 02_pulse_reveal.png
  - 03_navigate_dark.png
  - 04_avoid_shadows.png
  - 05_level_clear.png

## Release Files
- `index.html`: public support page with embedded screenshots
- `privacy.html`: privacy policy for App Store Connect
- `keywords.txt`: App Store keywords (under 100 characters)
- `GAMEPLAY_FACT_CARD.md`: source-grounded gameplay facts extracted from `SSEchoPathScene.m`
- `PUBLISH_CHECKLIST.md`: release and archive verification checklist
- `appstore-review-text.html`: App Store Connect copy fields with copy buttons
- `README.md`: this file
- `.gitignore`: Vercel deployment ignore file

## URLs
- Support URL: https://echo-path.vercel.app/
- Privacy Policy URL: https://echo-path.vercel.app/privacy.html

## Build
Final upload should be done from Xcode using `/Users/wxj/888ios/batch-game/EchoPath-ReleaseProject/EchoPath.xcodeproj`.
