# ℹ️ System Information & Monitoring

## System Information

### 1. To check Hostname

```
  ansible all -m command -a "hostname"
```

### 2. OS Distribution & Version

```
  ansible all -m setup -a 'filter=ansible_distribution*'
```

### 3. Kernel Version

```
  ansible all -m command -a "uname -r"
```

### 4. To check Uptime of all System

```
  ansible all -m command -a "uptime"
```

### 5. CPU Information

```
  ansible all -m setup -a 'filter=processor*'
```

### 6. Memory Information

```
  ansible all -m setup -a 'filter=mem*'
```

### 7. Disk Space Usage

```
  ansible all -m command -a "df -h"
```

### 8. Disk I/O Statistics

```
  ansible all -m command -a "iostat -x"
```

### 9. Network Interface

```
  ansible all -m setup -a 'filter=ansible_interfaces'
```

---

## Service Status

### 1. Check if a Service is Running

```
  ansible all -m service -a "name=<service_name> state=started"
```

### 2. List all Services and their Status

```
  ansible all -m command -a "systemctl list-units --type=service --state=running"
```

---

## Processes & Performance

### 1. List Running Processes

```
  ansible all -m command -a "ps aux"
```

### 2. Top Processes by Memory Usage

```
  ansible all -m command -a "ps aux --sort=-%mem | head -n 10"
```

### 3. Top Processes by CPU Usage

```
  ansible all -m command -a "ps aux --sort=-%cpu | head -n 10"
```

---

## Logs & Files

### 1. View last 10 Lines of a Log File

```
  ansible all -m command -a "tail -n 10 /var/log/syslog"
```

### 2. Check Disk Usage for a Specific Directory

```
  ansible all -m command -a "du -sh /path/to/directory"
```

---

## Network Monitoring

### 1. Check Listening Ports

```
  ansible all -m command -a "netstat -tuln"
```

### 2. Check Network Connections

```
  ansible all -m command -a "ss -tuln"
```

---

## User & Groups 

### 1. List Users

```
  ansible all -m command -a "cut -d: -f1 /etc/passwd"
```

### 2. List Groups

```
  ansible all -m command -a "cut -d: -f1 /etc/group"
```

---

## Package Information

### 1. List Installed Packages (Debian-based)

```
  ansible all -m command -a "dpkg -l"
```

### 2. List Installed Packages (RHEL-based)

```
  ansible all -m command -a "rpm -qa"
```

---

## System Load

### 1. Current Load Averages

```
  ansible all -m command -a "cat /proc/loadavg"
```

---

## Custom Facts

### 1. Gather Custom Facts (Using a setup module)

```
  ansible all -m setup
```

---



