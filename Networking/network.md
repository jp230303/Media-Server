This document outlines networking schemes

---

## IP Addressing

### Deco
- **IP Address**: 192.168.68.0

---

### Media Server
- **IP Address**: 192.168.68.68
- **Name**: Prox
- **Purpose**: docker services run with this address (see below)

### NAS (HP)
- **IP Address**: 192.168.68.56
- **Name**: Jellyfin (legacy)
- **Purpose**: runs legacy media server, will change to NAS

---

## Services
### Bazzarr
- **Port**: 6767
- **Purpose**: Automates captions

### Homarr
- **Port**: 9898
- **Purpose**: Pretty web UI to access services

### Jellyfin
- **Port**: 8096
- **Purpose**: Hosts media

### Jellyseer
- **Port**: 5055
- **Purpose**: Allows for easy media requests

### Prowlarr
- **Port**: 9696
- **Purpose**: Hosts torrent indexers

### Radarr
- **Port**: 7878
- **Purpose**: Handles movie torrents

### Sonarr
- **Port**: 8989
- **Purpose**: Handles TV torrents

### Qbittorrent
- **Port**: 6881
- **Purpose**: Downloads torrent request
