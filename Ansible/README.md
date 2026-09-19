# Ansible

This directory contains the Ansible part of the DevOps Automation project.

The goal is to use Ansible as the central configuration management and automation platform for servers deployed in the lab.

## What Ansible will be used for

Ansible will handle tasks that happen after a server has been created and completed its initial Cloud-Init configuration.

Examples include:

* Installing packages
* Configuring services
* Managing users and permissions
* Deploying configuration files
* Starting and enabling services
* Applying repeatable server configurations
* Verifying that systems are in the expected state

## Planned setup

Ansible will run from a dedicated Ansible server.

The Ansible environment itself will eventually be containerized so that the configuration can be reproduced from files stored in this repository.

The planned structure will include:

* Ansible inventory
* Playbooks
* Roles
* Variables
* Configuration files
* Docker configuration for the Ansible environment

## Deployment flow

The expected deployment flow is:

```text
Proxmox
   ↓
VM created
   ↓
Cloud-Init
   ↓
Initial server configuration
   ↓
Ansible
   ↓
Final server configuration
```

Cloud-Init is responsible for preparing the server.

Ansible is responsible for configuring what the server should become.

## Project goal

The goal is not only to automate server configuration, but to build the Ansible environment in a way that is:

* Repeatable
* Understandable
* Version controlled
* Easy to expand
* Easy to demonstrate

The Ansible setup will be built gradually as the project develops.
