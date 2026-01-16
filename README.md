# Battleye-Discord-Bot
This bot posts the Battleye Ban Statistics into your Server either automatically or with a command.

# Tutorial

# *1.* Prerequisites
A Linux Server (Ubuntu recommended).  
Python 3.10 or higher.  
A Discord Bot Token (from the Discord Developer Portal).  
Privileged Gateway Intents (Message Content Intent) enabled in the Developer Portal.

# *2.* Server Preparation  
Run the following commands to set up the environment:  
- Update the system  
sudo apt update && sudo apt upgrade -y  
- Create a project folder  
mkdir gta_ban_bot && cd gta_ban_bot  
- Set up a virtual environment  
python3 -m venv venv  
source venv/bin/activate  
- Install required libraries  
pip install discord.py requests

# *3.* Creating the Bot Script  
Create the script file:  
nano bot.py  
Paste your Python code into this file. Make sure to update the following variables at the top:  
TOKEN: Your Discord Bot Token.  
ANNOUNCEMENT_CHANNEL_ID: The ID of the channel where updates should be posted.  
ROLE_ID: The ID of the role to ping during ban waves.  
Save and exit: Ctrl+O, Enter, then Ctrl+X.  

# *4.* Setting up 24/7 Operation (Systemd)  
To keep the bot running after you close the terminal and to restart it automatically on server reboots:  
 1.Create a service file:  
   sudo nano /etc/systemd/system/gta_bot.service
   
  2.Paste this configuration (adjust User and WorkingDirectory if necessary):  

[Unit]  
Description=GTA Ban Discord Bot  
After=network.target  

[Service]  
User=USER  
WorkingDirectory=/home/USER/gta_ban_bot  
ExecStart=/home/USER/gta_ban_bot/venv/bin/python3 /home/USER/gta_ban_bot/bot.py  
Restart=always  
RestartSec=5  

[Install]  
WantedBy=multi-user.target  

  3.Enable and start the service:  
 sudo systemctl daemon-reload  
 sudo systemctl enable gta_bot  
 sudo systemctl start gta_bot  
# *5.* Bot Commands:  
!bans: Shows current ban statistics in the channel where the command is used.  
!post: Manually forces a status update into the predefined announcement channel.  
Auto-Alerts: Pings the defined role if bans exceed 500 within 24 hours.  
Schedules: Automatically posts updates at 00:00, 06:00, 12:00, and 18:00. (Changeable in the bot.py)

