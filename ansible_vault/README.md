# 🔐 Ansible Vault Playbook Setup with Encrypted Secrets

This project demonstrates the usage of **Ansible Vault** for encrypting secrets and securely injecting them into Ansible playbooks. It follows a structure and workflow tailored to the directory and file naming used in your actual implementation.

---

## 🚀 SSH into EC2 Instance

To access the EC2 instance:

```bash
ssh -i /Users/user_name/.ssh/aws_ec2_terraform ubuntu@ipAddress
```
---

## 1. 🔐 Ansible Vault Commands

### a. Create a New Vault File

``` bash
ansible-vault create group_vars/my_vault.yml
```
Enter the vault password when prompted.

Add a secret inside the file:

``` bash
my_message: "This is test message from vault"
```

🔒 You won’t be able to read it using cat group_vars/my_vault.yml since it's encrypted.

### b. Edit the Encrypted File

``` bash
ansible-vault edit group_vars/my_vault.yml
```

### c. View the Encrypted File


```bash
ansible-vault view group_vars/my_vault.yml
```

### d. Encrypt an Existing File

``` bash
ansible-vault encrypt group_vars/plain_text_secret_file.txt
```
---

## 2. Running Playbooks with Vault

### a. Using --ask-vault-pass

```bash
ansible-playbook --inventory inventory/ansible_vault/hosts ansible_vault_playbook.yml -e @group_vars/my_vault.yml --ask-vault-pass -K
```

-e @group_vars/my_vault.yml passes the encrypted vars into the playbook.

---

## 3. 🔐 Encrypting Vault with a Base64-Generated Password

### a. Generate the Vault Password File

```bash
openssl rand -base64 2048 > pass_file/ansible-vault.pass
```

### b. Create Vault Using Password File

```bash
ansible-vault create group_vars/my_vault_with_bas64_pass.yml --vault-password-file=pass_file/ansible-vault.pass
```

### c. View the Encrypted File

```bash
ansible-vault view group_vars/my_vault_with_bas64_pass.yml \
  --vault-password-file=pass_file/ansible-vault.pass
 ```

### d. Run Playbook with Password File

``` bash
ansible-playbook --inventory inventory/ansible_vault/hosts ansible_vault_playbook.yml -e @group_vars/my_vault_with_bas64_pass.yml --vault-password-file=pass_file/ansible-vault.pass
```

---

## 4.🛠️ Setting Environment Variable for Password File
### a. Export the Vault Password File Path

```bash

export ANSIBLE_VAULT_PASSWORD_FILE=/home/pratiksha/ansible_project/Ansible_Projects/Projects/ansible_vault/pass_file/ansible-vault.pass
```

- ✅ Make sure you do not use Windows paths (e.g., /wsl.localhost/...) inside WSL.

### b. Run Playbook Without Repeating --vault-password-file

```bash
ansible-playbook \--inventory inventory/ansible_vault/hosts ansible_vault_playbook.yml -e @group_vars/my_vault_with_bas64_pass.yml
```

## ✅ Tips & Reminders
- Always use Linux-style paths inside WSL (e.g., /home/pratiksha/...).

### Set file permissions for the password file:

``` bash
chmod 600 pass_file/ansible-vault.pass
```

You can also define ANSIBLE_VAULT_PASSWORD_FILE in ~/.bashrc to persist it.

---