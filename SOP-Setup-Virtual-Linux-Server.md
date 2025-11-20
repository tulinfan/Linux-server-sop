# Standard Operating Procedure (SOP)
## Setup a Virtual Linux Server for Web Application Testing
**Version:** 1.0  
**Date:** 2025-11-19  

---

## 1. Purpose
This Standard Operating Procedure (SOP) describes the steps required to create, configure, and validate a virtual Linux server using Ubuntu Server 22.04 on VMware Workstation. The server will be used for basic web application testing using an Nginx + PHP environment. The goal is to ensure repeatable, consistent, and efficient setup for students or IT personnel.

---

## 2. Scope
This SOP applies to:
- Students in IT, networking, and system administration programs  
- IT administrators preparing lab or testing environments  
- Anyone responsible for creating Linux virtual machines for testing purposes  

This document includes:
- VM creation in VMware Workstation  
- Installation of Ubuntu Server 22.04  
- Basic networking configuration  
- Installation of Nginx + PHP for web testing  
- Verification and documentation steps  

---

## 3. Accountability Matrix

| Task / Step | Responsible Person | Approver |
|------------|-------------------|----------|
| Create VM in VMware Workstation | Student | Instructor |
| Install Ubuntu Server | Student | Instructor |
| Configure Web Testing Environment | Student | Instructor |
| Security & network configuration | Student | Instructor |
| Documentation & reporting | Student | Instructor |

---

## 4. Definitions

| Term | Meaning |
|------|---------|
| VM | Virtual Machine |
| ISO | Installation image file for OS setup |
| LTS | Long Term Support version of Ubuntu |
| Nginx | A lightweight web server used for hosting applications |
| PHP-FPM | FastCGI Process Manager used to run PHP applications |

---

## 5. Procedure Steps

---

### **Step 1: Pre-Setup Preparation**
1. Download the Ubuntu Server 22.04 LTS ISO file from the official Ubuntu website.
2. Ensure VMware Workstation is installed.
3. Recommended VM resources:
   - **CPU**: 2 cores  
   - **RAM**: 4 GB  
   - **Disk**: 25 GB  
   - **Network**: NAT or Bridged  

---

### **Step 2: Create a Virtual Machine in VMware Workstation**
1. Open **VMware Workstation** → Click **Create a New Virtual Machine**.
2. Select **Typical (recommended)**.
3. Choose **Installer disc image (ISO)** and select the Ubuntu 22.04 ISO.
4. Choose guest OS type: **Linux → Ubuntu 64-bit**.
5. Set VM name, e.g., `web-test-ubuntu`.
6. Allocate **25 GB** disk space.
7. Customize hardware:
   - Memory → 4096 MB  
   - Processors → 2 cores  
   - Network Adapter → NAT  
8. Finish and power on the VM.

---

### **Step 3: Install Ubuntu Server 22.04**
1. Select **Install Ubuntu Server**.
2. Choose language and keyboard settings.
3. Network configuration:
   - Default DHCP, or  
   - Configure static IP if required.
4. Enter hostname: `web-test-01`.
5. Create user (example: `student`).
6. Choose default storage layout.
7. Enable **OpenSSH Server**.
8. Reboot after installation completes.

---

### **Step 4: System Updates and Tools**
Run updates:

```sudo apt update && sudo apt upgrade -y```

---

### **Step 5: Install common tools**
run the command：

```sudo apt install net-tools curl git unzip -y```

---

### **Step 6: Install Web Test Environment (Nginx + PHP)**
run the command：

```sudo apt install nginx -y
sudo systemctl enable nginx
sudo systemctl start nginx
```






