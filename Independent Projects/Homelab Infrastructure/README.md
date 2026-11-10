# Homelab Infrastructure

My homelab is a continuously evolving environment used to develop hands-on experience with networking, virtualization, Linux, Windows Server, containerization, storage, monitoring, home automation, and local AI.

The environment is designed around network segmentation, virtualization, service redundancy, centralized storage, and self-hosted infrastructure.

## Infrastructure Overview

### Network

The network is built around a UniFi Cloud Gateway Fiber (UCG-Fiber), which serves as the primary gateway and routing device.

Connected infrastructure includes:

- UniFi UCG-Fiber
- UniFi 5G Backup
- UniFi U7 Pro XG Access Point
- UniFi Switch Flex Mini 2.5G
- Two Proxmox virtualization hosts
- Network Attached Storage (NAS)
- Dedicated local AI server

### Network Segmentation

The environment uses VLANs to separate devices and services based on their purpose. They include but are not limited to:

| VLAN | Purpose |
|------|---------|
| VLAN 20 | Servers |
| VLAN 40 | IoT |
| VLAN 50 | User Devices |

My AP broadcasts separate networks for trusted user devices and IoT devices.

My configured network segmentation allows IoT devices, servers, and user endpoints to be separated while allowing specifically required communication between networks.

## Virtualization

Two Proxmox hosts provide the primary virtualization platform for the environment.

### Proxmox Node 1

Primary workloads include:

- Primary AdGuard Home instance
- Media Stack
- Utility Stack

### Proxmox Node 2

Primary workloads include:

- Secondary AdGuard Home instance
- Home Assistant
- Windows 11 VM
- Windows Server 2025 VM

Running AdGuard Home on both Proxmox nodes provides DNS redundancy if either virtualization host or AdGuard instance becomes unavailable.

You can find more documentation on how I got started with Proxmox [here](https://github.com/NBarricelli/tech-journey/blob/main/Independent%20Projects/1.%20Virtualization/Documentation.md). My homelab has evolved significantly since this, but this file has notes on how I started.

## Media Stack

The Media Stack runs within an Ubuntu virtual machine and uses Docker to host multiple containerized applications.

Current services include but are not limited to:

- Jellyfin
- Seerr
- BookStack
- Mealie
- Additional media-related services

Jellyfin is a media server that allows me to organize, manage, and play digital media. Seerr is a service that make it easy for me to "request" specific types of media for Jellyfin. BookStack is my self-hosted wiki where I keep all the granular documentation about my homelab, network, and other related topics. Mealie is a self-hosted cookbook service.

## Utility Stack

The Utility Stack runs within an Ubuntu virtual machine and uses Docker to host infrastructure and administrative utilities.

Current services include but are not limited to:

- Uptime Kuma
- LibreSpeed
- Homarr
- Heimdall
- Additional infrastructure utilities

Uptime Kuma allows me to configure "heartbeats" for my homelab services and send notifications when something goes down. LibreSpeed is an internal speedtest service, which is useful when troubleshooting network issues. Homarr serves primarily as an administrative dashboard, while Heimdall provides a simplified dashboard and bookmark interface for non-admins. This is useful as it allows me to have my own dashboard to monitor homelab performance and other metrics, while others who just need an easy way to get to Jellyfin or Mealie have a dedicated dashboard for that.

## Storage and Backup

A dedicated NAS provides centralized storage for personal data and infrastructure backups.

The NAS stores:

- Personal photos, videos, and files
- Proxmox host and virtual machine backups

## Local AI

A dedicated Ubuntu system is used for experimenting with locally hosted artificial intelligence models.

The system currently uses Ollama to run and evaluate local language models; however, as this discipline is constantly and rapidly evolving, I am always looking for more efficient platforms and engines to run LLMs.

## Goals

This homelab provides a practical environment for developing and maintaining experience with:

- Network architecture
- VLAN segmentation
- Firewall policy
- Virtualization
- Linux administration
- Windows administration
- Windows Server
- Docker
- DNS
- Infrastructure monitoring
- Storage and backup
- Service redundancy
- Home automation
- Local AI infrastructure
