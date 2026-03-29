# Ansible Configuration Management on AWS

## 📌 Project Description

This project demonstrates how to set up Ansible on an AWS EC2 instance (Control Node) and manage another EC2 instance (Managed Node) using SSH.

---

## 🚀 What We Did

1. Created AWS EC2 instances:

   * Control Node
   * Managed Node

2. Connected to Control Node using SSH

3. Installed Ansible on Control Node

4. Configured SSH access to Managed Node

5. Created inventory file

6. Tested connection using:

   ```bash
   ansible -i inventory.ini web -m ping
   ```

7. Ran ad-hoc command:

   ```bash
   ansible -i inventory.ini web -m command -a "uptime"
   ```

8. Created and executed playbook to install Apache

---

## 📂 Project Structure

```
ansible-project/
│
├── inventory.ini
├── playbook.yml
└── README.md
```

---

## ⚙️ Setup Instructions

### 1. Install Ansible

```bash
sudo apt update
sudo apt install ansible -y
```

---

### 2. Create Inventory

```ini
[web]
<managed-node-private-ip> ansible_user=ubuntu ansible_ssh_private_key_file=/home/ubuntu/Linux.pem
```

---

### 3. Test Connection

```bash
ansible -i inventory.ini web -m ping
```

---

### 4. Run Playbook

```bash
ansible-playbook -i inventory.ini playbook.yml
```

---

## ✅ Output

* Successful connection using Ansible ping
* Remote command execution
* Apache installed on managed node

---

## 👤 Author

Omkar
