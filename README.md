Obsidian Server – Self-hosted Synchronization with CouchDB
This Docker-based project sets up a CouchDB instance preconfigured for the Self-hosted LiveSync plugin for Obsidian. It provides a free, self-hosted alternative to Obsidian Sync, enabling real-time synchronization between all your devices.

✨ Features
Real-time, bidirectional sync between multiple Obsidian clients

Works across desktop and mobile (iOS/Android)

Simple Docker Compose deployment

End-to-end encryption support (E2EE) via the plugin

Optional HTTPS access via reverse proxy

📦 Requirements
Docker and Docker Compose

Domain name (optional but recommended for HTTPS)

Reverse proxy (e.g. Nginx, Traefik) with valid SSL certificate (recommended for mobile access)

🚀 Quick Start
Clone this repository:

bash
Copier
Modifier
git clone https://github.com/Memaii/obsidian-server.git
cd obsidian-server
Create a .env file with your settings:

env
Copier
Modifier
COUCHDB_USER=obsidian
COUCHDB_PASSWORD=strongpassword
COUCHDB_DATABASE=notes
COUCHDB_PORT=5984
Launch the container:

bash
Copier
Modifier
docker compose up -d
Access CouchDB's web UI:

http://localhost:5984/_utils (or your domain if configured)

🔧 Setting Up Obsidian LiveSync Plugin
Install the Self-hosted LiveSync plugin from Obsidian's community plugins.

In the plugin settings, configure the following:

Remote Database URI: http://localhost:5984 or https://your-domain.com

Database name: notes (or as defined in your .env)

Username: obsidian

Password: strongpassword

Enable E2EE if needed.

Repeat this configuration on each device.

📁 Project Structure
bash
Copier
Modifier
obsidian-server/
├── docker-compose.yml
├── .env
└── README.md
🛡️ Security (HTTPS & Mobile Access)
To access your server from mobile devices, it is strongly recommended to:

Set up a reverse proxy (e.g., Nginx) with a valid SSL certificate (via Let’s Encrypt or Cloudflare)

Ensure CORS headers are properly configured in CouchDB to allow origins like app://obsidian.md and capacitor://localhost (blackvoid.club)

🧪 Testing & Verification
Ensure CouchDB is reachable at the defined URL.

Create the notes database if it does not already exist.

Test synchronization by creating a note on one device and confirming it appears on another.

📚 Useful Resources
Official obsidian-livesync docs

Prebuilt Docker image by oleduc

Guide using Portainer + Nginx Proxy Manager

🧠 Notes
Do not mix this plugin with other sync solutions (Obsidian Sync, Dropbox, etc.) to avoid conflicts.

The plugin will auto-create system databases (_users, _replicator, etc.) on first connection (blog.kirillov.cc).
