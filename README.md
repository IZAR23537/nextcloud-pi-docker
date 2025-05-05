# 🧊 Nextcloud Docker Setup for Raspberry Pi (Local Only)

This is a lightweight, local-only Docker setup to run **Nextcloud with PostgreSQL** on a Raspberry Pi using an **external hard drive** for storage.

---
## 🌐 What is Nextcloud?

Nextcloud is an open-source platform that provides:

    📁 File sync and sharing (like Dropbox or Google Drive)

    🧑‍🤝‍🧑 User accounts and permissions

    📅 Calendars, Contacts, Notes, and To-Do apps

    🔌 Extendable via community apps (e.g., video calls, document editing)

It's ideal for privacy-conscious individuals or home lab setups, and runs well on Raspberry Pi when optimized.

## ✅ The Project Features

- Runs only on local network
- Uses PostgreSQL (not SQLite)
- All data (files + database) stored on external drive
- ARM-compatible images

---

## 🧰 Requirements

- Raspberry Pi 4 or 5 with 64-bit OS
- Docker + Docker Compose
- External USB drive, formatted as **ext4**

---

## 📁 External Drive Mounting

1. Format as ext4:
```bash
sudo mkfs.ext4 /dev/sda1
```

2. Mount:
```bash
sudo mkdir -p /mnt/externaldrive
sudo mount /dev/sda1 /mnt/externaldrive
```

3. Persist in `/etc/fstab`:
```
/dev/sda1 /mnt/externaldrive ext4 defaults 0 2
```

🚨 **Important**: PostgreSQL must not run on NTFS or exFAT. It requires a Unix-style FS (like ext4).

---

## 🚀 Getting Started

```bash
cd nextcloud-pi-docker
docker-compose up -d
```

Then visit [http://your-pi-ip:8080] and complete Nextcloud setup.

Use:
- **Database user**: `nextcloud`
- **Password**: `secret`
- **DB name**: `nextcloud`
- **Host**: `db`

---
