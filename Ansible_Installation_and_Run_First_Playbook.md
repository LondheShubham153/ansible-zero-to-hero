## Ansible Installation & Running Your First Playbook

### 1. Update Your System
Before installing Ansible, it's essential to update your package list to ensure you have the latest software. </br>

- **For Debian/Ubuntu**:

```
  sudo apt update
  sudo apt upgrade -y
```

- **For RHEL/CentOS**:
```
  sudo yum update -y
```

### 2. Install Ansible

- **On Debian/Ubuntu**:
  Ansible is available via the official package repository. Install it using the following commands. </br>

```
  sudo apt install software-properties-common -y
  sudo add-apt-repository --yes --update ppa:ansible/ansible
  sudo apt install ansible -y
```

- **On RHEL/CentOS**:
  On RHEL/CentOS, you can install Ansible by enabling the EPEL repository:

```
  sudo yum install epel-release -y
  sudo yum install ansible -y
```

### 3. Verify Installation
After the installation is complete, verify it by checking the version of Ansible installed. </br>
```
  ansible --version
```

### 4. You should see output similar to

```
  ansible [core 2.14.3]
  config file = /etc/ansible/ansible.cfg
  configured module search path = ['/home/user/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python3.8/site-packages/ansible
  executable location = /usr/bin/ansible
  python version = 3.8.10 (default, May  3 2021, 08:55:58) [GCC 10.2.1 20210110]
```
---

## Ansible Master-Slave Architecture Implementation!

### 1. Configure Ansible & Set Up AWS Environment
  Create thee EC2 instances on AWS cloud. Ensure you have an SSH key pair to access them, assign a security group that allows SSH (port 22) and HTTP (port 80). </br>

- **Master Server**: This will be the Ansible controller. </br>
- **Slave Server 1**: This will be the first target server. </br>
- **Slave Server 2**: This will be the second target server. </br>
- **Configure Security Groups**: Make sure the security groups for the slave servers allow traffic from the master server, especially on SSH (port 22) and HTTP (port 80). </br>

### 2. Install and Configure Ansible on the Master Server

- **SSH into the Master Server**:

```
  ssh –I “master-key-pair.pem” ubuntu@ec2-52-15-176-134.us-east-2.compute.amazonaws.com
```

- **Update the System**:

```
  sudo apt update
```

- **Install Ansible on Ubuntu**:

```
  sudo apt install software-properties-common -y
  sudo add-apt-repository --yes --update ppa:ansible/ansible
  sudo apt install ansible -y
```
### 3. Configure SSH Access to Slave Servers

- **Copy SSH Keys to Slaves**:
  Copy the SSH key from the master to both slave servers.

 - **Test SSH Connectivity**:
   Ensure you can SSH into both slave servers from the master without needing a password.

 ### 4. Set Up Ansible Inventory

 - **Edit Inventory File**:
  The Ansible hosts file **(/etc/ansible/hosts)** is where you define your inventory of servers.

- **Open the hosts file**:

```
  sudo nano /etc/ansible/hosts
```

- **Add your servers under a specific group**:

```
  [servers]
  slave_server1 ansible_host=54.234.56.78
  slave_server2 ansible_host=54.123.45.67

  [all:vars]
  ansible_python_interpreter=/usr/bin/python3
  ansible_user=ubuntu
  ansible_ssh_private_key_file=/home/ubuntu/keys/master-key-pair.pem
```
 
 ### 5. Write an Ansible Playbook to Install NGINX

 - **Create the Playbook File**:
   Create a directory for your Ansible project and a playbook file.

```
  mkdir ~/ansible-project
  cd ~/ansible-project
  vi install_nginx.yml

```

- **Write the Playbook (install_nginx.yml)**:

```
  ---
  -  name: This playbook will install nginx
     hosts: servers
     become: yes  # to use sudo
     tasks:
       - name: install nginx
         apt: 
           name: nginx
           state: latest
       - name: start and enable nginx service
         service:
           name: nginx
           state: started
           enabled: yes
```

 - **Run the Ansible Playbook**:
   Run the playbook to install and start nginx webserver on both slave servers.

```
  ansible-playbook -i inventory.ini install_nginx.yml
```

 ### 6. Verify the Set Up

 - **Check NGINX installation on Slave Servers**:
   Open your web browser and navigate to the public IP of both slave servers.

```
  http://54.234.56.78:80
  http://54.123.45.67:80
```

- **Note:- You should see the default NGINX welcome page**

---
