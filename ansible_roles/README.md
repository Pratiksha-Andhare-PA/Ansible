# 🛠️ Ansible Role-Based Web Server Setup

This Ansible project demonstrates a structured, role-based approach to setting up web servers using **nginx** and **apache2**. It highlights role separation, task modularization, and discusses a real-world issue of port conflict between web servers.

---

## ✅ Task Flow and Execution Order

### 🔹 `ansible_roles.yml` (Playbook entry point)
- Executes roles in order:
  1. **custom-role**
  2. **install-apache**

---

### 🔹 `custom-role` Role

#### 1. `tasks/main.yml`
- Includes subtasks:
  - `packages.yml`
  - `message.yml`

#### 2. `tasks/packages.yml`
- Installs `nginx` web server and prints a debug message.

#### 3. `tasks/message.yml`
- Reads a variable from `vars/main.yml` and prints a custom message.

#### 4. `vars/main.yml`
- Defines variables like `message` used in tasks.

---

### 🔹 `install-apache` Role

#### 1. `tasks/main.yml`
- Installs and attempts to start the `apache2` web server service.

---

## ⚠️ Port Conflict: Apache2 vs Nginx

Both **nginx** and **apache2** default to **port 80**, which causes a conflict if both are started simultaneously.

### ❌ Error Example:

```bash
fatal: [localhost]: FAILED! => {"msg": "Could not find the requested service lighttpd: host"}
```

(OR)

``` bash
Job for apache2.service failed because the control process exited with error code.
```

---

### ✅ Solution: Change Apache2 Port
##### Can change either of Apache2 (OR) Nginx 

🔧 Edit Apache2 Port:
``` bash
sudo nano /etc/apache2/ports.conf
```

Change:
``` bash
Listen 80
```

to:

``` bash
Listen 8080
```

---

### 🔄 Restart Apache2:
``` bash
sudo systemctl restart apache2
```

This ensures both nginx and apache2 can run simultaneously without port conflict.

---