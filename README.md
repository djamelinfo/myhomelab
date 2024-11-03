# Home Lab Setup

This is a comprehensive overview of my home lab environment, which consists of various servers and devices configured to support multiple services and applications.

<img src="https://github.com/djamelinfo/myhomelab/raw/main/images/IMG_20241102_163709229.jpg" alt="Rack Setup" width="400"/>

## 1. Main Server: HP ProDesk 400 G4 SFF running Proxmox

<img src="https://github.com/djamelinfo/myhomelab/raw/main/images/Screenshot_20241101_135806_Chrome.jpg" alt="Proxmox width="400"/>
- **Hardware**:
  - **CPU**: Intel i5-6500T
  - **RAM**: 32GB
  - **Storage Setup**:
    - **The motherboard has 2 SATA 3.0 connectors**:
      - 512GB SSD for Proxmox OS
      - 256GB SSD for caching
    - **PCIe to SAS HBA Card**: Used for 4x 4TB HDDs, passed through to the [**TrueNAS**](https://www.truenas.com/) VM for storage management.
    - **WiFi-M.2 to SATA 3.0 Adapter**: Used to connect:
      - 2TB 2.5" HDD, primarily for Frigate and LXC backups.
      - 256GB SSD for VM disk storege.
  - **Coral USB TPU**: For accelerating machine learning tasks (e.g., object detection in Frigate)
- **Virtual Machines (VMs)**:
  - [**Home Assistant**](https://www.home-assistant.io/): Home automation platform
    ![HomeAssistant](https://github.com/djamelinfo/myhomelab/raw/main/images/Homeassistat.jpg)
  - [**TrueNAS**](https://www.truenas.com/) VM for storage management
    ![TrueNas](https://github.com/djamelinfo/myhomelab/raw/main/images/Screenshot_20241102_173951_Chrome.jpg)
- **Other services (LXC)**:
    - [**Frigate**](https://frigate.video/): Real-time surveillance with object detection, accelerated by Coral USB TPU
      ![Frigat](https://github.com/djamelinfo/myhomelab/raw/main/images/Frigat.jpg)
    - [**Jellyfin**](https://jellyfin.org/): Media streaming server
      ![Jellyfin](https://github.com/djamelinfo/myhomelab/raw/main/images/Jellyfin.jpg)
    - [**PhotoPrism**](https://photoprism.app/): AI-based photo management
    - [**Nginx**](https://www.nginx.com/): Web server and reverse proxy
    - [**NextcloudPi**](https://ownyourbits.com/nextcloudpi/): Self-hosted file sharing and collaboration platform
    - [**Vaultwarden**](https://github.com/dani-garcia/vaultwarden): Self-hosted password manager
    - [**Gitea**](https://gitea.io/en-us/): Self-hosted Git service
    - [**Pi-hole**](https://pi-hole.net/): Network-wide ad blocker
      ![Frigat](https://github.com/djamelinfo/myhomelab/raw/main/images/pihole.jpg)



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
- **Storage**: 64GB SD Card
- **Running Services**:
  - [**Homer Dashboard**](https://github.com/bastienwirtz/homer): Docker containers, including a customizable dashboard
    ![Homer](https://github.com/djamelinfo/myhomelab/raw/main/images/homer.jpg)
  - [**Pi-hole**](https://pi-hole.net/): Network-wide ad blocker

## 4. Raspberry Pi 5
- **RAM**: 4GB
- **Storage**: 120GB SSD
- **Running Services**:
  - [**HyperHDR**](https://github.com/awawa-dev/HyperHDR): For advanced HDR lighting setups
  

## 5. Networking Equipment
- **UniFi Cloud Gateway Ultra**: Network management and routing
- **2x UniFi AP LR**: Long-range wireless access points for Wi-Fi coverage
- **Netgear 8-port PoE switch GS308PP**: Power-over-Ethernet for devices like access points
- **TP-Link 8-port managed switch TL-SG608E**: For managing network traffic
- **TP-Link 8-port switch TL-SG108**: Basic network connectivity

## Overview
This home lab setup allows me to experiment with various applications and services while maintaining an efficient and organized environment. It's designed for both learning and practical applications in home automation, media consumption, and network management.
