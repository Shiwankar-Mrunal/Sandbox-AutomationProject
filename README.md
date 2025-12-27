# Automated Sandbox Environment Provisioning & Monitoring

## Overview

This project provides an automated solution for creating, deploying, monitoring, and maintaining **sandbox cloud environments** using **Infrastructure as Code (IaC)**, **CI/CD pipelines**, and **real-time monitoring**.  

The solution ensures that sandbox environments are:
- Automatically provisioned and updated
- Continuously monitored for health and performance
- Protected against configuration drift
- Fully observable through dashboards and notifications

## Key Features

### 1. Infrastructure Automation
- Provision sandbox environments using  **Ansible**
- Supports creation of:
  - Resource Group
  - Virtual Networks (VNets)
  - Subnet
  - Public Ip
  - NIC
  - SSH Key
  - Virtual Machine
  - Storage Accounts
  - Worksppace
- Environments are reproducible
### 2. CI/CD Pipeline Integration
- Automated deployment using CI/CD pipelines (GitHub Actions)
- Pipelines are triggered by:
  - Download Python
  - Install Azure Ansible Collection
  - Azure SDK dependencies
  - Run Ansible Playbook

### 3. Slack Notifications
- Real-time alerts sent to Slack for:
  - Successful or failed provisioning
  - Configuration drift detection

### 4. Azure Monitor Integration
- Monitor sandbox environments using **Azure Monitor**

  - Health and availability
  - Resource performance (CPU, memory, disk, network)
  - Logs and metrics in real time

### 5. Configuration Drift Hunter
- Detects deviations between deployed infrastructure and desired state
- Periodic drift detection using:
- Helps maintain consistent and secure sandbox environments

### 6. Custom Dashboard
A centralized dashboard provides visibility into:
- CI/CD pipeline execution status
- Configuration drift status across sandbox environments
- Overall environment health and compliance

##########