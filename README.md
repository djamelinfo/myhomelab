# Home Lab Setup

This is a comprehensive overview of my home lab environment, which consists of various servers and devices configured to support multiple services and applications.
![Rack Setup](https://github.com/djamelinfo/myhomelab/raw/main/IMG_20241031_151244038.jpg)

## 1. Main Server: HP ProDesk 400 G4 SFF
- **Hardware**:
  - **CPU**: Intel i5-6500T
  - **RAM**: 32GB
  - **Storage Setup**:
    - **SATA 3.0 Connectors**: The motherboard has 2 SATA 3.0 connectors:
      - 512GB SSD for Proxmox OS
      - 256GB SSD for caching
    - **PCIe to SAS HBA Card**: Used for 4x 4TB HDDs, passed through to the [**TrueNAS**](https://www.truenas.com/) VM for storage management.
    - **WiFi-M.2 to SATA 3.0 Adapter**: Used to connect:
      - 2TB 2.5" HDD, primarily for Frigate and LXC backups.
      - 256GB SSD for VM disk storege.
  - **Coral USB TPU**: For accelerating machine learning tasks (e.g., object detection in Frigate)
- **Virtual Machines (VMs)**:
  - [**Home Assistant**](https://www.home-assistant.io/): Home automation platform
  - [**TrueNAS**](https://www.truenas.com/) VM for storage management
- **Other services (LXC)**:
    - [**Frigate**](https://frigate.video/): Real-time surveillance with object detection, accelerated by Coral USB TPU
    - [**Jellyfin**](https://jellyfin.org/): Media streaming server
    - [**PhotoPrism**](https://photoprism.app/): AI-based photo management
    - [**Nginx**](https://www.nginx.com/): Web server and reverse proxy
    - [**NextcloudPi**](https://ownyourbits.com/nextcloudpi/): Self-hosted file sharing and collaboration platform
    - [**Vaultwarden**](https://github.com/dani-garcia/vaultwarden): Self-hosted password manager
    - [**Gitea**](https://gitea.io/en-us/): Self-hosted Git service
    - [**Pi-hole**](https://pi-hole.net/): Network-wide ad blocker

![Proxmox](https://github.com/djamelinfo/myhomelab/raw/main/Screenshot_20241101_135806_Chrome.jpg).

## 2. Second Server: Lenovo ThinkCenter 710Q
- **CPU**: Intel i3-7100T
- **RAM**: 16GB
- **Storage**:
  - 1TB NVMe for OS
  - 1TB 2.5" HDD
- **Virtual Machines (VMs)**:
  - [**Proxmox Backup Server**](https://www.proxmox.com/en/proxmox-backup-server): For managing backups

## 3. Raspberry Pi 4
- **RAM**: 4GB
- **Storage**: 64GB SSD
- **Running Services**:
  - [**Homer Dashboard**](https://github.com/bastienwirtz/homer): Docker containers, including a customizable dashboard

## 4. Raspberry Pi 5
- **RAM**: 4GB
- **Storage**: 120GB SSD
- **Running Services**:
  - [**HyperHDR**](https://github.com/awawa-dev/HyperHDR): For advanced HDR lighting setups
  - [**Pi-hole**](https://pi-hole.net/): Network-wide ad blocker

## 5. Networking Equipment
- **UniFi Cloud Gateway Ultra**: Network management and routing
- **2x UniFi AP LR**: Long-range wireless access points for Wi-Fi coverage
- **Netgear 8-port PoE switch**: Power-over-Ethernet for devices like access points
- **TP-Link 8-port managed switch**: For managing network traffic
- **TP-Link 8-port switch**: Basic network connectivity

## Overview
This home lab setup allows me to experiment with various applications and services while maintaining an efficient and organized environment. It's designed for both learning and practical applications in home automation, media consumption, and network management.
