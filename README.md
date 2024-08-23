# Install-Docker

## Docker Installation Guide
This repository provides step-by-step instructions to install Docker on different operating systems, including yum-based (Red Hat family), apt-based (Debian family), and Windows.
Table of Contents

### Table of Contents
- Prerequisites
- Installing Docker on yum-based OS
- Installing Docker on apt-based OS
- Installing Docker on Windows
- Post-Installation Steps
- Uninstall Docker
- Prerequisites

### Prerequisites
Before installing Docker, ensure your system meets the following prerequisites:

- yum-based OS: CentOS, RHEL, Fedora, Amazon Linux
- apt-based OS: Ubuntu, Debian, Linux Mint
- Windows: Windows 10 64-bit: Pro, Enterprise, or Education (Build 1903 or later)

Ensure your system has an active internet connection and sufficient permissions to install software.

## Installing Docker on yum-based OS

Update your system:
```bash
sudo yum update -y
```

Install Docker:
```bash
sudo yum install docker -y
```

Start Docker service:
```bash
sudo systemctl start docker
```

Add your user to the Docker group:

This allows your user to run Docker commands without using sudo.
```bash
sudo usermod -aG docker $USER
```

Activate the Docker group:

Run the following command to apply the new group membership immediately:
```bash
newgrp docker
```

Change permissions for the Docker socket:

This command sets the Docker socket to be readable and writable by all users. Note: This step poses a security risk and is generally not recommended.
```bash
sudo chmod 777 /var/run/docker.sock
```


