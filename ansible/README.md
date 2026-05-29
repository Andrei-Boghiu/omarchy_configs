# Ansible Provisioning

This directory contains Ansible playbooks used to provision and configure Omarchy Linux systems.

## Overview

Each machine in the infrastructure has a distinct role and requires a different set of packages, services, and configurations. Rather than managing a shared inventory, all playbooks target the local machine (`localhost`) and are intended to be executed directly on the system being provisioned.

## Playbooks

| Playbook                       | Purpose                                                                            |
| ------------------------------ | ---------------------------------------------------------------------------------- |
| `general-purpose-playbook.yml` | Installs and configures common tools and services required on all Omarchy systems. |
| `compute-node-playbook.yml`    | Installs and configures software specific to the compute node.                     |
| `control-node-playbook.yml`    | Installs and configures software specific to the control node.                     |

## Prerequisites

Before running any playbook, ensure the following packages are installed:

### Update the Package Database

```bash
sudo pacman -Sy
```

### Install Ansible

```bash
sudo pacman -S ansible
```

### Install Ansible Collections

Some playbooks use community-maintained Ansible collections, including support for installing AUR packages in an idempotent manner.

Install the required collections:

```bash
ansible-galaxy collection install community.general
ansible-galaxy collection install kewlfft.aur
```

### Install Git

```bash
sudo pacman -S git
```

## Clone the Repository

```bash
git clone <repository-url>
cd <repository-directory>
```

## Running Playbooks

### General Purpose Configuration

```bash
ansible-playbook general-purpose-playbook.yml --ask-become-pass
```

### Compute Node Configuration

```bash
ansible-playbook compute-node-playbook.yml --ask-become-pass
```

### Control Node Configuration

```bash
ansible-playbook control-node-playbook.yml --ask-become-pass
```

## Notes

- All playbooks are designed to run against `localhost`.
- Playbooks should be executed directly on the target machine.
- Tasks are written to be idempotent whenever possible, allowing playbooks to be safely re-run.
- Administrative privileges are required for most provisioning tasks.

---

Created and maintained by Andrew.
