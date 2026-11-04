# GuestControlMod

A Fabric server mod for **Minecraft 26.3** that automatically manages guest players with Spectator mode enforcement, a timed BossBar, auto-kick, and Discord webhook integration.

**Developed by GoodDoggoLuna**

---

## Features

### 🔒 Automatic Guest System
- Every player who joins is automatically set as a **guest**
- Guests are forced into **Spectator mode** and cannot interact with the world
- Admins can remove guest status to grant full access

### 🚫 Interaction Restrictions
Guests are blocked from:
- Breaking blocks
- Placing blocks (right-click)
- Using items

A **red chat message** is sent when an action is blocked.

### 📊 BossBar with Countdown Timer
- Displays a **red BossBar** with the text: `Developed by GoodDoggoLuna | Guest Timer: MM:SS`
- Progress bar drains over the 1-hour session
- Each player sees their personal countdown above their hotbar

### ⏱️ Auto-Kick (1 Hour)
- Guests are automatically **kicked after 1 hour**
- Disconnect message: *"Your 1-hour guest session has expired. Contact an admin for access."*
- Timer resets if the player reconnects

### 💬 Discord Webhook (`/request`)
- Any player can run `/request <message>` to send a message to server admins via Discord
- Sends an async HTTP POST to your configured Discord webhook URL
- Format: `**Player [name] requested:** [message]`

### 🛡️ Admin Commands
| Command | Permission | Description |
|---|---|---|
| `/guest add <player>` | OP Level 2 | Manually set a player as guest |
| `/guest remove <player>` | OP Level 2 | Remove guest status, restore Survival mode |
| `/request <message>` | Everyone | Send a request to admins via Discord |

---

## Installation

### Requirements
- Minecraft **26.3**
- [Fabric Loader](https://fabricmc.net/use/installer/) **0.20.1+**
- [Fabric API](https://modrinth.com/mod/fabric-api/versions?g=26.3) **0.165.0+26.3**

### Steps
1. Download the latest `GuestControlMod-x.x.x.jar` from [Releases](../../releases)
2. Place it in your server's `mods/` folder alongside Fabric API
3. Start the server

---

## Configuration

### Discord Webhook URL
Edit the `DISCORD_WEBHOOK_URL` constant in `GuestControlMod.java` before building:

```java
private static final String DISCORD_WEBHOOK_URL =
        "https://discord.com/api/webhooks/YOUR_WEBHOOK_URL_HERE";
```

Replace `YOUR_WEBHOOK_URL_HERE` with your actual [Discord webhook URL](https://support.discord.com/hc/en-us/articles/228383668-Intro-to-Webhooks).

### Kick Timer
The default auto-kick timer is **1 hour** (72,000 ticks). To change it, edit:

```java
private static final long KICK_TIMER_TICKS = 60L * 60L * 20L; // 1 hour
```

---

## Building from Source

### Requirements
- **JDK 25+** (tested with JDK 27)

### Build
```bash
./gradlew build
```

The compiled JAR will be in `build/libs/GuestControlMod-x.x.x.jar`.

---

## Tech Stack

| Component | Version |
|---|---|
| Minecraft | 26.3 |
| Fabric Loader | 0.20.1 |
| Fabric Loom | 1.19-SNAPSHOT |
| Fabric API | 0.165.0+26.3 |
| Java | 25+ |

---

## License

This project is licensed under the [MIT License](LICENSE).
