# Ansible

## 🧩 Ansible Essentials

This repository is a comprehensive guide and practice workspace for learning and implementing various core components of Ansible. 

It includes multiple directories with categorized examples and playbooks covering variables, conditionals, roles, error handling, encryption with vault, and a sample project that deploys a simple HTML website using Nginx.

---

## 📘 Contents

1. **Ansible Variables** 
– Demonstrates how to use different types of variables in Ansible and how to override them.

2. **Environment Variables** 
– Shows how to work with and manage environment variables in Ansible.

3. **Conditionals** 
– Includes examples of using conditionals and logical statements in playbooks.

4. **Roles** 
– Structured demonstration of how to organize Ansible content using roles for better reusability and scalability.

5. **Error Handling** 
– Covers methods for handling errors gracefully in Ansible playbooks.

6. **Ansible Vault** 
– Securing sensitive data like passwords and API keys using Ansible Vault.

7. **Basic Website Deployment (Nginx)** 
– A simple static website built with HTML and deployed using Ansible on an Nginx server.

---

## 🚀 Running the Playbook

To execute a playbook:

```bash
ansible- inventory inventory/hosts playbook.yml -K
```
- Replace playbook.yml with the playbook file name inside the respective directory.

- -K or --ask-become-pass prompts for the sudo password, which is required when the playbook contains tasks that need elevated (root) privileges, like installing packages or modifying system files.

---