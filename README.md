# 🔥 Discord Nuke Bot

A Discord bot that instantly mass-deletes all channels and roles in your server.

---

## Commands

| Command | What it does | Required Permission |
|---|---|---|
| `!nuke` | Deletes ALL channels AND roles | Administrator |
| `!nukechannels` | Deletes all channels only | Manage Channels |
| `!nukeroles` | Deletes all roles only | Manage Roles |
| `!help` | Shows command list | — |

---

## Setup

### 1. Create a Discord Bot

1. Go to [https://discord.com/developers/applications](https://discord.com/developers/applications)
2. Click **New Application** → give it a name
3. Go to **Bot** tab → click **Add Bot**
4. Under **Privileged Gateway Intents**, enable:
   - ✅ Server Members Intent
   - ✅ Message Content Intent
5. Copy the **Bot Token** — you'll need this shortly
6. Go to **OAuth2 → URL Generator**:
   - Scopes: `bot`
   - Bot Permissions: `Administrator`
7. Open the generated URL and invite the bot to your server

### 2. Deploy to Railway

1. Push this repo to GitHub
2. Go to [https://railway.app](https://railway.app) and create a **New Project**
3. Choose **Deploy from GitHub repo** and select this repo
4. Go to **Variables** and add:
   ```
   DISCORD_TOKEN = your_bot_token_here
   ```
5. Railway will auto-detect `railway.toml` and deploy

### 3. Run Locally (optional)

```bash
npm install
DISCORD_TOKEN=your_token_here node bot.js
```

---

## ⚠️ Important Notes

- The bot's **role must be at the top** of the role hierarchy in your server settings, otherwise it can't delete roles above it.
- The bot **cannot delete** roles managed by integrations (e.g. Nitro Booster, other bots).
- The `@everyone` role is never deleted (it's the server itself).
- After `!nuke` or `!nukechannels`, a `#nuke-log` channel is automatically created with a summary.
