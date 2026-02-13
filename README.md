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

# Key Features

# 1. Infrastructure Automation
- Provision sandbox environments using  **Ansible**
- Supports creation of:
    - Resource Groups Creation
    - Networking Setup
    - SSH Key Generation
    - Virtual Machines (VMs)
    - Storage Accounts
    - CI/CD Integration Support
    - Environment Variables

- Environments are reproducible, version-controlled, and auditable.

- ``` 'n' no of infra will create``` 

# 2. CI/CD Pipeline Integration

## Overview : 

- Choose how many Resource Groups to create (1–10)
- Define a base name
- Automatically tag resources
- Detect configuration drift
- Send Slack notifications
- Upload execution logs as artifacts
- The workflow is manually triggered using workflow_dispatch.

### Required Inputs :

- rg_count
- rg_base_name

### End-to-End Flow : 

- User triggers workflow manually
- Inputs are validated
- Azure Ansible playbook provisions RGs
- Logs are stored as artifacts
- Drift detection check runs
- Slack notifications are sent
- Resource group names are exported as environment variables


# 3. Slack Notifications
- Sends Slack notifications after sandbox Resource Groups are provisioned.
- Sends real-time updates to Slack
- Enhances visibility and collaboration

# 4. Azure Monitor Integration
- Monitor sandbox environments using **Azure Monitor**
- Track:
  - Health and availability
  - Resource performance (CPU, memory, disk, network)
  - Logs and metrics in real time
- Alerts configured for threshold breaches

# 5. Configuration Drift Hunter
- Detects deviations between deployed infrastructure and desired state
- Periodic drift detection using:
  -  Ansible state validation
- Helps maintain consistent and secure sandbox environments

# 6. Custom Dashboard
A centralized dashboard provides visibility into:
- Configuration drift status across sandbox environments
- Overall environment health and compliance

# TTL (Time To Live ) Lifecycle  : 

```The lifecycle is calculated using the create_date tag assigned to each resource group.```

This helps to reduce : 
- Reduce Azure costs
- Automatically clean up Dev/Test environments
- Enforce temporary environment policies
- Support CI/CD temporary deployments

## How it works :

- Gets the current date.
- Reads the create_date tag from each resource group.

### Required Tags :

  - create_date
  - Environment

### Calculates  :

    - Age in days
    - End-of-life date
    - Remaining days
    - Deletes the resource group if TTL has expired.
    - lifecycle information.

### Lifecycle Logic :

  ### For each resource group 

    AgeDays = Today − Create Date

    EndOfLifeDate = Create Date + TTL

    RemainingDays = EndOfLifeDate − Today

### Testing On basis of Time

|Sr. No.  | No. Of Environment | Total Time |     Maximum TimeTaken Task          | Time Taken | SecondMaximum TimeTaken Task | Time Taken |
|  ---    |         ---         |   ---      |          ---                        |     ---    |              ---             |      ---   |
|         |                     |            |                                     |            |                              |            |
|  1.     |      5              |   14m20s   | Run Ansible playbook (Provisioning) |   9m14s    |      Drift Detection Mode    |   3ms      |
| ex.     | 5(already created)+1  |   11m14s   |                                     |   5m26s    |                              |   3m48s    |
|         |                     |            |                                     |            |                              |            |
|   2.    |       7             |   18m44s   | Run Ansible playbook (Provisioning) |   12m23s   |      Drift Detection Mode    |   4m14s    |
|         |                     |            |                                     |            |                              |            |
|   3.    |       10            |   27m48s   | Run Ansible playbook (Provisioning) |   19m25s   |      Drift Detection Mode    |   6m9s     |


# Conclusion : 

- Able to create 'n' no. of environment
- 'n' no of environment will be notify on slack.
- Having Powershell Script which run daily to check resources for deletion.
-  If Resources are already created and one resource gruop newly attached to create  ```Run Ansible playbook (Provisioning)``` take less time compare to previous task becuuse ansible feature ```BUT``` ```Drift Detection Mode``` task take more time compare to previous task
