# 📁 File & Directory Management

### 1. Creating a Directory
To create a directory, you can use the **ansible** command with the **file** module.

```
  ansible all -m file -a "path=/tmp/mydir state=directory"
```
> **Note:** -a "path=/tmp/mydir state=directory" provides the arguments to the file module, where path is the directory path and **state=directory** indicates that the directory should be created.</br>

### 2. Removing a Directory
To remove a directory, you can use the same file module with **state=absent**. This command removes the **/tmp/mydir** directory if it exists.

```
  ansible all -m file -a "path=/tmp/mydir state=absent"
```

### 3. Creating a File
Ansible's file module can also be used to create an empty file if it does not already exist.

```
  ansible all -m file -a "path=/tmp/myfile.txt state=touch"

  # create a file with content
  ansible all -m copy -a "dest=/tmp/myfile.txt content='This is the content of the file.'"
```

### 4. Deleting a File
To delete a file, you use the file module with **state=absent**. This removes **/tmp/myfile** from the remote hosts.

```
  ansible all -m file -a "path=/tmp/myfile state=absent"
```

### 5. Copying a File
To copy a file from the local machine to a remote host, use the **copy** module. 

```
  ansible all -m copy -a "src=/local/path/to/file dest=/remote/path/to/file"
```

### 6. Changing a File Permissions
To change the permissions of a file, you can use the **file** module with the **mode** argument. This sets the permissions of **/tmp/myfile to 0644**.

```
  ansible all -m file -a "path=/tmp/myfile mode=0644"
```

### 7. Changing a File Content
To change the content of a file, you can use the **copy** module with the **content** argument.

```
  ansible all -m copy -a "dest=/tmp/myfile content='This is the new content.'"
```

### 8. Appending Text to a File
To append text to a file, use the **lineinfile** module.

```
  ansible all -m lineinfile -a "path=/tmp/myfile line='This is a new line to append.' state=present"
```

### 9. Moving/Renaming a File
To move or rename a file, you generally need to use the command or **shell** module because Ansible does not have a direct module for moving files. 

```
  ansible all -m shell -a "mv /tmp/oldname /tmp/newname"
```

---
