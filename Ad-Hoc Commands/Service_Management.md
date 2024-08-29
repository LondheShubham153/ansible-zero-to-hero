# ℹ️ Service Management

### 1. Check Service Status

```
  ansible all -m service -a "name=nginx state=status"
```

### 2. Start a Serive

```
  ansible all -m service -a "name=nginx state=started"
```

### 3. Stop a Service

```
  ansible all -m service -a "name=nginx state=stopped"
```

### 4. Restart a Service

```
  ansible all -m service -a "name=nginx state=restarted"
```

### 5. Reload a Service

```
  ansible all -m service -a "name=nginx state=reloaded"
```

### 6. Enable a Service

```
  ansible all -m service -a "name=nginx enabled=yes"
```

### 7. Disable a Service

```
  ansible all -m service -a "name=nginx enabled=no"
```

### 8. Manage Multiple Services

```
  ansible all -m service -a "name=nginx state=started"
  ansible all -m service -a "name=mysql state=started"

  # or use a single line command with a loop

  for service in nginx mysql; do ansible all -m service -a "name=$service state=started"; done

```

### 9. Check Status of Multiple Services

```
  ansible all -m service -a "name=nginx state=status"
  ansible all -m service -a "name=mysql state=status"

  # or use a single line command with a loop

  for service in nginx mysql; do ansible all -m service -a "name=$service state=status"; done

```

---
