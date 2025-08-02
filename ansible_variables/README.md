# 🛠️ Ansible Variables Playbook

This project demonstrates how to use different types of variables in Ansible and how to override them at runtime. It also includes a standard Git branching and merging workflow to contribute effectively.

---

## 📘 Table of Contents

1. [Project Description](#project-description)  
2. [Setup Instructions](#setup-instructions)  
   - [Prerequisites](#prerequisites)  
   - [Clone the Repository](#clone-the-repository)  
   - [Running the Playbook](#running-the-playbook)  
3. [Variable Precedence](#variable-precedence)  
4. [Git Workflow](#git-workflow)  
5. [Tips](#tips)

---

## 📄 Project Description

This project provides examples of:

- Defining various types of variables in Ansible
- Overriding variables using inline input and external YAML files
- Understanding Ansible's variable precedence
- Following a clean Git branching workflow for collaborative development

---

## ⚙️ Setup Instructions

### Prerequisites

- Ensure Ansible is installed on your system.

To verify:
```bash
ansible --version
```

### ▶️ Run the Ansible Playbook
#### 1. Basic Run (uses variables from the playbook)
```bash
ansible-playbook --inventory inventory/ansible-variables-playbook/hosts ansible-variables-playbook.yml -K
```

#### 2. With Inline Extra Variables
```bash
ansible-playbook --inventory inventory/ansible-variables-playbook/hosts ansible-variables-playbook.yml --extra-vars '{"version": 1.0, "other_variable": "foo-world"}' -K
```

#### 3. With External YAML File
```bash
ansible-playbook --inventory inventory/ansible-variables-playbook/hosts ansible-variables-playbook.yml --extra-vars "@my_vars.yml" -K
```

-ℹ️ Use -K only if your playbook requires privilege escalation (become: yes).

---

## 🧪 Variable Precedence in Ansible
- Ansible resolves variables in the following order (from highest to lowest priority):

1. --extra-vars (inline or file)
2. vars_files
3. vars (within the playbook)

defaults (from roles or elsewhere)

---

## 🌿 Git Branch Workflow
### 🧱 Initial Setup
```bash
git init
git remote add origin <your_repo_url>
git pull origin main   # Pull if remote already has files (like README)
```

### 🔧 Working on a Feature
```bash
git checkout -b feature-branch-name
```

### Make your changes in the code...

```bash
git add .
git commit -m "Add new feature"
git push -u origin feature-branch-name
```

### 🔄 Merge Back to Main
```bash
git checkout main
git pull origin main
git merge feature-branch-name
git push origin main
```

---

## 💡 Tips
- Use feature branches to organize your work and avoid conflicts.

- Always pull the latest changes before pushing.

- Use inline or external variables for flexible and reusable Ansible playbooks.

---
