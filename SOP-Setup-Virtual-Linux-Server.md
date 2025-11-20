# Standard Operating Procedure for Setting Up a Virtual Linux Server for Web Application Testing

## PURPOSE OF THE DOCUMENT

This document outlines the standardized procedures for creating and configuring a virtual Linux server specifically designed for web application testing purposes. It ensures consistency, proper configurations, and adherence to security best practices while establishing a reliable testing environment.

## AUDIENCE

This document is intended for:
- System Administrators
- DevOps Engineers
- Quality Assurance Teams
- Development Teams
- IT Operations Staff involved in test environment setup

## APPROVAL TABLE

| Version | Date       | Name                 | Designation |
|---------|------------|----------------------|-------------|
| 1.0     | 2025-11-19 | [Your Name]          | Author      |
| 1.0     | 2025-11-19 | [Reviewer Name]      | Reviewer    |
| 1.0     | 2025-11-19 | [Approver Name]      | Approver    |

## SCOPE/OBJECTIVES

This SOP covers the complete process for setting up a virtual Linux server for web application testing, including:

1. Pre-deployment planning and resource assessment
2. Virtual machine creation and configuration
3. Ubuntu Server 22.04 LTS installation
4. Essential software stack installation for web application testing
5. Network and security configuration
6. Post-deployment verification and testing
7. Documentation and knowledge transfer

## ACCOUNTABILITY MATRIX

| Task/Steps | Responsible Person/Team | Emergency Contact | Non-Emergency Contact | Review/Approval |
|------------|-------------------------|-------------------|------------------------|-----------------|
| Pre-deployment Planning | DevOps Team | Phone: [Emergency #] | Email: devops-team@company.com | IT Manager |
| VM Creation & Configuration | System Administrators | Phone: [Emergency #] | Email: sysadmin@company.com | Infrastructure Lead |
| OS & Software Installation | DevOps Engineers | Phone: [Emergency #] | Email: devops-team@company.com | Development Manager |
| Security Configuration | Security Team | Phone: [Emergency #] | Email: security@company.com | CISO |
| Verification & Testing | QA Team | Phone: [Emergency #] | Email: qa-team@company.com | QA Manager |
| Documentation | Technical Writers | Phone: [Emergency #] | Email: docs@company.com | Project Manager |

## DEFINITIONS

- **SOP**: Standard Operating Procedure
- **VM**: Virtual Machine
- **LTS**: Long Term Support
- **LAMP Stack**: Linux, Apache, MySQL, PHP/Python/Perl
- **CI/CD**: Continuous Integration/Continuous Deployment
- **SSH**: Secure Shell
- **DNS**: Domain Name System

## EXECUTION STEPS

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
