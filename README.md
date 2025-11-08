# SpawnLogic

**Lightweight, lore-forward Minecraft spawn manager for Paper/Spigot servers.**  
Handles archetype-aware spawns (`NewPlayer`, `ReturningPlayer`, `Whitelisted`, `Legacy`, etc.), safe random spawn placement with ring logic, live whitelist transition countdowns (10…9…8…), and configurable post-countdown behavior.

Built for maintainability, copy-safe code structure, and expressive in-game messaging.

---

## ✨ Key Features

- **Archetype system** with the following types:
  - `NewPlayer`, `ReturningPlayer`, `ReturningToLastLocation`, `RespawnedPlugin`, `Legacy`, `Whitelisted`
- **Live whitelist change detection** while players are online
  - Configurable countdown with per-second feedback (chat or actionbar)
- **Configurable post-countdown behavior**
  - Choose archetype to apply after whitelist add/remove
  - Optional teleport per flow
- **Safe spawn placement**
  - Forbidden + habitat ring logic
  - Minimum distance between players
- **Rejoin support**
  - Restore last location on join (optional one-time clear)
- **Centralized messaging per archetype**
  - Titles, subtitles, actionbar — easily themed and localized
- **Admin utilities**
  - Force archetype, timers, debug flags

---

## 📦 Installation

1. Build using Maven or Gradle targeting **Paper/Spigot 1.21+**
2. Place the compiled JAR in your server `/plugins/` folder
3. Start the server to generate default config
4. Edit `config.yml` (see below)
5. Restart or reload the plugin

---

## 🚀 Basic Usage

- On join, players are automatically classified as `NewPlayer`, `ReturningPlayer`, `Legacy` or `Whitelisted` based on stored data and vanilla playerdata.
- Adding/removing a player from the **whitelist** triggers a live countdown.
- Countdown displays numeric feedback each second (`10…9…8…1`)
- At the end of countdown, the configured archetype is applied and messages are shown according to `Archetypes.yml`.

---

## ⚙️ Configuration (Example)

Add/verify these keys in your `config.yml`. The plugin ships with defaults.

```yaml
Settings:
  legacy-empowered: false
  whitelist-reset-delay-seconds: 10
  after-whitelist-archetype: Whitelisted
  after-whitelist-teleport: false
  after-unwhitelist-archetype: NewPlayer
  after-unwhitelist-teleport: true

rings:
  forbidden-radius: 256
  habitat-radius: 512
  expansion-step: 256

spawn:
  min-distance-between-players: 128
  max-distance-between-players: 512

rejoin:
  restore-last-location: true
  clear-after-use: true

debug:
  save-load-stacktraces: false
Archetypes
yaml
Copy code
Archetypes:
  NewPlayer:
    Enabled: true
    Title:
      Enabled: true
      Value: "§6§lAwakened Wanderer"
    Subtitle:
      Enabled: true
      Options:
        - "§fYou step into a world already turning."
    Actionbar:
      Enabled: true
      Options:
        - "§aYour place was prepared long before you arrived."
Notes

whitelist-reset-delay-seconds controls countdown (default 10)

after-* lets servers choose new archetype after countdowns

after-*-teleport toggles teleport for each flow

🛠 Commands
Add the following to plugin.yml:

php-template
Copy code
/spawnlogic forcetype <player> <archetype> [teleport]
Force-apply an archetype to an online player (clears countdown).

Recommended permission:
spawnlogic.forcetype → default: OP

bash
Copy code
/spawnlogic reload
Reloads config (includes post-countdown settings and timers).

Example:

bash
Copy code
/spawnlogic forcetype Notch NewPlayer teleport
🧩 Developer Notes
Polling interval defaults to 5s to balance performance and responsiveness
(adjust in SpawnHandler constructor)

Countdown messages are chat by default — enable actionbar for cleaner UX

Persistent state is stored under spawns.<uuid> keys:

type, lastKnownWhitelist, initialLocation

whitelistCountdownActive, unwhitelistCountdownActive, etc.

ForceSetArchetype centralizes:

State storage

Initial spawn saving

Messaging

Optional teleport

Player yaw/pitch preserved when teleporting using safe spawn results

🧯 Troubleshooting
Issue	Check
Countdowns never start	Ensure spawns.<uuid>.lastKnownWhitelist initializes (use force command if needed)
Players not detected	Check polling frequency and plugin’s data access permissions
Unexpected behavior / data issues	Enable debug.save-load-stacktraces: true temporarily

🤝 Contributing
Pull requests welcome.

Guidelines:

Fork → create feature branch per change

Small, focused PRs

Include tests where possible

Update README/config examples when relevant

Maintain copy-safe, split-file structure

📜 License & Credits
SpawnLogic — © 2025 CHAWITZ Development. All Rights Reserved.
Lead author: CHAWITZ (Chawit Chandabimba)

