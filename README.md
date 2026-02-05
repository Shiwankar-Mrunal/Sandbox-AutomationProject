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
  - Virtual Machines (VMs)
  - Virtual Networks (VNets)
  - Storage Accounts
- Environments are reproducible, version-controlled, and auditable

### 2. CI/CD Pipeline Integration
- Automated deployment using CI/CD pipelines (GitHub Actions)
- Pipelines are triggered by:
  - Code changes (push/PR)
  - Manual triggers
  - Scheduled runs
- Pipelines handle:
  - Infrastructure provisioning
  - Updates and reconfiguration
  - Validation and compliance checks

### 3. Slack Notifications
- Real-time alerts sent to Slack for:
  - Successful or failed provisioning
  - CI/CD pipeline status
  - Configuration drift detection
- Improves visibility and rapid incident response

### 4. Azure Monitor Integration
- Monitor sandbox environments using **Azure Monitor**
- Track:
  - Health and availability
  - Resource performance (CPU, memory, disk, network)
  - Logs and metrics in real time
- Alerts configured for threshold breaches

### 5. Configuration Drift Hunter
- Detects deviations between deployed infrastructure and desired state
- Periodic drift detection using:
  - Terraform plan checks or Ansible state validation
- Automatically flags non-compliant resources
- Helps maintain consistent and secure sandbox environments

### 6. Custom Dashboard
A centralized dashboard provides visibility into:
- CI/CD pipeline execution status
- Configuration drift status across sandbox environments
- Overall environment health and compliance

----
## working on verion two


########