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
   Create an inventory file (/etc/ansible/hosts) or create your own in your home directory (~/ansible_hosts).

 - **Add the following Server Configuration**:  

 ### 5. Write an Ansible Playbook to Install NGINX

 - **Create the Playbook File**:
 - **Write the Playbook**:

 ### 6. Run the Ansible Playbook

 - **Execute the Playbook**:

 ### 7. Verify the Set Up

 - **Check NGINX installation on Slave Servers**:
   Open your web browser and navigate to the public IP of bothe slave servers.

```
  http://54.234.56.78:80
  http://54.123.45.67:80
```

- **Note:- You should see the default NGINX welcome page*









