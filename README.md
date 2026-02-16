# 🏠 Home Server Infrastructure
A high-availability, containerized home server stack managed via Docker Compose. This setup automates the entire media lifecycle—from requests and discovery to automated downloading and streaming—while maintaining secure remote access through encrypted tunnels.

#Disclaimers
Please only utilize this setup to view media you already own. Such as Ripping DVDs and such that you have already bought. I do not endorse or condone the use of this for any illegal aquisition of copywrite protected materials. Whatever the user does with this setup is on them, especially if they dont use an VPN to secure their connections.

## 🚀 Architecture Overview
This server is built on a modular architecture using Docker containers, organized into specific virtual networks to ensure service isolation and security.

## 🛡️ Networking & Remote Access
Cloudflare Tunnel (cloudflared): Provides secure, outbound-only connectivity to the public internet without opening firewall ports.

Playit.gg: A global proxy service used as a secondary low-latency tunnel, specifically for gaming traffic.

Tailscale (Optional): Provisioned for a private WireGuard-based Mesh VPN (Meshnet) for administrative access. 
  (This is currently not included but I do like it and could find use)

## 📺 Media Automation Stack (The "Arr" Suite)
Jellyseerr: The discovery and request layer for end-users.

Sonarr & Radarr: Automated management for TV shows and movies.

SABnzbd: High-speed Usenet downloader for binary content retrieval.

Bazarr: Automated subtitle management and synchronization.

AudiobookShelf and ReadMeABook: Audiobook Management for retrieval and Listening

Jellyfin: The core media server providing hardware-accelerated transcoding (/dev/dri) for high-performance streaming.

## 🛠️ Utilities & Security
Vaultwarden: A lightweight implementation of the Bitwarden API for self-hosted password management.

Homarr: A sleek, customizable dashboard used as the central "landing page" for all server services.

Crafty Controller: A professional-grade management panel for hosting and monitoring Minecraft servers.

# 📂 Deployment
Prerequisites
Docker and Docker Compose installed.

An external Docker network named shared-network (used for cross-stack communication).

A .env file containing the necessary environment variables (CONFIG_PATH, MEDIA_PATH, PUID, PGID, etc.).

Configuration
The stack relies on local mapping for persistence:

App Data: All service configurations are stored in ${CONFIG_PATH}.

Media: Organized into /movies and /tvshows within ${MEDIA_PATH}.

Startup
Bash
docker-compose up -d
🛠️ Key Technical Features
Hardware Transcoding: Jellyfin is configured to access /dev/dri for Intel QuickSync/VA-API hardware acceleration.

Service Dependency Mapping: Utilizes depends_on to ensure the download client and database providers are healthy before application services start.

Infrastructure as Code: The entire environment is reproducible and portable via this docker-compose.yml and a single .env file.

# My Homarr Setup
<img width="1844" height="1029" alt="image" src="https://github.com/user-attachments/assets/a60a71e3-987c-4b29-8db2-b3afee78850d" />



