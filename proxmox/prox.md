This document outlines proxmox istallation and setup

## Instalation Guide
### 1. Installing Proxmox VE
**1.1 Create USB** 
- Download Proxmox [ISO](https://www.proxmox.com/en/downloads/category/iso-images-pve)
- Use Etcher to flab USB
**1.2 Install Proxmox**
- Used F12 to access Boot Menu
- Select Proxmox Graphical Interface
- Set hostname
  > jp.prox
- Create strong login
  > Will add yubikey authentification
- Set network config
  > see [Network Document](Networking/network.md)
- Finish install
- Access Web UI
  - http://192.168.68.70:8006

### 2. Add NAS
**2.1 HP UnRAID**
- Make sure sharing is enabled for folder
**2.2 On Proxmox**
- Go to Datacenter > Storage > Add > SMB/CIFS
- Set ID
- Server (IP of network drive)
- Select Share
### 3. Setup Ubuntu VM
**3.1 Download ISO**
- [Ubuntu ISO](https://ubuntu.com/download/server)
- Go to Web UI > local > ISO Image > Upload
**3.2 Create VM**
- General
  - Node
  - VM ID
  - Name
- OS
  - Ubuntu
- System
  - Keep Default
- Disk
  - Disk size: 50GB
- CPU
  - 2 cores
- Memory
  - 4GB
- Netowrk
  - Use default bridge
- Finish

## Issues

### Proxmox Install Failed - Could not detect drive
- **Problem**: During Proxmox install, drive could not be detected
- **Solution**: Drive was set in raid array, Go to BIOS and set array to ACHI
