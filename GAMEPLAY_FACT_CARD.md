# Gameplay Fact Card - Echo Path

## Source Evidence
- Core scene: `EchoPathGame/SSEchoPathScene.m`
- Menu scene: `EchoPathGame/MainMenuScene.m`
- Level select: `EchoPathGame/LevelSelectScene.m`
- Settings: `EchoPathGame/SettingsScene.m`
- Bundle configuration: `EchoPathGame/Info.plist`, `project.yml`

## App Identity
- App name: Echo Path
- Bundle ID: com.rosewood.echopath.game
- Product name: EchoPath
- Platform: iPhone only
- Version: 1.0
- Framework: SpriteKit + Objective-C
- Orientation: Portrait only
- iOS deployment target: 15.0+
- Age Rating: 4+

## Core Gameplay Loop
Echo Path is a sonar exploration puzzle set in pitch-black caves. The player controls a glowing light point and must reach the exit on the right side of each cavern. Walls, shadow creatures, and the exit are invisible in the dark and only become visible when revealed by a sonar pulse.

1. **Drag to move** — Touch and drag anywhere to steer the light point at a fixed speed (175 px/sec). The player glow is always visible; everything else is dark.
2. **Tap PULSE to reveal** — Fire a sonar pulse that illuminates all walls, shadow creatures, and the exit for 1.4 seconds (full brightness for the first 0.7s, then fading out).
3. **Avoid shadow creatures** — Monsters patrol the cave randomly. When the player enters their 90px aggro radius, they switch to chase mode. Contact with a monster ends the level in failure.
4. **Find the exit** — Reach the glowing exit portal on the right side of the cave to clear the level.
5. **Manage pulse quota** — Each level provides a limited number of pulses (8 down to 3 as levels increase). Bumping into a wall reveals just that wall for free.

## Game Entities
- **Player** — White light point, radius 12px, always visible. Spawned on the left side of the play area. Moves at 175 px/sec following touch drag.
- **Walls** — Crystal walls, 22px wide, 90–210px tall. Invisible by default. Revealed by pulse or by bumping into them. Block both player and monster movement.
- **Shadow creatures** — Red shadow sprites, radius 16px. Two AI modes: patrol (random direction, 0.45 px/frame, bounces off walls and boundaries) and chase (0.85 px/frame toward player when within 90px aggro radius).
- **Exit portal** — Green portal on the right side, 12px wide x 90px tall. Invisible until revealed by pulse. Touching it clears the level.

## Level Progression
- 50 levels total (`TotalLevelCount = 50`).
- Wall count scales with level: `MIN(7, 2 + (level + 1) / 2)` → 2 walls at level 1, up to 7 walls.
- Monster count scales with level: `MIN(5, 1 + level / 2)` → 1 monster at level 1, up to 5 monsters.
- Pulse quota decreases with level: `MAX(3, 8 - level / 2)` → 8 pulses at level 1, down to 3 pulses.
- Progress saved locally via NSUserDefaults with key `EchoPathUnlockedLevel`. Clearing a level unlocks the next one.
- Exit position is randomized vertically on the right side each level.
- Wall positions are procedurally generated with collision avoidance against player spawn and exit.

## Mechanics
- **Player movement**: Drag-follow with 10px dead zone. Speed 175 px/sec, clamped to play area bounds.
- **Wall collision**: Player is blocked by walls (padded by player radius). Axis-separated sliding allows moving along a wall even if blocked on one axis. Bumping reveals that wall for 1.4s and shows "You bump into a wall — it pulses into view."
- **Monster AI**: Patrol mode moves in a random direction at 0.45 px/frame, bouncing off walls (axis-based reflection) and play area boundaries. Chase mode activates within 90px of the player, moving at 0.85 px/frame directly toward the player.
- **Pulse system**: Costs one pulse. 0.6s cooldown. Fires an expanding ring animation (0.7s duration). Reveals all walls, monsters, and exit for 1.4s. Reveal alpha is 1.0 for the first half (0.7s), then linearly fades to 0 over the second half.
- **Step counter**: Accumulates movement distance; every 26px of travel counts as one step. Displayed in HUD.
- **Win/lose**: Win = player rect intersects exit rect. Lose = player center within (playerRadius + monsterRadius) of any monster center. On level end, the entire scene is fully revealed.

## Monetization
- No advertisements.
- No in-app purchases.
- No account login.
- No subscription.
- No rewarded ads.
- Fully offline single-player experience.

## Data Collection
- No personal information collected.
- No account registration.
- No analytics SDKs.
- No tracking SDKs.
- No advertising SDKs.
- No third-party services.
- Local-only data: unlocked level progress stored in NSUserDefaults (`EchoPathUnlockedLevel`). Stays on device, never transmitted.

## Template Residue Check
- Shared template helpers use `ss_` prefix (`ss_addGeneratedTextureBackdropNamed:accentNames:`, `ss_spriteNamed:fallbackColor:size:`) — standard shared SpriteKit scene template, not visible to end users.
- Inherited template labels `scoreLabel` and `timerLabel` are explicitly hidden in `didMoveToView:` (`self.scoreLabel.hidden = YES; self.timerLabel.hidden = YES;`).
- No `tw_*` resource names found.
- Asset names are Echo-Path-specific: `background_dark_cave`, `sonar_and_shadow_set`, `echo_reveal_fx`, `ep_exit_portal`, `ep_wall_crystal`, `ep_player_light`.
- App Store copy is written specifically for Echo Path's sonar exploration gameplay.

## Debug UI
- `showsFPS` is not enabled (not set on SKView).
- `showsNodeCount` is not enabled (not set on SKView).
- No debug overlay is visible in release builds.
- HUD elements are gameplay-facing only: header title "Echo Path", status bar (Cave / Steps / Walls / Shadows), hint text, PULSE button, and pulse count (remaining/max).
