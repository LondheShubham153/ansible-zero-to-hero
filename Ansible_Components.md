# 🚀 Ansible Components!

---

### 1. Inventory
Ansible inventory is a file or a collection of files that define the hosts and groups of hosts that Ansible uses to connect to and manage systems. It tells Ansible where the target machines are, what their IP addresses or hostnames are, and any specific variables associated with those hosts. </br>

#### Types of Ansible Inventory

- **Static Inventory**:
A simple text file **(hosts)** where you list your hosts and group them under categories, or A list of IP addresses or hostnames, organized into groups.
Typically written in **INI or YAML** format.</br>

Example of a Static Inventory File (inventory.ini)</br>
```
[servers]
server1 ansible_host=server1_publicip ansible_user=username ansible_ssh_private_key_file=~/.ssh/server_key.pem
server2 ansible_host=server1_publicip ansible_user=username ansible_ssh_private_key_file=~/.ssh/server_key.pem

[all:vars]
ansible_python_interpreter=/usr/bin/python3

```

Example of a YAML format static inventory: </br>
```
all:
  hosts:
    server1:
      ansible_host: server1_publicip
      ansible_user: username
      ansible_ssh_private_key_file: ~/.ssh/server_key.pem
    server2:
      ansible_host: server2_publicip
      ansible_user: username
      ansible_ssh_private_key_file: ~/.ssh/server_key.pem

  vars:
    ansible_python_interpreter: /usr/bin/python3

```

Write a Ansible Playbook for Static Inventory File (inventory.ini):</br>
Sample Playbook (deploy.yml)</br>

```
---
- name: Set up NGINX web server
  hosts: servers
  become: yes
  tasks:
    - name: Install NGINX
      apt:
        name: nginx
        state: present
      when: ansible_os_family == "Debian"

    - name: Ensure NGINX is running and enabled to start at boot
      service:
        name: nginx
        state: started
        enabled: yes

    - name: Create a basic HTML file for the default NGINX page
      copy:
        content: |
          <!DOCTYPE html>
          <html>
          <head>
              <title>Welcome to NGINX</title>
          </head>
          <body>
              <h1>Success! The NGINX web server is installed and working!</h1>
          </body>
          </html>
        dest: /var/www/html/index.html

    - name: Restart NGINX to apply changes
      service:
        name: nginx
        state: restarted
```

Running a Playbook on All Servers:</br>
```
ansible-playbook -i inventory.ini deploy.yml
```
This command will run the deploy.yml playbook on all the servers listed in the inventory.ini file.</br>

Running a Playbook on a Specific Group:</br>
```
ansible-playbook -i inventory.ini deploy.yml --limit servers
```
This command will run the deploy.yml playbook for the servers group listed in the inventory.ini file.</br>

- **Dynamic Inventory**:
Used in dynamic environments like cloud providers where hosts can change frequently. Ansible can fetch the list of hosts dynamically using scripts or plugins.</br>
An inventory that is generated dynamically at runtime using scripts or APIs. Commonly used for cloud environments (e.g., AWS, Azure, & GCP) where the list of hosts can change frequently.</br>

Example of Dynamic Inventory Using an AWS EC2 plugin:</br>
```
plugin: aws_ec2
regions:
  - us-west-2
filters:
  instance-state-name: running
```

Example command to use a dynamic inventory script:</br>
```
ansible-playbook -i dynamic_inventory_script.py playbook.yml
```
---

### 2. Modules 
### 3. Playbooks
### 4. Roles
### 5. Handlers
### 6. Templates
### 7. Varibles
### 8. Facts
### 9. Tags
### 10. Loops


