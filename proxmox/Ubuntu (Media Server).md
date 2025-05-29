This document outlines docker installation on ubuntu server as well as the docker compose for the services in use.

---

## Ubuntu/Docker Configuration
### Docker installation
```
# Update and install Docker
sudo apt update && sudo apt upgrade -y
sudo apt install docker.io docker-compose -y
sudo usermod -aG docker $USER
```
- run ``` newgrp docker```

---

### Mount NAS
```
sudo mkdir /mnt/media
sudo mount -t cifs //192.168.68.56/media /mnt/media -o user=server,password=Frog2121
```
### Auto-mount in /etc/fstab
```
//192.168.68.56/media  /mnt/media  cifs  username=youruser,password=yourpass,iocharset=utf8,uid=1000,gid=1000,nofail  0  0
```
- run sudo mount -a

---

### Docker Compose
- Create directory
```
mkdir -p /home/user/docker
cd /home/user/docker
```
```
nano docker-compose.yml
```
```
version: '3.8'

services:
  jellyfin:
    image: jellyfin/jellyfin:latest
    container_name: jellyfin
    ports:
      - "8096:8096"
    volumes:
      - /mnt/media:/mnt/media
      - /home/user/docker/jellyfin/config:/config
    restart: always
    networks:
      - media_network

  jellyseer:
    image: fallenbagel/jellyseerr:latest
    container_name: jellyseer
    ports:
      - 5055:5055
    volumes:
      - /mnt/media:/mnt/media
      - /home/user/docker/jellyseer/config:/config
    restart: always
    networks:
      - media_network

  prowlarr:
    image: lscr.io/linuxserver/prowlarr:latest
    container_name: prowlarr
    ports:
      - "9696:9696"
    volumes:
      - /mnt/media:/mnt/media
      - /home/user/docker/prowlarr/config:/config
    restart: always
    networks:
      - media_network

  bazarr:
    image: lscr.io/linuxserver/bazarr:latest
    container_name: bazarr
    depends_on:
      - jellyfin
    volumes:
      - /mnt/media:/mnt/media
      - /home/user/docker/bazarr/config:/config
    restart: always
    networks:
      - media_network

  radarr:
    image: lscr.io/linuxserver/radarr:latest
    container_name: radarr
    ports:
      - "7878:7878"
    volumes:
      - /mnt/media:/mnt/media
      - /home/user/docker/radarr/config:/config
    restart: always
    networks:
      - media_network

  sonarr:
    image: lscr.io/linuxserver/sonarr:latest
    container_name: sonarr
    ports:
      - "8989:8989"
    volumes:
      - /mnt/media:/mnt/media
      - /home/user/docker/sonarr/config:/config
    restart: always
    networks:
      - media_network

  qbittorrent:
    image: lscr.io/linuxserver/qbittorrent:latest
    container_name: qbittorrent
    ports:
      - "8080:8080"
      - "6881:6881"
    volumes:
      - /mnt/media:/mnt/media
      - /home/user/docker/qbittorrent/config:/config
    restart: always
    networks:
      - media_network

  homarr:
    image: ghcr.io/homarr-labs/homarr:latest 
    container_name: homarr
    ports:
      - "7575:7575"
    volumes:
      - /home/user/docker/homarr/config:/config
    restart: always
    networks:
      - media_network
  flaresolverr:
    image: ghcr.io/flaresolverr/flaresolverr:latest
    container_name: flaresolverr
    restart: unless-stopped
    ports:
      - 8191:8191
    environment:
      - LOG_LEVEL=info


networks:
  media_network:
    driver: bridge
```

**Docker Commands**
- ```docker-compose up -d``` starts services
- ```docker-compose down``` shuts off services for troubleshooting
- ```docker ps``` shows running services
