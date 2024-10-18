# Home Lab Setup

This is a comprehensive overview of my home lab environment, which consists of various servers and devices configured to support multiple services and applications.

## 1. Main Server: HP ProDesk 400 G4
- **CPU**: Intel i3-6700
- **RAM**: 32GB
- **Storage**:
  - 512GB SSD for Proxmox OS
  - 2TB 2.5" HDD (used mainly for Frigate and LXC backups)
  - TrueNAS VM with HBA card passthrough for:
    - 4x 4TB HDDs for main storage
    - 256GB SSD for caching
- **Hardware**:
  - **Coral USB TPU**: For accelerating machine learning tasks (e.g., object detection in Frigate)
- **Virtual Machines (VMs)**:
  - TrueNAS VM for storage management
  - Other services:
    - **Frigate**: Real-time surveillance with object detection, accelerated by Coral USB TPU
    - **Jellyfin**: Media streaming server
    - **PhotoPrism**: AI-based photo management
    - **Nginx**: Web server and reverse proxy
    - **NextcloudPi**: Self-hosted file sharing and collaboration platform
    - **Vaultwarden**: Self-hosted password manager
    - **Pi-hole**: Network-wide ad blocker

## 2. Second Server: Lenovo ThinkCenter 710Q
- **CPU**: Intel i3-7100T
- **RAM**: 16GB
- **Storage**:
  - 1TB NVMe for OS
  - 1TB 2.5" HDD
- **Virtual Machines (VMs)**:
  - Home Assistant VM for home automation
  - Proxmox Backup Server VM for managing backups

## 3. Raspberry Pi 4
- **RAM**: 4GB
- **Storage**: 64GB SSD
- **Running Services**:
  - Docker containers, including Homer dashboard

## 4. Raspberry Pi 5
- **RAM**: 4GB
- **Storage**: 120GB SSD
- **Running Services**:
  - HyperHDR for advanced HDR lighting setups
  - Pi-hole for network-wide ad blocking

## 5. Networking Equipment
- **UniFi Cloud Gateway Ultra**: Network management and routing
- **2x UniFi AP LR**: Long-range wireless access points for Wi-Fi coverage
- **Netgear 8-port PoE switch**: Power-over-Ethernet for devices like access points
- **TP-Link 8-port managed switch**: For managing network traffic
- **TP-Link 8-port switch**: Basic network connectivity

## Overview
This home lab setup allows me to experiment with various applications and services while maintaining an efficient and organized environment. It's designed for both learning and practical applications in home automation, media consumption, and network management.
