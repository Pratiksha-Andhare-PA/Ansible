# 🧪 Ansible Environment Variables Playbook

This playbook demonstrates setting environment variables at both play and task levels in Ansible.

---

## ▶️ Run Commands

```bash
ansible-playbook --inventory inventory/ansible-env-variables-playbook/hosts ansible-env-variables-playbook.yml -K
```

- -K prompts for the sudo password (become: yes is used in the playbook to run tasks with elevated privileges).

``` bash
ansible-playbook --inventory inventory/ansible-env-variables-playbook/hosts ansible-env-variables-playbook.yml -v -K
``` 

- -v enables verbose output, useful for debugging and viewing task execution details.

---