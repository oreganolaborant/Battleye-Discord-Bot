# 🛡️ GTA V BattlEye Ban Tracker Bot

A professional Discord bot that tracks real-time BattlEye ban statistics for GTA V. It uses a headless browser (Playwright) to bypass protection and provides live updates, automated ban-wave alerts, and a smart caching system.

---

## ✨ Features
* **Live Stats:** Tracks Today's Bans, All-Time Bans, Latest Ban and Average Daily Bans.
* **Smart Caching:** Updates every 10 minutes to save server resources.
* **Ban-Wave Alerts:** Automatically pings a role in an announcement channel if bans exceed 500.
* **Dynamic UI:** Embed colors change based on risk level (Green = Clear, Red = Ban Wave).
* **Status Presence:** Displays live ban counts in the bot's Discord activity.
* **Admin Commands:** Manual posting and forced cache updates.
* **Automatic Updates:** Sends a Automatic Battleye Update every 6hrs.

---

## 🚀 Installation & Setup

### 1. Prerequisites
You need a Linux server (Ubuntu recommended) with Python 3.10+ installed.

### 2. Prepare the Environment
```bash
# Create project folder
mkdir -p ~/gta_ban_bot && cd ~/gta_ban_bot

# Create virtual environment
python3 -m venv venv
source venv/bin/activate

# Install dependencies
pip install discord.py playwright
playwright install firefox
playwright install-deps
```

### 3. Bot Script (bot.py)

Create a file named bot.py and paste the code. Replace the placeholders in the CONFIG section with your actual IDs.

(Download bot.py.txt for the code)

### 4. Run as a System Service (24/7)
Create the service file: sudo nano /etc/systemd/system/gta_bot.service

(Download gta_bot.service.txt for the code)

Template: (Replace YOUR_USER with your Linux username)

Enable and Start:
```
sudo systemctl daemon-reload
sudo systemctl enable gta_bot
sudo systemctl start gta_bot
```

---

### Commands:

Command Permission     Description

!bans   Everyone       Shows current stats in a compact embed (no image).

!post   Admin          Manually posts the stats with a banner to the announcement channel.

!update Admin          Forces a browser refresh and updates the cache immediately.

---

### 📊 Status Indicators
✅ Status: 🛡️ Clear: Today's bans are below 500.

🚨 Ban Wave | Be careful: Today's bans have exceeded 500.

