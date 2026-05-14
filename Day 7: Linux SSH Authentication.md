# Task-08: Configure Password-less SSH Access for User `thor`

## 📌 Objective

Configure password-less SSH authentication from the `jump host` for user `thor` to all Nautilus app servers using their respective sudo users.

Example:

- App Server 1 → user `tony`
- App Server 2 → respective sudo user
- App Server 3 → respective sudo user

This setup allows automation scripts to connect to app servers without entering passwords.

---

# 🛠️ Implementation Steps

> Perform all steps from the **jump host** as user `thor`.

---

## 1. Switch to User `thor`

```bash
sudo su - thor
```

## 2. Generate SSH Key Pair

Generate an SSH key pair for user thor:

```bash
ssh-keygen -t rsa
```
Press Enter for all prompts to accept default values.

This creates:

- Private Key → ~/.ssh/id_rsa
- Public Key → ~/.ssh/id_rsa.pub


## 🔐 Configure Password-less Access to App Servers

Repeat the following steps for all app servers using their respective sudo users.

## 3. Copy SSH Key to App Server 1

Example for App Server 1 using user tony:

```bash
ssh-copy-id tony@stapp01
```

Enter the password when prompted.

## 4. Copy SSH Key to App Server 2

Example:
```bash
ssh-copy-id steve@stapp02
```

Enter the password when prompted.

## 5. Copy SSH Key to App Server 3

Example:
```bash
ssh-copy-id banner@stapp03
```
Enter the password when prompted.

## 🔍 Verification

Verify password-less SSH login for each server.

Verify App Server 1
```bash
ssh tony@stapp01
```
Expected behavior:

- Login should happen directly
- No password prompt should appear
