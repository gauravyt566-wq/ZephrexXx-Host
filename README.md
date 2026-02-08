# 🚀 Python Hosting Bot

<div align="center">

**A powerful Telegram bot for hosting Python projects with advanced monitoring, auto-restart, and analytics**

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Telegram](https://img.shields.io/badge/Telegram-Bot-blue.svg)](https://core.telegram.org/bots)

</div>

---

## 📋 Table of Contents

- [Features](#-features)
- [Demo](#-demo)
- [Installation](#-installation)
- [Configuration](#-configuration)
- [Usage](#-usage)
- [Commands](#-commands)
- [Admin Panel](#-admin-panel)
- [Project Structure](#-project-structure)
- [Deployment](#-deployment)
- [Troubleshooting](#-troubleshooting)
- [Contributing](#-contributing)
- [License](#-license)

---

## ✨ Features

### 🎯 Core Features
- **🆓 Free Hosting** - 1 free project per user with 512 MB RAM
- **📦 Easy Upload** - Support for .zip files or individual file uploads
- **▶️ Project Management** - Start, stop, restart projects with one click
- **🔄 Auto-Restart** - Automatic crash recovery with configurable limits
- **📊 Live Dashboard** - Real-time CPU, RAM, and uptime monitoring
- **📈 Analytics** - Detailed usage statistics and resource tracking
- **🔔 Smart Alerts** - Get notified about crashes, high CPU/RAM usage
- **🔐 Environment Variables** - Secure .env file management
- **📄 Logs** - Download project, error, and dependency logs
- **👑 Admin Panel** - Complete user and project management

### 🛡️ Security Features
- User ban/unban system
- Admin-only commands
- Secure environment variable storage
- Private file backup to designated channel

### 🎨 UI/UX Features
- Clean, professional interface
- No link previews for cleaner chat
- Emoji-rich messages
- Progress indicators
- Confirmation dialogs for destructive actions

---

## 🎥 Demo

```
User: /start

Bot:
🎉 Welcome to Python Hosting Bot!
━━━━━━━━━━━━━━━━━━━━

👤 User Details:
├─ Name: John Doe
├─ Username: @johndoe
└─ User ID: 123456789

🚀 Quick Commands:

📝 /newproject - Create a new project
📂 /myproject - View & manage projects
❓ /help - Get detailed help

📊 Your Free Plan:
├─ Projects: 1 active project
└─ RAM: 512 MB per project
```

---

## 🔧 Installation

### Prerequisites
- Python 3.8 or higher
- MongoDB database
- Telegram Bot Token (from [@BotFather](https://t.me/BotFather))
- VPS/Server with systemd (for production)

### Step 1: Clone Repository
```bash
git clone https://github.com/badalxjod/HostingBot
cd HostingBot
```

### Step 2: Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 3: Configure Bot
Edit `config.py`:
```python
BOT_TOKEN = "YOUR_BOT_TOKEN_HERE"
MONGO_URI = "YOUR_MONGODB_URI_HERE"
BACKUP_CHANNEL_ID = "-1001234567890"  # Your private group/channel ID
OWNER_IDS = [123456789]  # Your Telegram user ID
```

### Step 4: Run Bot
```bash
python3 main.py
```

---

## ⚙️ Configuration

### `config.py` Settings

```python
# Bot Configuration
BOT_TOKEN = "7992799467:AAENUHclwcSWmZzj-uE6pgMiZgHFqAKSG4c"

# Database Configuration
MONGO_URI = "mongodb+srv://username:password@cluster.mongodb.net/"
DB_NAME = "hostbot"

# File System Configuration
BASE_DIR = Path.home() / "hosting_projects"

# Admin Configuration
OWNER_IDS = [8302548508]  # Add your Telegram user IDs

# Backup Channel Configuration
BACKUP_CHANNEL_ID = "-1003469358500"  # Private group/channel for file backups

# Branding
DEVELOPER_LINK = "t.me/TheNoxen"
CHANNEL_LINK = "t.me/MadXBots"
```

### Getting Backup Channel ID

1. Create a private group/channel
2. Add `@RawDataBot` to the group
3. Send any message
4. Bot will reply with the chat ID (negative number like `-1001234567890`)
5. Copy that ID to `BACKUP_CHANNEL_ID` in config.py

### Getting Your User ID

1. Message `@userinfobot` on Telegram
2. It will send you your user ID
3. Add it to `OWNER_IDS` list in config.py

---

## 📖 Usage

### Creating a Project

1. Send `/newproject` to the bot
2. Enter a project name
3. Upload your files:
   - **Option 1:** Send a .zip file containing all project files
   - **Option 2:** Upload `main.py` and `requirements.txt` separately
4. Type `/done` when finished
5. Click **▶️ Start** to run your project

### Managing Projects

Send `/myproject` to view all your projects with management buttons:

| Button | Action |
|--------|--------|
| ▶️ Start | Start the project |
| ⏹ Stop | Stop running project |
| 🔄 Restart | Restart project |
| 📊 Dashboard | View live stats |
| 🔐 Env Vars | Manage environment variables |
| 📈 Analytics | View usage analytics |
| 📄 Logs | Download log files |
| 📦 Dependencies | Install requirements.txt |
| ✏️ Edit Run Cmd | Change execution command |
| 🗑 Delete | Delete project permanently |

---

## 🤖 Commands

### User Commands

| Command | Description |
|---------|-------------|
| `/start` | Start the bot and view welcome message |
| `/help` | Get detailed help guide |
| `/newproject` | Create a new project |
| `/myproject` | View and manage your projects |
| `/done` | Complete project setup |
| `/cancel` | Cancel current operation |

### Admin Commands

| Command | Description |
|---------|-------------|
| `/admin` | Open admin control panel |

---

## 👑 Admin Panel

Access via `/admin` command (only for users in `OWNER_IDS`)

### Features

#### 📢 Broadcast
Send messages to all active users:
- Text messages
- Photos with captions
- Videos with captions
- Documents with captions

#### 🚫 User Management
- **Ban User** - Block user from using the bot
- **Unban User** - Restore user access

#### ⭐ Slot Management
Manage user project limits:
- **Free Slots** - Number of free projects
- **Premium Slots** - Number of premium projects

#### 👥 User List
View all registered users with:
- Username and name
- User ID
- Active/Banned status
- Admin badge
- Project count and slots

#### 📂 User Projects
Inspect any user's projects:
- View all projects
- Check project status
- View project details

#### 📈 Activity Log
View recent bot activity:
- User actions
- Project operations
- Timestamps

---

## 📁 Project Structure

```
python-hosting-bot/
├── main.py                  # Main bot entry point
├── bot_instance.py          # Bot instance and state management
├── config.py                # Configuration file
├── database.py              # MongoDB database operations
├── process_manager.py       # Process management (start/stop/restart)
├── keyboards.py             # Inline keyboards for bot
├── handlers_user.py         # User command handlers
├── handlers_admin.py        # Admin command handlers
├── handlers_features.py     # Feature handlers (dashboard, analytics, env vars)
├── requirements.txt         # Python dependencies
├── README.md               # This file
│
└── utils/                   # Utility modules
    ├── __init__.py
    ├── env_manager.py       # Environment variables management
    ├── health_monitor.py    # Process health monitoring
    └── analytics.py         # Usage analytics and tracking
```

---

## 🚀 Deployment

### Option 1: Systemd Service (Recommended)

Create a service file:
```bash
sudo nano /etc/systemd/system/hostbot.service
```

Add this content:
```ini
[Unit]
Description=Python Hosting Bot
After=network.target

[Service]
Type=simple
User=YOUR_USERNAME
WorkingDirectory=/path/to/python-hosting-bot
ExecStart=/usr/bin/python3 /path/to/python-hosting-bot/main.py
Restart=always
RestartSec=10

[Install]
WantedBy=multi-user.target
```

Enable and start:
```bash
sudo systemctl daemon-reload
sudo systemctl enable hostbot
sudo systemctl start hostbot
sudo systemctl status hostbot
```

View logs:
```bash
sudo journalctl -u hostbot -f
```

### Option 2: PM2

```bash
# Install PM2
npm install -g pm2

# Start bot
pm2 start main.py --name hostbot --interpreter python3

# Auto-restart on system reboot
pm2 startup
pm2 save

# View logs
pm2 logs hostbot

# Restart bot
pm2 restart hostbot
```

### Option 3: Screen/Tmux

```bash
# Using screen
screen -S hostbot
python3 main.py
# Press Ctrl+A then D to detach

# Reattach
screen -r hostbot

# Using tmux
tmux new -s hostbot
python3 main.py
# Press Ctrl+B then D to detach

# Reattach
tmux attach -t hostbot
```

---

## 🐛 Troubleshooting

### Bot Not Starting

**Problem:** Bot doesn't respond to commands

**Solutions:**
1. Check if bot token is correct in `config.py`
2. Verify MongoDB connection string
3. Check bot logs for errors:
   ```bash
   sudo journalctl -u hostbot -n 50
   ```

### Projects Not Starting

**Problem:** Project shows "Failed to Start"

**Solutions:**
1. Check if `main.py` exists in project directory
2. Verify Python syntax in uploaded files
3. Check dependencies are installed
4. View error logs from bot

### MongoDB Connection Failed

**Problem:** Can't connect to MongoDB

**Solutions:**
1. Verify `MONGO_URI` in config.py
2. Check MongoDB server is running
3. Whitelist your VPS IP in MongoDB Atlas
4. Test connection:
   ```python
   from pymongo import MongoClient
   client = MongoClient("YOUR_MONGO_URI")
   print(client.server_info())
   ```

### Auto-Restart Not Working

**Problem:** Projects don't restart after crash

**Solutions:**
1. Check health monitor is running in logs
2. Verify `auto_restart` is enabled in database
3. Check restart count hasn't exceeded `max_restarts`
4. Review project logs for crash reason

### File Upload Failed

**Problem:** Can't upload files to bot

**Solutions:**
1. Check file size (Telegram limit: 50MB)
2. Verify file format (.zip, .py, .txt)
3. Check bot has write permissions to `BASE_DIR`
4. Ensure sufficient disk space on server

---

## 🔐 Security Best Practices

1. **Keep Bot Token Secret**
   - Never commit `config.py` to public repositories
   - Use environment variables for sensitive data
   - Regenerate token if compromised

2. **Secure MongoDB**
   - Use strong passwords
   - Enable IP whitelist
   - Use SSL/TLS connections
   - Regular backups

3. **Server Security**
   - Keep system updated
   - Use firewall (UFW/iptables)
   - Disable root SSH login
   - Use SSH keys instead of passwords

4. **Regular Monitoring**
   - Check bot logs regularly
   - Monitor disk space
   - Track unusual activity
   - Review admin actions

---

## 📊 Features Deep Dive

### 📊 Dashboard
Real-time monitoring showing:
- Process ID (PID)
- CPU usage percentage
- RAM usage (current/limit)
- Uptime duration
- Restart count
- Active alerts

### 📈 Analytics
Detailed statistics including:
- Total uptime
- CPU hours consumed
- Average memory usage
- Storage used
- File count
- Uptime percentage

### 🔐 Environment Variables
Secure variable management:
- Add variables one by one
- Upload complete .env files
- View masked values (KEY=ab***xy)
- Delete individual variables
- Variables loaded automatically on project start

### 🔄 Auto-Restart System
Smart crash recovery:
- Monitors processes every 30 seconds
- Auto-restarts on crash (up to 5 times)
- Alerts user on failures
- Tracks restart attempts
- Prevents restart loops

### 🔔 Alert System
Get notified about:
- Process crashes
- High CPU usage (>90%)
- High memory usage (>80%)
- Disk space warnings
- Failed restarts

---

## 📈 Scaling

### Handling More Users

1. **Vertical Scaling**
   - Upgrade VPS RAM and CPU
   - Increase MongoDB capacity
   - Optimize database queries

2. **Horizontal Scaling**
   - Deploy multiple bot instances
   - Use load balancer
   - Implement message queue
   - Separate database server

3. **Resource Limits**
   - Implement CPU throttling
   - Set RAM limits per project
   - Disk quota management
   - Rate limiting

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Code Style
- Follow PEP 8 guidelines
- Use meaningful variable names
- Add comments for complex logic
- Write docstrings for functions

---

## 📝 Changelog

### Version 2.0.0 (Current)
- ✅ Removed referral system
- ✅ Removed file manager
- ✅ Simplified to 1 free project model
- ✅ Added user details in /start message
- ✅ Disabled link previews everywhere
- ✅ Improved UI/UX
- ✅ Silent file backup system
- ✅ Cleaner admin notifications

### Version 1.0.0
- ✅ Initial release
- ✅ Basic project management
- ✅ Dashboard and analytics
- ✅ Auto-restart system
- ✅ Environment variables
- ✅ Admin panel

---

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 👨‍💻 Developer

**Made with ❤️ by [TheNoxen](https://t.me/TheNoxen)**

### Support
- 📢 Updates: [MadXBots Channel](https://t.me/MadXBots)
- 💬 Support: [Contact Developer](https://t.me/TheNoxen)

---

## 🙏 Acknowledgments

- [pyTelegramBotAPI](https://github.com/eternnoir/pyTelegramBotAPI) - Telegram Bot API wrapper
- [MongoDB](https://www.mongodb.com/) - Database
- [psutil](https://github.com/giampaolo/psutil) - Process monitoring
- All contributors and users!

---

## ⭐ Star History

If you found this project helpful, please consider giving it a star! ⭐

---

## 📞 Contact

- Telegram: [@TheNoxen](https://t.me/TheNoxen)
- Channel: [@MadXBots](https://t.me/MadXBots)

---

<div align="center">

**Made with ❤️ for the Python community**

⭐ Don't forget to star this repo if you find it useful! ⭐

</div>
