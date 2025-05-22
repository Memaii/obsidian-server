# Obsidian Server – Self-hosted Synchronization with CouchDB

This Docker-based project sets up a CouchDB instance preconfigured for the Self-hosted LiveSync plugin for Obsidian. It provides a free, self-hosted alternative to Obsidian Sync, enabling real-time synchronization between multiple Obsidian clients.

You need to use this Github project to make it work
   ```bash
   git clone https://github.com/vrtmrz/obsidian-livesync.git
   ```
---

## ✨ Features

- Real-time, bidirectional sync between multiple Obsidian clients
- Works across desktop and mobile (iOS/Android)
- Simple Docker Compose deployment
- End-to-end encryption support (E2EE) via the plugin
- Optional HTTPS access via reverse proxy

---

## 📦 Requirements

- Docker and Docker Compose
- Domain name (optional but recommended for HTTPS)
- Reverse proxy (e.g., Nginx, Traefik) with a valid SSL certificate (recommended for mobile access)

---

## 🚀 Quick Start

1. Clone this repository:
   ```bash
   git clone https://github.com/Memaii/obsidian-server.git
   cd obsidian-server
   ```

2. Create a `.env` file with your settings:
   ```env
   COUCHDB_USER=obsidian
   COUCHDB_PASSWORD=strongpassword
   COUCHDB_DATABASE=notes
   COUCHDB_PORT=5984
   ```

3. Launch the container:
   ```bash
   docker compose up -d
   ```

4. Access CouchDB's web UI:
   ```
   http://localhost:5984/_utils (or your domain if configured)
   ```

---

## 🔧 Obsidian LiveSync Plugin Setup

1. Install the Self-hosted LiveSync plugin from Obsidian's community plugins.
2. In the plugin settings, configure:
   - **Remote Database URI:** `http://localhost:5984` or `https://your-domain.com`
   - **Database name:** `notes` (or as defined in your `.env`)
   - **Username:** `obsidian`
   - **Password:** `strongpassword`
   - Enable E2EE if needed
3. Repeat this configuration on each device you want to sync.

---

## 📁 Project Structure

```
obsidian-server/
├── docker-compose.yml
├── .env
└── README.md
```

---

## 🛡️ Security (HTTPS & Mobile Access)

- Set up a reverse proxy (e.g., Nginx) with a valid SSL certificate (Let’s Encrypt, Cloudflare, etc.)
- Ensure CORS headers are configured in CouchDB to allow origins like `app://obsidian.md` and `capacitor://localhost` (see blackvoid.club for examples)

---

## 🧪 Testing & Verification

- Ensure CouchDB is reachable at your configured URL
- Create the `notes` database if it does not already exist
- Test synchronization by creating a note on one device and confirming it appears on another

---

## 📚 Useful Resources

- Official obsidian-livesync documentation
- Prebuilt Docker image by oleduc
- Guide for using Portainer + Nginx Proxy Manager

---

## 🧠 Notes

- Do not mix this plugin with other sync solutions (Obsidian Sync, Dropbox, etc.) to avoid conflicts
- The plugin will auto-create system databases (`_users`, `_replicator`, etc.) on first connection (see blog.kirillov.cc)

---
