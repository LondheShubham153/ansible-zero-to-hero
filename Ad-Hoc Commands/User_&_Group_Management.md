## ♂️ User & Group Management

### 1. Create a User

```
  ansible all -m user -a "name=newuser state=present"
```

### 2. Delete a User

```
  ansible all -m user -a "name=olduser state=absent"
```

### 3. Create a Group

```
  ansible all -m group -a "name=newgroup state=present"
```

### 4. Delete a Group

```
  ansible all -m group -a "name=oldgroup state=absent"
```

### 5. Add a User to a Group

```
  ansible all -m user -a "name=existinguser groups=existinggroup append=yes"
```

### 6. Remove a User from a Group

```
  ansible all -m user -a "name=existinguser groups=existinggroup remove=yes"
```

### 7. Set User's Shell

```
  ansible all -m user -a "name=existinguser shell=/bin/bash"
```

### 8. Set User's Home Directory

```
  ansible all -m user -a "name=existinguser home=/home/newhome"
```

### 9. Change User's Password

```
  ansible all -m user -a "name=existinguser password={{ 'newpassword' | password_hash('sha512') }}"
```

### 10. Create a User with Specific UID & GID

```
  ansible all -m user -a "name=newuser uid=1001 gid=1001 state=present"
```

### 11. Create a Group with Specific GID

```
  ansible all -m group -a "name=newgroup gid=2001 state=present"
```

### 12. List all Users

- **Create a Custom Script to List all Users (list_users.sh)***

```
  #!/bin/bash
  # Script to list all users on a system

  # List all users from /etc/passwd and format the output
  cut -d: -f1 /etc/passwd
```

- **Make the list_users.sh Executable**

```
  chmod +x list_users.sh
```

- **Use Ansible to execute the Script**

```
  ansible all -m shell -a "/home/ubuntu/list_users.sh"
```

---

### 13. List all Groups

- **Create a Custom Script to List all Groups (list_groups.sh)***

```
  #!/bin/bash
  # Script to list all groups on a system

  # List all groups from /etc/group and format the output
  cut -d: -f1 /etc/group
```

- **Make the list_groups.sh Executable**

```
  chmod +x list_groups.sh
```

- **Use Ansible to execute the Script**

```
  ansible all -m shell -a "/home/ubuntu/list_groups.sh"
```

---
