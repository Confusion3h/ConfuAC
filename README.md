# ConfuAC - Lightweight Anti-Cheat Plugin

<p align="center">
  <img src="https://img.shields.io/badge/Minecraft-1.8.8+-brightgreen" alt="Minecraft Version">
  <img src="https://img.shields.io/badge/Java-8+-blue" alt="Java Version">
  <img src="https://img.shields.io/badge/Platform-Spigot%20%7C%20Velocity%20%7C%20BungeeCord-orange" alt="Platforms">
  <img src="https://img.shields.io/badge/License-MIT-yellow" alt="License">
</p>

**ConfuAC** is a lightweight, cross-platform anti-cheat plugin for Minecraft servers. It provides real-time cheat detection with cross-server alert forwarding, perfect for network setups.

---

## ✨ Features

### 🔍 Detection Modules

| Module | Description |
|--------|-------------|
| **Autoclicker** | CPS monitoring with rolling window analysis (left & right click) |
| **Reach** | Detects hits beyond vanilla reach (3.0 blocks) |
| **Speed** | Monitors horizontal movement for speed hacks |
| **Fly** | Tracks air ticks for unauthorized flight |
| **Scaffold** | Block placement rate monitoring |
| **Velocity/Anti-KB** | Knockback percentage measurement |
| **Aim-Snap** | Sudden camera rotation detection (aimbot/killaura) |
| **Chat** | Spam, caps, and profanity filtering |

### 🌐 Cross-Server Support

- Real-time alert forwarding via BungeeCord/Velocity
- Staff receive alerts from all connected servers
- Centralized logging on proxy

### 🔐 Permission System

- Full **LuckPerms** integration
- OP users have full access by default
- Create custom staff roles (helper, mod, admin)

### 📝 Built-in Punishments

- Mute/Ban commands (permanent & temporary)
- Persistent storage (JSON)
- Auto-punishment on repeated flags

---

## 📦 Installation

1. Download the latest release
2. Place the appropriate JAR in your `plugins/` folder:
   - `confuac-spigot-1.0.jar` for Spigot/Paper servers
   - `confuac-velocity-1.0.jar` for Velocity proxy
   - `confuac-bungee-1.0.jar` for BungeeCord proxy
3. Restart your server
4. Configure in `plugins/ConfuAC/config.yml`

---

## 🔧 Configuration

### Default Thresholds (config.yml)

```yaml
checks:
  autoclicker_min_cps: 18      # CPS threshold
  reach_max_blocks: 3.0         # Vanilla reach
  speed_max_bps: 5.5            # Blocks per second
  fly_max_air_ticks: 25         # Air ticks before flag
  scaffold_max_bps: 12.0        # Blocks placed per second
  velocity_min_kb_pct: 40.0     # Minimum KB percentage
```

### Enable/Disable Checks

```yaml
checks:
  enabled:
    autoclicker_left: true
    autoclicker_right: true
    reach: true
    speed: true
    fly: true
    scaffold: true
    velocity: true
    aim_snap: true
```

---

## 🔑 Permissions

| Permission | Description | Default |
|------------|-------------|---------|
| `confuac.alerts` | Receive anti-cheat alerts | OP |
| `confuac.admin` | Access admin commands | OP |
| `confuac.bypass` | Bypass all checks | OP |
| `confuac.mute` | Mute players | OP |
| `confuac.tempmute` | Temporary mute | OP |
| `confuac.ban` | Ban players | OP |
| `confuac.tempban` | Temporary ban | OP |
| `confuac.unmute` | Remove mute | OP |
| `confuac.unban` | Remove ban | OP |
| `confuac.logs` | View player logs | OP |
| `confuac.ss` | Screenshare commands | OP |
| `confuac.*` | All permissions | OP |

---

## 💻 Commands

### Spigot Commands

| Command | Description |
|---------|-------------|
| `/alerts` | Toggle alert notifications |
| `/confuac reload` | Reload configuration |
| `/confuac info` | Show plugin info |
| `/mute <player> <reason>` | Permanent mute |
| `/tempmute <player> <time> <reason>` | Temporary mute |
| `/unmute <player>` | Remove mute |
| `/ban <player> <reason>` | Permanent ban |
| `/tempban <player> <time> <reason>` | Temporary ban |
| `/unban <player>` | Remove ban |
| `/logs <player>` | View player flags |

### Proxy Commands (Velocity/BungeeCord)

| Command | Description |
|---------|-------------|
| `/valerts` or `/balerts` | Toggle cross-server alerts |
| `/confuacproxy info` | Show proxy statistics |
| `/confuacproxy reload` | Reload proxy config |

---

## 🎯 LuckPerms Integration

Create custom staff roles without giving OP:

```bash
# Helper role (alerts only)
/lp creategroup helper
/lp group helper permission set confuac.alerts true

# Moderator role (alerts + punishments)
/lp creategroup mod
/lp group mod permission set confuac.alerts true
/lp group mod permission set confuac.mute true
/lp group mod permission set confuac.tempmute true
/lp group mod permission set confuac.unmute true
/lp group mod permission set confuac.logs true

# Admin role (full access)
/lp creategroup admin
/lp group admin permission set confuac.* true

# Assign to player
/lp user <player> parent set <group>
```

---

## 📋 Requirements

- **Java**: 8+ (17 recommended)
- **Server**: Spigot/Paper 1.8.8+ or compatible fork
- **Optional**: Velocity 3.0+ or BungeeCord for cross-server
- **Optional**: LuckPerms for advanced permissions

---

## 🏗️ Building from Source

```bash
git clone https://github.com/yourusername/confuac.git
cd confuac
mvn clean package
```

JARs will be in:

- `spigot/target/confuac-spigot-1.0.jar`
- `velocity/target/confuac-velocity-1.0.jar`
- `bungee/target/confuac-bungee-1.0.jar`

---

## 📄 License

This project is licensed under the MIT License.

---

## 🤝 Contributing

Contributions are welcome! Please open an issue or pull request.

---

<p align="center">Made with ❤️ by Confusion3h</p>
