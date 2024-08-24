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
####  Optional: Install Git and Python if needed
```
  sudo apt install git python-pip -y
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


For more detailed installation instructions, please refer to the official Ansible documentation:

[Ansible Community Documentation](https://docs.ansible.com/ansible/latest/installation_guide/index.html)

