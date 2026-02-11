# Automated Sandbox Environment Provisioning & Monitoring

## Overview :

This project provides an automated solution for creating, deploying, monitoring, and maintaining **sandbox cloud environments** using **Infrastructure as Code (IaC)**, **CI/CD pipelines**, and **real-time monitoring**.  

The solution ensures that sandbox environments are:
- Automatically provisioned and updated
- Continuously monitored for health and performance
- Protected against configuration drift
- Fully observable through dashboards and notifications

## Problem Statement : 

### Need for Isolated Environments:

- Development teams require separate, isolated environments (sandboxes) for testing and experimentation.

- Manual creation and maintenance of these environments is inefficient and prone to errors.

### Automation Requirement :

- There is a need for an automated system to provision and manage these environments.

- This system should use Infrastructure as Code (IaC) to ensure consistency and repeatability.

### CI/CD Integration :

- The automated system must integrate with CI/CD pipelines to deploy code and updates to the sandboxes seamlessly.

### Monitoring and Health Checks :

- The system should actively monitor the health and configuration of these sandbox environments.

- It should detect issues, failures, or deviations in real-time.

### Configuration Drift Detection :

- The system should identify configuration drift, i.e., differences between the intended and actual state of environments.

- Automated alerts or corrective actions may be required to maintain environment integrity.

### Visual Dashboard :

- Provide a real-time visual dashboard to:

- Show the status of sandboxes

- Highlight configuration deviations or issues

## Key Features

### 1. Infrastructure Automation
- Provision sandbox environments using  **Ansible**
- Supports creation of:
    - Resource Groups Creation
    - Networking Setup
    - SSH Key Generation
    - Virtual Machines (VMs)
    - Storage Accounts
    - CI/CD Integration Support
    - Environment Variables

- Environments are reproducible, version-controlled, and auditable
```n no of infra will create``` 

## Configure Playbook Variables:
### Set variables such as:

- rg_base_name – Base name for resource groups

- vnet_name, subnet, address_prefixes_vnet/subnet – Networking config

- vm_name, vm_size, admin_username – VM config

- storage – Storage account name prefix

### 2. CI/CD Pipeline Integration
- Automated deployment using CI/CD pipelines (GitHub Actions)
- Pipelines are triggered by:
  - Code changes (push/PR)
  - Manual triggers
- Pipelines handle:
  - Infrastructure provisioning

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
