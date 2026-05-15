# Day-08: Install Ansible 4.8.0 on Jump Host

## 📌 Objective

Install **Ansible version 4.8.0** on the Jump Host using `pip3` only.

Requirements:

- Install Ansible using `pip3`
- Install exactly version `4.8.0`
- Ensure Ansible commands are available globally for all users

---

# 🛠️ Implementation Steps

## 1. Verify pip3

Check pip3 version:

```bash
pip3 --version
```

## 2. Install Ansible 4.8.0 Using pip3

Run the following command:
```bash
sudo pip3 install ansible==4.8.0
```
This installs:

- ansible 4.8.0
- Required dependencies

## 3. Verify Ansible Installation

Check installed Ansible version:
```bash
ansible --version
```

Expected output should contain:
```bash
ansible [core 2.11.x]
```
and
```bash
ansible 4.8.0
```

---

## 📖 Explanation
What is Ansible?

Ansible is an open-source automation and configuration management tool used for:

- Server provisioning
- Configuration management
- Application deployment
- Infrastructure automation

It works over SSH and does not require agents on target servers.

---
Why Use pip3?

The task specifically requires installation using pip3.

Advantages:

- Easy version management
- Install specific versions
- Independent of OS package repositories
