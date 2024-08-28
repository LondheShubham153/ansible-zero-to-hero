## 📁 File & Directory Management

- **1. Creating a Directory**:
To create a directory, you can use the **ansible** command with the **file** module.

```
  ansible all -m file -a "path=/tmp/mydir state=directory"
```
> **Note:** -a "path=/tmp/mydir state=directory" provides the arguments to the file module, where path is the directory path and state=directory indicates that the directory should be created.

- **2. Removing a Directory**:
- **3. Creating a File**:
- **4. Removing a File**:
- **5. Copying a File**:
- **6. Deleting a File**:
- **7. Changing a File Permissions**:
- **8. Changing a File Content**:
- **9. Appending Text to a File**:
- **10. Moving/Renaming a File**:









