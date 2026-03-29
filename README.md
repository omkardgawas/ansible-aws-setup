# Ansible Configuration Management on AWS

## 📌 Project Description

This project demonstrates how to set up Ansible on an AWS EC2 instance (Control Node) and manage another EC2 instance (Managed Node) using SSH.

---

## 🚀 What We Did

1. Created AWS EC2 instances:

   * Control Node
     <img width="1918" height="867" alt="image" src="https://github.com/user-attachments/assets/fd8c6b2f-57b0-43b9-bdbb-cc2b2de602ab" />

   * Managed Node
     <img width="1918" height="867" alt="image" src="https://github.com/user-attachments/assets/31c2907d-70e1-4e16-a3a0-7acc73495214" />


2. Connected to Control Node using SSH
   ssh -i my-key.pem ubuntu@192.168.10.71

4. Installed Ansible on Control Node
   sudo apt update
   sudo apt install ansible -y

6. Configured SSH access to Managed Node
   a. Copy .pem key to Control Node (from local)
     ```bash
     scp -i Linux.pem Linux.pem ubuntu@192.168.10.71:/home/ubuntu/
     ```
   b. Set Correct Permissions (on Control Node)
     ```bash
     chmod 400 Linux.pem
     ```
   c. Connect to Managed Node (from Control Node)
     ```bash
     ssh -i Linux.pem ubuntu@192.168.10.247
     ```
     
8. Created inventory file
   a. Create Inventory File
     ```bash
     nano inventory.ini
     ```
   b. Add Content in the file
     ```bash
     [web]
     192.168.10.247 ansible_user=ubuntu ansible_ssh_private_key_file=/home/ubuntu/Linux.pem
     ```

10. Tested connection using:

   ```bash
   ansible -i inventory.ini web -m ping
   ```

11. Ran ad-hoc command:

   ```bash
   ansible -i inventory.ini web -m command -a "uptime"
   ```

11. Created and executed playbook to install Apache

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
