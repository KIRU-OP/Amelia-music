# ⚙️ KanhaMusic — Configuration Guide

Everything you need to configure and run **KanhaMusic**. All variables below can be set either as **environment variables** or inside a `.env` file placed in the project root.

> 💡 **Naming is flexible.** For every variable listed here, the loader accepts `UPPER_CASE`, `lower_case`, or `NoUnderscores` — e.g. `API_ID`, `api_id`, and `APIID` all work the same way.

---

## 📑 Table of Contents

1. [Quick Start](#-quick-start)
2. [Required Variables](#-required-variables)
3. [Assistant Configuration](#-assistant-configuration)
4. [Ownership](#-ownership)
5. [External APIs (Optional)](#-external-apis-optional)
6. [Bot Behavior & Limits](#️-bot-behavior--limits)
7. [Customization](#-customization)
8. [System Settings](#️-system-settings)
9. [Notes](#-notes)

---

## 🚀 Quick Start

Create a `.env` file in your project root with at least the required variables filled in:

```env
API_ID=1234567
API_HASH=your_api_hash_here
TOKEN=your_bot_token_here
MONGO_DB_URI=mongodb+srv://user:pass@cluster.mongodb.net
STRING_SESSIONS=your_session_string_here
```

Then restart the bot for changes to take effect. Everything else below is optional and comes with sensible defaults.

---

## 🔴 Required Variables

The bot **will not start** unless these are set.

| Variable | Type | Description |
| :--- | :--- | :--- |
| `API_ID` | `int32` | Your Telegram API ID from [my.telegram.org](https://my.telegram.org). |
| `API_HASH` | `string` | Your Telegram API Hash from [my.telegram.org](https://my.telegram.org). |
| `TOKEN` | `string` | Your Telegram Bot Token from [@BotFather](https://t.me/BotFather). Also accepts `BOT_TOKEN`. |
| `MONGO_DB_URI` | `string` | MongoDB connection string (e.g., `mongodb+srv://...`). |
| `STRING_SESSIONS` | `[]string` | Space, comma, or semicolon separated session strings for assistant accounts. Also accepts `STRING_SESSION`. |

---

## 🟢 Assistant Configuration

| Variable | Default | Options | Description |
| :--- | :--- | :--- | :--- |
| `SESSION_TYPE` | `pyrogram` | `pyrogram` · `telethon` · `gogram` | The library used to generate your `STRING_SESSIONS`. This **must** match the session format you used. |

---

## 👑 Ownership

| Variable | Default | Description |
| :--- | :--- | :--- |
| `OWNER_ID` | `0` | The Telegram User ID of the bot owner. Grants full administrative access. |

---

## 🎵 External APIs (Optional)

| Variable | Default | Description |
| :--- | :--- | :--- |
| `SPOTIFY_CLIENT_ID` | `None` | Spotify API Client ID for metadata resolution. |
| `SPOTIFY_CLIENT_SECRET` | `None` | Spotify API Client Secret for metadata resolution. |
| `FALLEN_API_KEY` | `""` | API Key for [Fallen API](https://beta.fallenapi.fun) YouTube downloader. |
| `FALLEN_API_URL` | `https://beta.fallenapi.fun` | Base URL for Fallen API. |

---

## 🛠️ Bot Behavior & Limits

| Variable | Default | Description |
| :--- | :--- | :--- |
| `DEFAULT_LANG` | `en` | Default language for bot responses (see `Amelia/locales/`). |
| `DURATION_LIMIT` | `4200` | Maximum track duration in seconds (70 minutes). |
| `QUEUE_LIMIT` | `24` | Maximum number of tracks in queue per chat. |
| `MAX_AUTH_USERS` | `25` | Max number of non-admin users allowed to control playback. |
| `LEAVE_ON_DEMOTED` | `false` | If `true`, the bot leaves the group if its admin rights are removed. |
| `SET_CMDS` | `false` | Automatically set bot commands in Telegram UI on startup. |
| `DISABLE_COLOUR` | `false` | If `true`, disables Telegram inline button colour styling (`Primary` / `Success` / `Danger`). |
| `COOKIES_LINK` | `""` | URL to a `yt-dlp` cookies file (e.g., via batbin). |
| `LOGGER_ID` | `0` | Chat ID where the bot sends logs and error reports. Also accepts `LOG_GROUP_ID`. If unset, logging-to-chat is disabled. |

---

## 🎨 Customization

| Variable | Default | Description |
| :--- | :--- | :--- |
| `EFFECT_IDS` | `""` | List of Telegram message effect IDs (space/comma/semicolon separated). One is chosen at random and applied on `/start`. Try `5104841245755180586` to see a sample effect. |
| `START_IMAGES` | `""` | List of start image URLs (space/comma/semicolon separated). One is chosen randomly for each `/start`. |
| `PING_IMG_URL` | `https://...` | Image URL shown in the `/ping` command response. |
| `SUPPORT_CHAT` | `https://t.me/MeowClone` | Full URL to the support group. |
| `SUPPORT_CHANNEL` | `https://t.me/Meowcloner` | Full URL to the announcement channel. |

---

## 🖥️ System Settings

| Variable | Default | Description |
| :--- | :--- | :--- |
| `PORT` | `8000` | Port for the internal debug pprof server. |
| `LOG_FILE` | `logs.txt` | Filename for system logs. |

---

## 📝 Notes

- Changes to the `.env` file or environment variables **require a bot restart** to take effect.
- Variable names are case-insensitive and underscore-insensitive — pick whichever style fits your workflow.
- Keep secrets like `API_HASH`, `TOKEN`, and `MONGO_DB_URI` out of version control; use `.env` (and `.gitignore` it) rather than hardcoding them.
