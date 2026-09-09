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
| **Disk** | 50 GB HDD | 500 GB+ NVMe / High-IOPS SSD |

### Network Ports
* **`8000/tcp`** — Splunk Web Interface (HTTP/HTTPS).
* **`8089/tcp`** — Splunk Management Port (REST API & CLI).
* **`9997/tcp`** — Splunk Receiver Port (Incoming data from Splunk Forwarders).

---

## 1. Download the Package

Download the installation package for your Linux distribution from official web site. Need account for splunk.com site.
Click Trials & Downloads. Choose Splunk Enterprise. For example my Linux server is Ubuntu 24.04.

<img src="../assets/Splunk installation.JPG" alt="Splunk installation" >

<img src="../assets/Splunk installation2.JPG" alt="Splunk installation" >

## 2. Transferring the Installer Package via SCP

After downloading the Splunk Enterprise `.deb` installer package from the official [Splunk Website](https://www.splunk.com) to your local workstation, upload it to the target Linux server using Secure Copy Protocol (`scp`).


### Command Execution (Run on Local Machine):
```cli```

scp splunk-10.x.x-xxxxxx-linux-xxx-amd64.deb user@<SERVER_IP>:/tmp/


<img src="../assets/Splunk installation3.JPG" alt="Splunk installation" >


    scp - Secure Copy utility that leverages SSH to transfer files securely between remote hosts.

    splunk-10.x.x-xxxxxx-linux-264-amd64.deb - The relative or absolute file path to the Splunk package on your local computer.

    user@<SERVER_IP> - The SSH username and IP address/hostname of the target server.

    :/tmp/ - The target directory on the remote server where the installer package will be stored.

## 3. Package Installation via DPKG

Connect to your target server via SSH, navigate to the upload directory, and install the package using the Debian Package Manager (`dpkg`).


### Command Execution (Run on Target Server):
```cli```

cd /tmp
sudo dpkg -i splunk-10.x.x-xxxxxx-linux-xxx-amd64.deb


<img src="../assets/Splunk Installation5.JPG" alt="Splunk installation" >


    cd /tmp - Changes the working directory to /tmp where the installer file was uploaded.

    sudo - Executes the command with elevated root privileges (required for system-wide software installation).

    dpkg - The core package management system for Debian-based Linux distributions.

    -i (or --install) - Instructs dpkg to unpack and install the specified .deb package.

    💡 Installation Location: By default, Splunk installs all binaries, default configurations, scripts, and libraries into the /opt/splunk directory.

## 4. First Launch & Administrator Account Setup

Navigate to the Splunk binary directory and launch the initial setup process. During this step, you will accept the license agreement and configure the primary administrator credentials.


### Command Execution (Run on Target Server):
```cli```

cd /opt/splunk/bin
sudo ./splunk start --accept-license --run-as-root


<img src="../assets/Splunk Installation6.JPG" alt="Splunk installation" >

<img src="../assets/Splunk Installation7.JPG" alt="Splunk installation" >


    cd /opt/splunk/bin - Moves into the directory containing Splunk executable binaries.

    ./splunk start - Initiates the Splunk service startup sequence, including environment checks, database initializations, and process spawning.

    --accept-license - Automatically accepts the Splunk End User License Agreement (EULA), bypassing the requirement to manually scroll through the text.

    --run-as-root - Explicitly permits Splunk to run under the root superuser account without throwing a safety prompt/warning.

## 5. Enabling Systemd Autostart (Boot-Start)

To ensure Splunk starts automatically whenever the server reboots or restarts, configure the system service manager (`systemd`).


### Command Execution (Run on Target Server):
```cli```

cd /opt/splunk/bin
./splunk enable boot-start


<img src="../assets/Splunk Installation8.JPG" alt="Splunk installation" >

    enable boot-start - Creates the necessary systemd unit files (or init.d scripts) and system symlinks so the Splunk background service is automatically managed by the OS.

## 6. Accessing Splunk Web Interface

Once the service is active, open your web browser to access the Splunk Web management portal.

### Command Execution (Run on Target Server):
```cli```

http://<YOUR_SERVER_IP>:8000

<img src="../assets/Splunk Installation9.JPG" alt="Splunk installation" >

    Enter Username: admin (or the username created in Step 4).

    Enter Password: The password created in Step 4.

