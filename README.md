
# Automated Sandbox Environment Provisioning & Monitoring

## Overview

The Auto Sandbox project automates the creation and management of isolated sandbox environments, integrating provisioning tools like  Ansible with CI/CD pipelines. It provides real-time monitoring, configuration drift tracking, and alerting through platforms like Azure Monitor and Slack. A custom dashboard visualizes pipeline status and environment health, streamlining development and testing workflows.

The solution ensures that sandbox environments are:
- Automatically provisioned and updated
- Continuously monitored for health and performance
- Protected against configuration drift
- Fully observable through dashboards and notifications

## Objectives

- Automate sandbox creation using  Ansible to provision cloud resources (VMs, networks, storage).

- Integrate CI/CD pipelines to automatically deploy and   update sandboxes triggered by code changes or other events.

- Implement Slack notifications for alerts related to provisioning issues, failures, or configuration drift.

- Monitor sandbox environments using Azure Monitor for   health, performance, and availability in real-time.

- Implement Configuration Drift Hunter to detect deviations from the desired infrastructure state and maintain compliance.

- Create a custom dashboard to visualize:

  - CI/CD pipeline run status

  - Configuration drift status of sandbox environments

## 1. Infrastructure Automation(Provision sandbox environments using  **Ansible**)

 - Resource Group Creation
    ```
     Module: azure.azcollection.azure_rm_resourcegroup
    ```
  - Virtual Networks (VNets) Creation
    ```
     Module: azure.azcollection.azure_rm_virtualnetwork
    ```
  - Subnet Creation
    ```
     Module: azure.azcollection.azure_rm_subnet
    ```
  - Public Ip Creation
    ```
     Module: azure.azcollection.azure_rm_publicipaddress
    ```
  - NIC Creation Creation
    ```
     Module: azure.azcollection.azure_rm_networkinterface
    ```
  - SSH Key Creation
     ```
     Module: ansible.builtin.openssh_keypair
    ```
  - Virtual Machine Creation
    ```
     Module: azure.azcollection.azure_rm_virtualmachine
    ```
  - Storage Accounts Creation
    ```
     Module: azure_rm_storageaccount
    ```

    https://docs.ansible.com/projects/ansible/latest/collections/azure/azcollection/azure_rm_virtualmachine_module.html


### 2. CI/CD Pipeline Integration
- Automated deployment using CI/CD pipelines (GitHub Actions)
  - Set Up Python
  - Install Azure Ansible Collection
  ```
  ansible-galaxy collection install azure.azcollection --force
  ```
  - Install Azure SDK Dependencies for Ansible
  ```
    ~/.ansible/collections/ansible_collections/azure/azcollection/requirements.txt
  ```
  - Run Ansible Playbook
  ```
    ansible-playbook main.yml -e "ansible_python_interpreter=..."
  ```
  - Run Ansible Playbook in Drift Detection Mode
  - Notify Slack

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
- Helps maintain consistent and secure sandbox environments

### 6. Custom Dashboard
A centralized dashboard provides visibility into:
- CI/CD pipeline execution status
- Configuration drift status across sandbox environments
- Overall environment health and compliance

### 7. Future Scope 
- Can perfor using Terraform
- Multiple Cloud Support