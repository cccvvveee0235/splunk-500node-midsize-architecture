# 🚀 Basic Splunk Enterprise Installation on Linux

This guide provides step-by-step instructions for downloading, installing, configuring, and enabling autostart for Splunk Enterprise on Linux servers (Ubuntu/Debian and RHEL/CentOS/Rocky Linux).

---

## 📋 1. Prerequisites

Before starting the installation, ensure your server meets the system requirements and the required ports are accessible.

| Parameter | Lab / Demo Requirements | Production Requirements |
| :--- | :--- | :--- |
| **OS** | Ubuntu 20.04+ / RHEL 8+ / Debian 11+ | RHEL 8+ / Rocky Linux 9 |
| **CPU** | 2 Cores | 16 Cores |
| **RAM** | 4 GB | 32 GB |
| **Disk** | 20 GB SSD | 500 GB+ NVMe / High-IOPS SSD |

### Network Ports
* **`8000/tcp`** — Splunk Web Interface (HTTP/HTTPS).
* **`8089/tcp`** — Splunk Management Port (REST API & CLI).
* **`9997/tcp`** — Splunk Receiver Port (Incoming data from Splunk Forwarders).

---

## 📥 2. Download the Package

Download the installation package for your Linux distribution from official web site. Need account for splunk.com site.
Click Trials & Downloads. Choose Splunk Enterprise. For example my Linux server is Ubuntu 24.04.

## 📥 2. Install Splunk Package in Linux server.



