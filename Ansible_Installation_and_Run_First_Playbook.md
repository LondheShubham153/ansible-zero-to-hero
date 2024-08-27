# 🚀 Ansible Installation & Host Configurations!

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

# 🚀 Ansible Controller Managed-Nodes Architecture Implementation!

![Ansible Controller Managed-Nodes](https://raw.githubusercontent.com/Skchoudhary/blog-asset/master/dgplug-blog/ansible-arch.png)

### 1. Configure Ansible & Set Up AWS Environment
  Create three EC2 instances on AWS cloud. Ensure you have an SSH key pair to access them, assign a security group that allows SSH (port 22) and HTTP (port 80). </br>

- **Controller Node**: The machine where Ansible is installed and from where tasks are executed.</br></br>
- **Managed Node-1**: The machines that the controller manages and configures. This will be the first target node.</br></br>
- **Managed Node-2**: This will be the second target node.</br>
- **Configure Security Groups**: Make sure the security groups for the slave servers allow traffic from the master server, especially on SSH (port 22) and HTTP (port 80).</br></br>

### 2. Install and Configure Ansible on the Master Server

- **SSH into the Master Server**:

```
 ssh -i "ansible-master-key.pem" ubuntu@ec2-18-219-133-17.us-east-2.compute.amazonaws.com
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
- **Verify Installation**:

```
  ansible --version
```

- **Create a keys directory inside .ssh**:

```
  mkdir /home/ubuntu/keys
  cd keys
```

- **Copy "ansible-master-key.pem" file to Controller to SSH into Managed Nodes**

Note: When you create EC2 instance on AWS, you have created ansible-master-key.pem file, so you need to copy this .pem file to controller node for SSH connectivity to the managed nodes.

```
  scp -i "ansible-master-key.pem" ansible-master-key.pem ubuntu@ec2-52-15-176-134.us-east-2.compute.amazonaws.com:/home/ubuntu/keys/
```

- **Run the following command to change the permissions:**:

```
  chmod 400 /home/ubuntu/keys/ansible-master-key.pem
```

- **Verify the permissions to ensure they have been set correctly:**

```
  ls -l /home/ubuntu/keys/ansible-master-key.pem
```

 ### 3. Set Up Ansible Inventory

 - **Edit Inventory File**:
  The Ansible hosts file **(/etc/ansible/hosts)** is where you define your inventory of servers.

- **Open the hosts file**:

```
  sudo vim /etc/ansible/hosts
```

- **Add your servers under a specific group**:

```
  [servers]
  node1 ansible_host=3.142.79.205
  node2 ansible_host=3.143.210.190

  [all:vars]
  ansible_python_interpreter=/usr/bin/python3
  ansible_user=ubuntu
  ansible_ssh_private_key_file=/home/ubuntu/keys/ansible-master-key.pem

```

- **Verify Ansible inventory list**:

```
  ansible-inventory --list
```

- **Test Connectivy**:
  Ping all the nodes from the controller without needing a password.

```
  ansible -m ping servers
```

- **To check RAM & ROM**:
  To check RAM & ROM in the all nodes from controller using a ad-hoc commands.

```
  ansible -a "free -h" servers # to check RAM
  ansible -a "df -h" servers   # to check ROM
```

- **To update of all servers**:
  If you want to update the nodes system from the controller use the below ad-hoc command.

```
  ansible -a "sudo apt-get update" servers
```

- **To check uptime of all servers**:
  If you want to check uptime of the all nodes from the controller use the below ad-hoc command.

```
  ansible -a "uptime" server
```

 ### 4. Write an Ansible Playbook to Install NGINX

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

 ### 5. Verify the Set Up

 - **Check NGINX installation on Slave Servers**:
   Open your web browser and navigate to the public IP of both slave servers.

```
  http://3.142.79.205:80
  http://3.143.210.190:80
```

- **Note:- You should see the default NGINX welcome page**

---
