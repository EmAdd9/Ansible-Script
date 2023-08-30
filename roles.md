# Ansible Role: Install Tomcat 9 on CentOS, Fedora, Debian, and Ubuntu Linux

This Ansible role is designed to automate the installation of Apache Tomcat 9 on various Linux distributions, including CentOS, Fedora, Debian, and Ubuntu. It simplifies the process of setting up Tomcat, Java, user management, firewall configuration, and more.

## Tested Operating Systems

- CentOS 8
- CentOS 7
- Fedora 36
- Ubuntu 20.04 / Ubuntu 18.04
- Debian 11 / Debian 10

## Role Tasks

This role consists of tasks that will:

1. Install necessary base packages.
2. Install Java.
3. Add a tomcat user and group.
4. Download Tomcat and perform the installation.
5. Configure systemd for Tomcat.
6. Configure the firewall.

## How to Use this Role

Follow these steps to use the Ansible role for installing Tomcat 9:

1. Clone the Project:
   ```bash
   git clone https://github.com/jmutai/tomcat-ansible.git
   cd tomcat-ansible
   ```

2. Update your Inventory:
   Modify the `hosts` file to include the target servers.
   ```ini
   [tomcat_nodes]
   192.168.10.10       # Replace with your server's IP
   ```

3. Update Variables:
   Edit the `tomcat-setup.yml` playbook file to set your desired Tomcat version, remote user, and Tomcat UI access credentials.
   ```yaml
   - name: Tomcat deployment playbook
     hosts: tomcat_nodes
     become: yes
     become_method: sudo
     remote_user: root
     vars:
       tomcat_ver: 9.0.64
       ui_manager_user: manager
       ui_manager_pass: Str0ngManagerP@ssw3rd
       ui_admin_username: admin
       ui_admin_pass: Str0ngAdminP@ssw3rd
     roles:
       - tomcat
   ```

4. Execute the Playbook:
   Run the playbook against your nodes based on your authentication method.

   - Playbook executed as root user with SSH key:
     ```bash
     ansible-playbook -i hosts tomcat-setup.yml
     ```

   - Playbook executed as root user with password:
     ```bash
     ansible-playbook -i hosts tomcat-setup.yml --ask-pass
     ```

   - Playbook executed as sudo user with password:
     ```bash
     ansible-playbook -i hosts tomcat-setup.yml --ask-pass --ask-become-pass
     ```

   - Playbook executed as sudo user with SSH key and sudo password:
     ```bash
     ansible-playbook -i hosts tomcat-setup.yml --ask-become-pass
     ```

   - Playbook executed as sudo user with SSH key and passwordless sudo:
     ```bash
     ansible-playbook -i hosts tomcat-setup.yml --ask-become-pass
     ```

The playbook should execute successfully without errors, setting up Tomcat on the specified servers. This role streamlines the deployment process and ensures consistency across different Linux distributions.
