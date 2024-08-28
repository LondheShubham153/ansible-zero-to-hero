## 💻 Ping all Hosts

### 1. Ping all the hosts in the inventory

```
  ansible all -m ping

```

### 2. Ping hosts in a specific group

```
  ansible webservers -m ping

```

### 3. Ping a single server from inventory

```
  ansible webserver -m ping

```

### 4. Ping all the hosts and save the results to a file

```
  ansible all -m ping > ping_results.txt
```

### 5. Filter outputs with grep command

```
  ansible all -m ping | grep -E "SUCCESS|UNREACHABLE"

```
---
