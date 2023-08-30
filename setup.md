## Installation

1. Update your system's packages:
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```

2. Install Ansible:
   ```bash
   sudo apt install ansible
   ```

## Getting Started

1. Generate SSH keys on your control node:
   ```bash
   ssh-keygen
   ```

2. Copy the public key to managed nodes:
   ```bash
   ssh-copy-id user@managed_node_ip
   ```

## Inventory Setup

1. Create an inventory file (`hosts`) and add managed node IP addresses:
   ```ini
   [servers]
   server1 ansible_host=ip_address1
   server2 ansible_host=ip_address2
   ```

## Running Commands

- Ping managed nodes to test connectivity:
  ```bash
  ansible -i hosts all -m ping
  ```

- Run shell commands:
  ```bash
  ansible -i hosts all -a "command_here"
  ```
