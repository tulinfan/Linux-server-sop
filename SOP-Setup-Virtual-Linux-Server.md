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

### Step 1: Pre-deployment Planning and Assessment

#### Step 1.1: Define Testing Requirements
- Determine the specific web application testing needs (functional, performance, security, etc.)
- Identify required testing frameworks and tools
- Estimate expected user load and performance requirements

#### Step 1.2: Plan Resource Allocation
- Allocate 4 vCPU cores, 8GB RAM, and 50GB storage for optimal performance
- Select high-performance datastore with SSD storage
- Plan for network configuration with static IP assignment
- Reserve hostname: `web-test-app-01`

#### Step 1.3: Stakeholder Communication
- Coordinate with development team for specific testing requirements
- Consult with security team for compliance requirements
- Confirm testing schedule with QA team

### Step 2: Virtual Machine Creation and Configuration

#### Step 2.1: Access Virtualization Platform
- Login to VMware vSphere Client or equivalent hypervisor management console
- Navigate to the appropriate cluster or host for test environments

#### Step 2.2: Create New Virtual Machine
- Select "Create New Virtual Machine"
- Choose compatibility: ESXi 7.0 and later
- Guest OS family: Linux
- Guest OS version: Ubuntu Linux (64-bit)

#### Step 2.3: Configure Virtual Machine Settings
- Name: `web-test-app-01`
- Location: `[Your Datacenter]/Test Environment/`
- CPU: 4 vCPUs
- Memory: 8192 MB RAM
- Hard disk: 50 GB (Thin Provisioning)
- Network: `Test-Network` VLAN
- CD/DVD: Connect to Ubuntu 22.04 LTS ISO file

### Step 3: Ubuntu Server Installation

#### Step 3.1: Start Installation
- Power on the virtual machine
- Boot from Ubuntu 22.04 LTS installation media
- Select "Ubuntu Server" installation type

#### Step 3.2: Configure Operating System
- Keyboard layout: US English
- Network configuration:
  - Hostname: `web-test-app-01`
  - Domain: `test.company.com`
- User account:
  - Username: `testadmin`
  - Full name: `Test Administrator`
  - Password: `[Secure Password]`
- Partition disks: Use entire disk with LVM
- Profile setup: Install OpenSSH server

### Step 4: Essential Software Stack Installation

#### Step 4.1: Update System and Install Base Packages
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y curl wget vim git unzip net-tools
