# Cloud-Init & Ansible Automated Deployment

This project is a school showcase focused on demonstrating what can be automated using **Cloud-Init** and **Ansible**.

The hypervisor used for the project is **Proxmox**, but Proxmox is only used as the platform for running the virtual machines. The main focus is the automation around Cloud-Init and Ansible.

## Planned setup

The environment will contain:

- A Proxmox hypervisor
- An Ubuntu Server running Ansible
- A web server providing a simple deployment interface
- Multiple Cloud-Init configuration files for different server types
- Multiple Ansible playbooks for further configuration

The Ansible server will connect to the Proxmox host over SSH and run the required shell commands to create and configure virtual machines.

The web interface will allow a developer to request a new server and specify values such as:

- Hostname
- Server type
- CPU count
- RAM
- Disk size
- Network

The web service will then send the request to the Ansible server, which will start the required playbook with the selected variables.

## Cloud-Init

Different Cloud-Init YAML files will be created for selected server types.

These files will be used to demonstrate features such as:

- User and SSH key creation
- Hostname configuration
- Package installation
- Service configuration
- File creation
- First-boot commands
- Server-specific setup

Values such as hostname and other server-specific settings will be generated dynamically during deployment.

A separate NoCloud/Cloud-Init metadata server is also planned, allowing manually created virtual machines on a specific network to retrieve Cloud-Init configuration without using Proxmox's built-in Cloud-Init drive.

## Intended deployment flow

```text
Developer
    |
    v
Web Interface
    |
    | POST request
    v
Ansible Server
    |
    | SSH
    v
Proxmox Host
    |
    | Create VM
    | Apply Cloud-Init configuration
    | Start VM
    v
New Virtual Machine
    |
    | Cloud-Init
    v
Initial Server Configuration
    |
    | SSH
    v
Ansible
    |
    v
Fully Configured Server