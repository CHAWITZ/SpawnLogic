# SpawnLogic

Smart spawn system for Minecraft servers – external download, All Rights Reserved.

---

## 📌 Overview

**SpawnLogic** provides a controlled, safe, and fair spawn experience for players joining your Minecraft server.  
Designed for servers that want structured spawn placement, reduced spawn chaos, and configurable player onboarding.

This plugin is **closed-source** and distributed as a compiled `.jar` only.  
Developed and maintained by **CHAWITZ Development**.

---

## ✅ Features

- Smart **ring-based spawn placement system**
- Safe-location scanning with fallback logic
- Handles **new players, returning players, respawns, and legacy players**
- Whitelist bypass mode for specific users
- Customizable **Title / Subtitle / Actionbar** messages per player type
- Admin commands for spawn management
- Permission-based access control
- Simple configuration with clear inline comments

---

## 🧩 Compatibility

| Item | Version |
|-------|-----------|
| **Minecraft** | **1.21+** |
| **Server Software** | Paper, Purpur (recommended), Spigot |

> Not tested on older versions or forks outside the above list.

---

## 📥 Installation

1. Download the latest release from GitHub Releases:  
   **(External download only)**  
   https://github.com/CHAWITZ/SpawnLogic/releases/latest

2. Extract the ZIP file.

3. Place `SpawnLogic.jar` into your server’s `/plugins` folder.

4. Start the server.  
   The configuration file will be generated automatically.

5. Adjust settings in the config if needed, then reload/restart.

---

## 🛠 Commands

| Command | Description | Permission | Default |
|---------|----------------|--------------|-----------|
| `/resetspawn <player>` | Reset a player's spawn so they receive a new one next join/respawn | `spawnlogic.reset` | OP |
| `/spawninfo` | Display the player’s stored spawn, ring “zone”, and world | `spawnlogic.info` | Everyone |

---

## 🔐 Permissions

| Permission | Description | Default |
|-------------|----------------|-----------|
| `spawnlogic.*` | Access to all SpawnLogic commands | OP |
| `spawnlogic.reset` | Allows admin to reset other players' spawns | OP |
| `spawnlogic.info` | Player can view their own spawn information | TRUE |

---

## ⚙️ Configuration Overview

A configuration file will generate on first startup with explanatory comments.  
Key areas include:

- **Settings** — legacy handling and behavior control  
- **Rings** — radius values controlling spawn distribution  
- **Spawn Rules** — minimum/maximum distance between player spawns  
- **Archetypes** — messaging rules for:

  - New Players  
  - Returning Players  
  - Plugin Respawns  
  - Legacy Join/Legacy Respawn  
  - Whitelisted  

> All messages support Titles, Subtitles, and Actionbar — fully toggleable.

---

## 🔒 License & Usage

© 2025 CHAWITZ Development. All Rights Reserved.

This plugin is distributed as a compiled binary only.  
You may use it on your servers, but the following **are strictly prohibited**:

- Redistribution or re-uploading of the plugin
- Sharing the `.jar` or ZIP file publicly
- Reselling or monetizing the plugin
- Modifying, decompiling, or reverse-engineering the plugin

Full license terms are provided in `LICENSE.md`.

---

## 🧑‍💼 Support

For inquiries, issue reporting, or commercial use requests, please contact:  
**CHAWITZ Development**

(Private support channel to be provided)

---

