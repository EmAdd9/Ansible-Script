Certainly, here are some of the most commonly used Ansible script samples that cover a variety of tasks, including package management, file operations, user management, service control, and more.

1. **Install Packages on Multiple Servers**:
   Install packages on multiple servers using the `apt` module.

   ```yaml
   ---
   - hosts: webservers
     tasks:
       - name: Install packages
         apt:
           name: "{{ item }}"
           state: present
         loop:
           - apache2
           - nginx
   ```

2. **Deploy an Application**:
   Clone a Git repository and deploy an application.

   ```yaml
   ---
   - hosts: app_servers
     tasks:
       - name: Clone Git repository
         git:
           repo: https://github.com/username/repo.git
           dest: /opt/app
       - name: Install dependencies
         command: npm install
         args:
           chdir: /opt/app
   ```

3. **Manage Files and Directories**:
   Create directories, copy files, and manage permissions.

   ```yaml
   ---
   - hosts: fileservers
     tasks:
       - name: Create directory
         file:
           path: /data/logs
           state: directory
       - name: Copy config file
         copy:
           src: files/app.conf
           dest: /etc/app.conf
       - name: Set file permissions
         file:
           path: /data/logs
           mode: '0755'
   ```

4. **User and SSH Key Management**:
   Create a user and manage SSH keys for that user.

   ```yaml
   ---
   - hosts: all
     tasks:
       - name: Add user
         user:
           name: newuser
           state: present
       - name: Add SSH key
         authorized_key:
           user: newuser
           key: "{{ lookup('file', '/path/to/public_key.pub') }}"
   ```

5. **Service Management**:
   Ensure a service is running and enabled.

   ```yaml
   ---
   - hosts: app_servers
     tasks:
       - name: Ensure service is running
         service:
           name: myapp
           state: started
           enabled: yes
   ```

6. **Dynamic Inventory with EC2**:
   Use a dynamic inventory script to manage AWS EC2 instances.

   ```yaml
   ---
   - hosts: tag_Name_app
     gather_facts: no
     tasks:
       - name: Ensure service is running
         service:
           name: myapp
           state: started
   ```

These are just a few common examples to demonstrate Ansible's versatility. Depending on your specific use cases, you can combine and modify these scripts to fit your infrastructure and automation needs.
