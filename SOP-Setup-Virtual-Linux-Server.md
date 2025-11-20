# Standard Operating Procedure (SOP)
## Setup a Virtual Linux Server for Web Application Testing
**Version:** 1.0  
**Date:** 2025-11-19  

---

## 1. Purpose
This Standard Operating Procedure (SOP) describes the steps required to create, configure, and validate a virtual Linux server using Ubuntu Server 22.04 on VMware Workstation. The server will be used for basic web application testing using an Nginx + PHP environment. This SOP ensures consistent and repeatable deployment.

---

## 2. Scope
This document applies to:
- Students in IT, networking, cybersecurity, or system administration
- IT administrators preparing lab virtual machines
- Anyone responsible for creating Linux test servers

This SOP includes:
- Virtual machine creation  
- Ubuntu Server installation  
- Networking setup  
- Installation of Nginx & PHP  
- Verification and documentation steps  

---

## 3. Accountability Matrix

| Task / Step | Responsible Person | Approver |
|------------|-------------------|----------|
| Create VM | Student | Instructor |
| Install OS | Student | Instructor |
| Install web environment | Student | Instructor |
| Network & security configuration | Student | Instructor |
| Documentation | Student | Instructor |

---

## 4. Definitions

| Term | Description |
|------|-------------|
| VM | Virtual Machine |
| ISO | OS installation image |
| LTS | Long Term Support version of Ubuntu |
| Nginx | High-performance web server |
| PHP-FPM | FastCGI Process Manager for PHP |
| NAT | Network Address Translation mode in VMware |

---

## 5. Procedure Steps

---

### **Step 1: Pre-Setup Preparation**
1. Download Ubuntu Server 22.04 LTS ISO.  
2. Ensure VMware Workstation is installed.  
3. Recommended resources:
   - 2 CPU cores  
   - 4 GB RAM  
   - 25 GB disk space  
   - NAT network mode  

---

### **Step 2: Create a Virtual Machine in VMware Workstation**
1. Open VMware Workstation → **Create a New Virtual Machine**.  
2. Select **Typical (recommended)**.  
3. Choose **Installer disc image (ISO)** and load Ubuntu 22.04 ISO.  
4. Select **Linux → Ubuntu 64-bit**.  
5. Name the VM: `web-test-ubuntu`.  
6. Set disk to **25 GB** (single file recommended).  
7. Customize hardware:
   - Memory: 4096 MB  
   - Processor: 2 cores  
   - Network Adapter: NAT  
8. Finish and start the VM.

---

### **Step 3: Install Ubuntu Server 22.04**
1. Select **Install Ubuntu Server**.  
2. Set language and keyboard.  
3. Network: select DHCP or set static IP.  
4. Hostname: `web-test-01`.  
5. Create user (example: `student`).  
6. Use default storage layout.  
7. Select *Install OpenSSH Server*.  
8. Reboot the VM after installation.

---

### **Step 4: System Updates and Tools**
Update system:

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install net-tools curl git unzip -y
sudo apt install nginx -y
sudo systemctl enable nginx
sudo systemctl start nginx
systemctl status nginx
sudo apt install php-fpm php-cli php-common php-mysql -y
php -v
sudo bash -c 'echo "<?php phpinfo(); ?>" > /var/www/html/info.php'
sudo systemctl restart nginx
ip a
http://<VM-IP>/info.php
sudo rm /var/www/html/info.php
sudo ufw allow 'Nginx Full'
sudo ufw enable

