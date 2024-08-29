# 💽 Disk Management

## For Debian/Ubuntu Based Systems

### 1. Check Disk Usage

```
  ansible all -m command -a "df -h"
```

### 2. List Partitions

```
  ansible all -m command -a "lsblk"
```

### 3. Create a new Partition

```
  ansible all -m command -a "parted /dev/sdX mkpart primary ext4 0% 100%"
```

### 4. Format a Partiion (e.g., /dev/sdX1 with ext4)

```
  ansible all -m command -a "mkfs.ext4 /dev/sdX1"
```

### 5. Mount a Filesystem

```
  ansible all -m mount -a "path=/mnt/mydisk src=/dev/sdX1 fstype=ext4 state=mounted"
```

### 6. Unmount a Filesystem

```
  ansible all -m mount -a "path=/mnt/mydisk state=unmounted"
```

### 7. Check Disk Health

```
  ansible all -m command -a "smartctl -a /dev/sdX"
```

---

## For Windows Systems

### 1. Check Disk Usage

```
  ansible all -m win_shell -a "Get-PSDrive -PSProvider FileSystem"
```

### 2. List Partitions

```
  ansible all -m win_shell -a "Get-Partition"
```

### 3. Create a new Partition

```
  ansible all -m win_shell -a "New-Partition -DiskNumber 0 -UseMaximumSize -AssignDriveLetter"
```

### 4. Format a Partiion (using New-Partition)

```
  ansible all -m win_shell -a "Format-Volume -DriveLetter D -FileSystem NTFS -Confirm:$false"
```

### 5. Mount a Filesystem (using Add-PartitionAccessPath)

```
  ansible all -m win_shell -a "Add-PartitionAccessPath -DiskNumber 0 -PartitionNumber 1 -AccessPath 'D:\'"
```

### 6. Unmount a Filesystem (using Remove-PartitionAccessPath)

```
  ansible all -m win_shell -a "Remove-PartitionAccessPath -DiskNumber 0 -PartitionNumber 1 -AccessPath 'D:\'"
```

### 7. Check Disk Health (using Get-PhysicalDisk)

```
  ansible all -m win_shell -a "Get-PhysicalDisk"
```

---
