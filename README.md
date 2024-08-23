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

### Update your system:
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


## Installing Docker on apt-based OS


Follow these steps to install Docker on apt-based Linux distributions like Ubuntu and Debian:

Update your system:
```bash
sudo apt-get update
```

Install Docker:
```bash
sudo apt-get install docker.io -y
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

## Installing Docker on Windows

### Download Docker Desktop:

- Visit the Docker Desktop download page and download the installer for Windows.

### Run the Docker Desktop Installer:

- Double-click the installer to run it. Follow the on-screen instructions to complete the installation.

### Enable WSL 2 (Windows Subsystem for Linux):

- Docker Desktop requires WSL 2 as the backend. The installer will prompt you to enable it if it is not already enabled.

### Start Docker Desktop:

- Once installed, start Docker Desktop from the Start menu or desktop shortcut.

### Verify Docker Installation:

Open Command Prompt or PowerShell and run:
```bash
docker --version
```
This should display the Docker version, confirming that Docker is installed successfully.

## 
Here’s an updated README.md file that provides simplified instructions for installing Docker on both yum-based and apt-based Linux distributions, as well as on Windows.

README.md
Docker Installation Guide
This guide provides simple commands to install Docker on various operating systems, including yum-based Linux distributions (like CentOS and RHEL), apt-based Linux distributions (like Ubuntu and Debian), and Windows.

Table of Contents
Installing Docker on yum-based OS
Installing Docker on apt-based OS
Installing Docker on Windows
Post-Installation Verification
Notes
Installing Docker on yum-based OS
Follow these steps to install Docker on yum-based Linux distributions like CentOS and RHEL:

Update your system:

bash
Copy code
sudo yum update -y
Install Docker:

bash
Copy code
sudo yum install docker -y
Start Docker service:

bash
Copy code
sudo systemctl start docker
Enable Docker to start on boot:

bash
Copy code
sudo systemctl enable docker
Add your user to the Docker group:

This allows your user to run Docker commands without using sudo.

bash
Copy code
sudo usermod -aG docker $USER
Replace $USER with your actual username if running as a different user.

Activate the Docker group:

Run the following command to apply the new group membership immediately:

bash
Copy code
newgrp docker
Change permissions for the Docker socket:

This command sets the Docker socket to be readable and writable by all users. Note: This step poses a security risk and is generally not recommended.

bash
Copy code
sudo chmod 777 /var/run/docker.sock
Installing Docker on apt-based OS
Follow these steps to install Docker on apt-based Linux distributions like Ubuntu and Debian:

Update your system:

bash
Copy code
sudo apt-get update
Install Docker:

bash
Copy code
sudo apt-get install docker.io -y
Add your user to the Docker group:

This allows your user to run Docker commands without using sudo.

bash
Copy code
sudo usermod -aG docker $USER
Activate the Docker group:

Run the following command to apply the new group membership immediately:

bash
Copy code
newgrp docker
Change permissions for the Docker socket:

This command sets the Docker socket to be readable and writable by all users. Note: This step poses a security risk and is generally not recommended.

bash
Copy code
sudo chmod 777 /var/run/docker.sock


Installing Docker on Windows
Download Docker Desktop:

Visit the Docker Desktop download page and download the installer for Windows.
Run the Docker Desktop Installer:

Double-click the installer to run it. Follow the on-screen instructions to complete the installation.
Enable WSL 2 (Windows Subsystem for Linux):

Docker Desktop requires WSL 2 as the backend. The installer will prompt you to enable it if it is not already enabled.
Start Docker Desktop:

Once installed, start Docker Desktop from the Start menu or desktop shortcut.
Verify Docker Installation:

Open Command Prompt or PowerShell and run:

bash
Copy code
docker --version
This should display the Docker version, confirming that Docker is installed successfully.

## Post-Installation Verification

Verify Docker installation:

Run the following command to verify Docker is installed and working correctly:
```bash
docker --version
```

Run a test Docker container:

To confirm Docker is running properly, execute:
```bash
docker run hello-world
```
This command downloads a test image and runs it in a container. If everything is set up correctly, you should see a "Hello from Docker!" message.
