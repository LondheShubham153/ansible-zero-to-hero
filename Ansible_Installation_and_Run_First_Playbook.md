## Ansible Installation & Running Your First Playbook

---

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
