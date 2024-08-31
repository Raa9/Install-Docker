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

### Prerequisites
Before installing Docker, ensure your system meets the following prerequisites:

- yum-based OS: CentOS, RHEL, Fedora, Amazon Linux
- apt-based OS: Ubuntu, Debian, Linux Mint
- Windows: Windows 10 64-bit: Pro, Enterprise, or Education (Build 1903 or later)

Ensure your system has an active internet connection and sufficient permissions to install software.

# Installing Docker on yum-based OS

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


# Installing Docker on apt-based OS


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

# Installing Docker on Windows

### Download Docker Desktop:

- Visit the Docker Desktop download page and download the installer for Windows.

### Enable wsl 
step 1:
 - click on start menu 
 - search 'turn windows on or off' and open
 - check the box of windows hypervisor platform and windows subsystem for linux
 - click ok 
 - restart the system 
step 2:
- open cmd as administrator 
- run the command and check the wsl 
  '''bash
  wsl --status
  '''
- update the wsl
  '''bash
  wsl --update
  '''

### install the docker desktop 
- once it is installed restart the system 

### Start Docker Desktop:

- start Docker Desktop from the Start menu or desktop shortcut.

### Verify Docker Installation:

Open Command Prompt or PowerShell and run:
```bash
docker --version
```
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

## uninstall Docker

Stop Docker Service:

First, stop the Docker service if it's running:
```bash
sudo systemctl stop docker
```

Uninstall Docker Packages:

Remove Docker and its associated packages:
```bash
sudo yum remove -y docker \
                   docker-client \
                   docker-client-latest \
                   docker-common \
                   docker-latest \
                   docker-latest-logrotate \
                   docker-logrotate \
                   docker-engine
```

Remove Docker Dependencies:

You may also want to remove Docker dependencies and related packages:
```bash
sudo yum autoremove -y
```

Remove Docker Files and Directories:

Clean up any residual Docker files and directories:
```bash
sudo rm -rf /var/lib/docker
sudo rm -rf /var/lib/containerd
```

### Optional: Remove Docker Group

If you created a Docker group and want to remove it:
```bash
sudo groupdel docker
```

Confirm Uninstallation
```bash
docker --version
```

# Uninstalling Docker on Ubuntu (Linux)

Stop Docker Service:
```bash
sudo systemctl stop docker
```

Uninstall Docker Packages:
```bash
sudo apt-get purge -y docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

Remove Docker Dependencies:
```bash
sudo apt-get autoremove -y
```

Remove Docker Files and Directories:
```bash
sudo rm -rf /var/lib/docker
sudo rm -rf /var/lib/containerd
sudo rm -rf /etc/docker
sudo rm -rf /var/run/docker.sock
```

Remove Docker Group (Optional):
```bash
sudo groupdel docker
```

Verify Uninstallation:
```bash
docker --version
```

# Uninstalling Docker on Windows

Stop Docker Desktop:
Ensure Docker Desktop is closed. Right-click the Docker Desktop icon in the system tray and select "Quit Docker Desktop."

Uninstall Docker Desktop:
- Open the Control Panel.
- Navigate to Programs > Programs and Features.
- Locate Docker Desktop in the list of installed programs, right-click on it, and select Uninstall.
- Follow the prompts to complete the uninstallation process.

Remove Docker Files (Optional):
Docker Desktop on Windows stores configuration and other data in several locations. You can manually delete these files if you want to ensure a complete removal:
 - Docker Desktop Configuration Files:
   Delete the Docker configuration folder located in your user profile directory:
   ```bash
   C:\Users\<YourUsername>\AppData\Roaming\Docker
   C:\Users\<YourUsername>\AppData\Local\Docker
   C:\Users\<YourUsername>\.docker
   ```
 - Virtual Machine Files (if using WSL 2 backend):
   Delete any WSL 2 distribution data from Docker. This may be stored in:
   ```bash
   C:\Users\<YourUsername>\AppData\Local\Docker\wsl
   ```

Remove Docker Context in WSL 2 (Optional):
If you were using Docker with WSL 2 integration and want to clean up completely, you can remove Docker context:
 - Open PowerShell as an administrator.
 - Run the following command to remove the Docker context:
   ```bash
   wsl --unregister docker-desktop
   wsl --unregister docker-desktop-data

Verify Uninstallation:

Restart your computer and confirm that Docker Desktop has been completely removed.
