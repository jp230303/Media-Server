# Homelab Hardware Specs
This document outlines hardware used in my homelab.

## Server

### Current Media Server
- **Model**: HP EliteDesk 800 G3 SFF
- **CPU**: Intel Core i5-4570 CPU @ 3.20GHz
- **RAM**: 24GB DDR3
- **Storage**:
  - 1TB SSD (Cache)
  - 2 4TB HDD (Media array)
- ***GPU**: NVIDIA Quadro P400 (Jellyfin hardware transcoding)
- **OS**: UnRAID

### Future Media Server
- **Model**: Dell Optiplex 5050 Micro
- **CPU**: Intel core i5-6500T
- **RAM**: 16GB DDR4
- **Storage**: 256GB NVMe
- **Purpose**: Proxmox, Media server, Kali, pfsense.

## Networking gear

### Router
- **Model**: TP-Link Deco W6000
- **Topology**: Mesh, secondary unit in room

### Switch
- **Model**:  TP-Link SG105
- **Type**: 5 -Port Gigabit Unmanaged
- **Purpose**: Connects all devices including NAS and Media Server

## NIC
- **Model**: TP-Link TX201
- **Type**: 2.5 Gigabit PCIe NIC
- **Purpose**: Installed in NAS, allows for gigabit connectivty

## Future Plans

- Upgrade HDDs to 2 8TB
- Replace HP with dedicated NAS (more power efficient)
- Yubikey Authentification
