Certainly, here are some basic Ansible script samples to help you get started with different tasks. These samples cover various scenarios like package management, file operations, and basic configurations.

1. **Ping All Hosts**:
   Ping all hosts in your inventory to check connectivity.
   
   ```yaml
   ---
   - hosts: all
     tasks:
       - name: Ping hosts
         ping:
   ```

2. **Install a Package**:
   Install a package on managed nodes.

   ```yaml
   ---
   - hosts: webservers
     tasks:
       - name: Install Apache
         apt:
           name: apache2
           state: present
   ```

3. **Copy a File**:
   Copy a file from the control node to managed nodes.

   ```yaml
   ---
   - hosts: webservers
     tasks:
       - name: Copy index.html
         copy:
           src: /path/to/local/index.html
           dest: /var/www/html/
   ```

4. **User Management**:
   Create a new user with a specified SSH key.

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

5. **Execute Commands**:
   Run a shell command on managed nodes.

   ```yaml
   ---
   - hosts: all
     tasks:
       - name: Update system
         command: apt update && apt upgrade -y
   ```

6. **Configure a Service**:
   Ensure a service is running and enabled.

   ```yaml
   ---
   - hosts: webservers
     tasks:
       - name: Ensure Apache is running
         service:
           name: apache2
           state: started
           enabled: yes
   ```

Remember to adjust the host groups, module parameters, and paths to match your actual environment. These samples provide a foundation for more complex Ansible playbooks and tasks.
