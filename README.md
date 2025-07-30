![](https://github.com/5hojib/5hojib/raw/main/images/Aeon-MLTB.gif)

---

# Aeon-MLTB Bot

Aeon-MLTB is a streamlined and feature-rich bot designed for efficient deployment and enhanced functionality.

---

## Features

- **Minimalistic and Optimized**: Simplified by removing unnecessary code for better performance.
- **Effortless Deployment**: Fully configured for quick and easy deployment to Heroku.
- **Enhanced Capabilities**: Integrates features from multiple sources to provide a versatile bot experience.

---

## 🚀 VPS Deployment Guide (Step by Step)

### Prerequisites
- A VPS with Ubuntu/Debian or similar Linux distribution
- Root or sudo access
- Basic knowledge of terminal commands

### Step 1: Connect to Your VPS
```bash
ssh root@your-vps-ip
# or
ssh username@your-vps-ip
```

### Step 2: Update System and Install Dependencies
```bash
# Update system packages
sudo apt update && sudo apt upgrade -y

# Install required packages
sudo apt install -y python3 python3-pip git curl wget nano

# Install Docker
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker $USER

# Install Docker Compose
sudo apt install -y docker-compose-plugin

# Logout and login again for Docker group to take effect
exit
# Reconnect to your VPS
```

### Step 3: Clone the Repository
```bash
# Clone the repository
git clone https://github.com/AeonOrg/Aeon-MLTB.git
cd Aeon-MLTB
git checkout extended

# Install CLI requirements
pip3 install -r dev/requirements-cli.txt
```

### Step 4: Configure the Bot
```bash
# Copy the sample configuration
cp config_sample.py config.py

# Edit the configuration file
nano config.py
```

**Required Configuration Fields:**
- `BOT_TOKEN`: Get from [@BotFather](https://t.me/BotFather)
- `OWNER_ID`: Your Telegram User ID
- `TELEGRAM_API`: Get from [my.telegram.org](https://my.telegram.org)
- `TELEGRAM_HASH`: Get from [my.telegram.org](https://my.telegram.org)
- `DATABASE_URL`: MongoDB connection string

### Step 5: Deploy Using Docker Compose
```bash
# Build and start the bot
sudo docker compose up -d

# View logs
sudo docker compose logs -f

# Stop the bot
sudo docker compose stop

# Start the bot
sudo docker compose start

# Restart with changes
sudo docker compose up -d --build
```

### Step 6: Configure Firewall and Ports
```bash
# Make the port opening script executable
sudo chmod +x open_ports.sh

# Run the script to open required ports
sudo ./open_ports.sh
```

### Step 7: Upload Private Files (Optional)
After the bot is running, use the `/botsettings` command in Telegram to upload:
- `token.pickle` (Google Drive authentication)
- `shorteners.txt` (URL shortener configurations)
- `cookies.txt` (Browser cookies)
- `accounts.zip` (Service accounts)
- `rclone.conf` (Rclone configuration)

### Step 8: Verify Deployment
1. Send `/start` to your bot on Telegram
2. Check if the bot responds
3. Use `/help` to see available commands

### Troubleshooting
```bash
# Check if Docker is running
sudo systemctl status docker

# Check container status
sudo docker compose ps

# View detailed logs
sudo docker compose logs --tail=100

# Restart everything
sudo docker compose down
sudo docker compose up -d
```

### Updating the Bot
```bash
# Pull latest changes
git pull origin extended

# Rebuild and restart
sudo docker compose up -d --build
```

---

## Read these

[Deployment](https://github.com/AeonOrg/Aeon-MLTB/blob/extended/docs/DEPLOYMENT.md)
[Configuration](https://github.com/AeonOrg/Aeon-MLTB/blob/extended/docs/CONFIGURATIONS.md)
[Commands](https://github.com/AeonOrg/Aeon-MLTB/blob/extended/docs/COMMANDS.md)
[Features](https://github.com/AeonOrg/Aeon-MLTB/blob/extended/docs/FEATURES.md)
[Extras](https://github.com/AeonOrg/Aeon-MLTB/blob/extended/docs/EXTRAS.md)

---

## Contributing

We welcome contributions! Whether it's bug fixes, feature enhancements, or general improvements:
- **Report issues**: Open an issue for bugs or suggestions.
- **Submit pull requests**: Share your contributions with the community.

---

## Support

For issues, join here https://t.me/AeonDiscussion.

---

## License

This project is licensed under the MIT License. Refer to the [LICENSE](LICENSE) file for details.

---

## Acknowledgements

- Special thanks to the original developers of the [Mirror-Leech-Telegram-Bot](https://github.com/anasty17/mirror-leech-telegram-bot).
- Gratitude to contributors from various repositories whose features have been integrated into Aeon.
