# 🌐 Simple Website Deployment with Ansible

This project demonstrates how to deploy a basic static HTML website on a server using **Nginx** with the help of **Ansible**.

## 📄 Project Description

- A simple HTML website is created.
- The website is deployed using Ansible on a server running Nginx.
- The playbook automates:
  - Installing Nginx
  - Copying the website files
  - Starting and enabling the Nginx service

---

## 🚀 How to Run

1. Clone this repository or navigate to the project directory.

2. Run the playbook:

   ```bash
   ansible-playbook -i inventory/hosts site.yml --ask-become-pass
   ```

Open your browser and go to:

``` bash
http://localhost
You should see your simple HTML website.
```

---

## 🛠️ Requirements

- Ansible
- Nginx (installed via playbook)
- Linux environment (tested on Ubuntu)

---