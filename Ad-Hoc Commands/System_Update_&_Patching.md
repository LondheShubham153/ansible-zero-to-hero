# ⤴️ System Update & Patching

## For Debian/Ubuntu Based Systems

### 1. Update the Package List

```
  ansible all -m apt -a "update_cache=yes"
```

### 2. Upgrade all Installed Packages to their Latest Version

```
  ansible all -m apt -a "upgrade=dist"
```

### 3. Install a Specific Package

```
  ansible all -m apt -a "name=package_name state=latest"
```

### 4. Remove a Specific Package

```
  ansible all -m apt -a "name=package_name state=absent"
```
### 5. Reboot the System

```
  ansible all -m reboot -b
```

### 6. Run a custom script for patching (assuming the script is located at /home/ubuntu/patching.sh)

```
  ansible all -m script -a "/home/ubuntu/patching.sh"  
```

---

## For RedHat/CentOS/Fedora Systems

### 1. Update the Package List

```
  ansible all -m yum -a "name=* state=latest udate_cache=yes" -b
```

### 2. Upgrade all Installed Packages to their Latest Version

```
  ansible all -m yum -a "name=* state=latest" -b
```

### 3. Install a Specific Package

```
  ansible all -m yum -a "name=package_name state=latest"
```

### 4. Remove a Specific Package

```
  ansible all -m yum -a "name=package_name state=absent"
```
### 5. Reboot the System

```
  ansible all -m reboot -b
```

---

## For Windows Systems

### 1. Update the all Installed Packages

```
  ansible all -m win_chocolatey -a "name=all state=latest"
```

### 2. Install a Specific Package

```
  ansible all -m win_chocolatey -a "name=package_name state=latest"
```

### 3. Remove a Specific Package

```
  ansible all -m win_chocolatey -a "name=package_name state=absent"
```
### 4. Reboot the System

```
  ansible windows -m win_reboot
```

### 5. Reboot with a Delay

```
  #sets a timeout of 600 seconds (10 minutes) before the system reboots.
  ansible windows -m win_reboot -a "reboot_timeout=600"
```
### 6. Reboot with a Custom Message

```
  ansible windows -m win_reboot -a "reboot_timeout=600 reboot_message='System will reboot in 10 minutes for maintenance.'"
```

---
