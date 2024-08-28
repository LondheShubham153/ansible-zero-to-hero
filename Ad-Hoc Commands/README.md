
# 🚀 Ad-Hoc Commands in Ansible!

### What are Ansible Ad-Hoc Commands?
Ansible Ad-Hoc commands are one-liner shell commands that allow you to perform simple operations across multiple machines in your inventory. They are typically used for quick tasks such as checking connectivity, restarting services, managing files, or gathering facts about systems. Since these commands don't require writing a full playbook, they're perfect for quick automation tasks. </br></br>

### Why use ad hoc commands?
Ad-Hoc commands in Ansible are powerful tools for quickly performing tasks across multiple systems without the need to write and execute a full playbook. ad hoc commands are great for tasks you repeat rarely. For example, if you want to power off all the machines in your lab for Christmas vacation, you could execute a quick one-liner in Ansible without writing a playbook. </br></br>

### General Syntax of Ansible Ad-Hoc Commands?

```
  ansible [host-pattern] -m [module] -a "[module options]" [other options]
```
- **host-patterns**: Specifies the group of hosts or individual host to run the command against. You can also use keywords like all to target all hosts.

- **m-module**: Specifies the Ansible module to use.

- **-a module-options**: Provides the arguments for the module.

- **other options**: Additional options like inventory file, become (for privilege escalation), etc.

---

### Use cases for ad hoc commands?

#### [1. Ping all Hosts](https://github.com/LondheShubham153/ansible-zero-to-hero/blob/main/Ad-Hoc%20Commands/Ping_all_Hosts.md)
#### [2. Gathering Facts](https://github.com/LondheShubham153/ansible-zero-to-hero/blob/main/Ad-Hoc%20Commands/Gathering_Facts.md)
#### [3. System Update & Patching](https://github.com/LondheShubham153/ansible-zero-to-hero/blob/main/Ad-Hoc%20Commands/System_Update_%26_Patching.md)
#### [4. Disk Management](https://github.com/LondheShubham153/ansible-zero-to-hero/blob/main/Ad-Hoc%20Commands/Disk_Management.md)
#### [5. System Information and Monitoring](https://github.com/LondheShubham153/ansible-zero-to-hero/blob/main/Ad-Hoc%20Commands/System_Information_%26_Monitoring.md)
#### [6. Network Configuration](https://github.com/LondheShubham153/ansible-zero-to-hero/blob/main/Ad-Hoc%20Commands/Network_Configuration.md)
#### [7. Package Management](https://github.com/LondheShubham153/ansible-zero-to-hero/blob/main/Ad-Hoc%20Commands/Package_Management.md)
#### [8. File and Directory Management](https://github.com/LondheShubham153/ansible-zero-to-hero/blob/main/Ad-Hoc%20Commands/File_%26_Directory_Management.md)
#### [9. Service Management](https://github.com/LondheShubham153/ansible-zero-to-hero/blob/main/Ad-Hoc%20Commands/Service_Management.md)
#### [10. User and Group Management](https://github.com/LondheShubham153/ansible-zero-to-hero/blob/main/Ad-Hoc%20Commands/User_%26_Group_Management.md)

