# Day 5 Task: SELinux Setup and Disable on App Server 3

## 📌 Objective
Enhance server security by installing SELinux packages on **App Server 3**, and configure SELinux to be **permanently disabled** (effective after reboot).

---

## 🛠️ Implementation Steps

### 1. List and Install SELinux Packages

Install the required SELinux-related packages:

```bash
yum list selinux*
yum install -y selinux-policy 
```

###  2. Permanently Disable SELinux

Edit the SELinux configuration file:
```bash
sudo vi /etc/selinux/config
```

Update the following line:

`SELINUX=enforcing` to `SELINUX=disabled`

Save and exit the file.

---
⚠️ Important Notes

- Do NOT reboot the server manually.
  
- Changes will take effect only after the scheduled reboot.
  
- Ignore the current SELinux runtime status (getenforce output is not relevant now).

- The requirement is focused on post-reboot state, not immediate state.
