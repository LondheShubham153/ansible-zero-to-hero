# ℹ️ Gathering Facts

### 1. Gathering Basic Facts of Hosts

```
  ansible all -m setup
```

### 2. Gather Facts from a Specific Host

```
  ansible <hostname> -m setup
```

### 3. Gather Facts with Filters from a Specific Host

```
  ansible all -m setup -a 'filter=ansible_os_family'
```

### 4. Gather Facts from a Specific Group

```
  ansible <group-name> -m setup
```

### 5. Gather Facts from a Specific Host and Save to a File

```
  ansible <hostname> -m setup -a 'filter=*' -o > facts_<hostname>.json
```

### 6. Gather Facts with a Timeout

```
  # This sets a 30-second timeout for gathering facts.

  ansible all -m setup -a 'timeout=30'

```

### 7. Gather Facts for Specific Facts Only

```
  # This command retrieves only specific facts like processor cores and total memory.

  ansible all -m setup -a 'filter=ansible_processor_cores,ansible_memtotal_mb'

```

### 8. Gather Facts for a Specific OS Type

```
  ansible all -m setup -a 'filter=ansible_distribution'
```

### 9. Gather Facts Using a Specific Inventory

```
  ansible all -m setup -i /etc/ansible/hosts
```

### 10. Gather Facts with Custom Arguments

```
  ansible all -m setup -a 'filter=ansible_*'
```

---
