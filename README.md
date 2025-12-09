# Reviving a Dead Laptop into a Home Server 🖥️➡️🧠

This project documents how I took an old **dead Dell laptop** and turned it into a **fully working home server**.

## 🧱 Hardware

- Old Dell Inspiron laptop (dead OS, but CPU/RAM still okay)
- 120 GB internal SSD (for OS)
- 500 GB internal HDD (for storage)
- External HDD (media backup)
- Wi-Fi router (192.168.29.x network)

## 🐧 Base System

- **OS:** Ubuntu Server 24.04.3 LTS (no GUI)
- Bootable USB created using **Rufus** on Windows
- Installed in **server mode** with:
  - OpenSSH server
  - LVM on SSD
  - Static IP on Wi-Fi

## 🌐 Networking

- Static IP for the server
- Wi-Fi configured via Netplan
- Router gives DHCP to other devices, but server has a fixed IP
- Can SSH from my main Windows laptop and Android phone

## 🧰 Core Services

- **Docker** & **Docker Compose**
- **Portainer** for container management (running on port `9000`)
- **Samba (SMB)** share:
  - Share name: `satyam-share`
  - Mounted on Windows as a network drive
- **External HDD** mounted on `/mnt/exthdd` and shared over SMB

## 📈 Monitoring & Health

- **Netdata** web dashboard
- **Glances** for terminal-based monitoring
- `lm-sensors` configured for CPU temperature and fan stats
- Basic **firewall** with `ufw`:
  - Default: deny incoming, allow outgoing
  - Allows: SSH (rate-limited), Samba, Portainer, Netdata
- **Fail2Ban** to protect SSH

## 🛡️ Security

- SSH access from local network only
- UFW firewall with `ufw limit ssh`
- Automatic security & package updates via `unattended-upgrades`

## 💿 Storage Layout

- SSD:
  - OS + Docker + configs
- HDD:
  - Mounted at `/mnt/hdd` for general storage
- External HDD:
  - Mounted at `/mnt/exthdd` for media and backups

All shares are accessible from my main Windows laptop and even my TV (via browser / Jellyfin in future).

## 📺 Media Server (Planned / WIP)

- Plan to run **Jellyfin** in Docker
- Use HDD + external HDD as media libraries
- Stream to:
  - Windows laptop
  - Android phone
  - Smart TV (via browser / Jellyfin app if available)

## 🔧 Laptop Revival Story

Originally, this laptop was:
- Failing to boot
- Throwing **7 beeps** (CPU-related issue)
- Overheating and full of dust

What I did:
1. Opened the laptop completely, cleaned dust and fan
2. Removed old thermal paste and applied new thermal paste
3. Reseated RAM and CPU cooler
4. Replaced internal drive with SSD
5. Installed Ubuntu Server and set it up as a home server

Now it runs:
- Headless (lid mostly closed)
- 24/7 as my **home server + NAS + future media server**

## 🚀 Future Plans

- Jellyfin media server
- Nextcloud / personal cloud
- Pi-hole for network-wide ad blocking
- Tailscale / WireGuard for secure remote access
- Automated backups for important folders

---

If you have an old laptop lying around, you can turn it into a server too.  
Feel free to open issues or discussions if you want to replicate this setup or improve it!
