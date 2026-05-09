# Task-07: Install and Configure Cron Job on Nautilus App Servers

## 📌 Objective

Install and configure the cron service on all Nautilus app servers in Stratos Datacenter.

The task includes:

- Installing the `cronie` package
- Starting and enabling the `crond` service
- Adding a cron job for the `root` user

---

## 🛠️ Implementation Steps

> Perform the following steps on all Nautilus app servers.

---

## 1. Install `cronie` Package

Install the required cron package:

```bash
sudo yum install -y cronie
```

2. Start and Enable crond Service

Start the cron daemon service:
```bash
sudo systemctl start crond
```

Enable the service to start automatically after reboot:
```bash
sudo systemctl enable crond
```

3. Verify crond Service Status

Check whether the service is running properly:
```bash
sudo systemctl status crond
```

Expected output should show:

active (running)

4. Add Cron Job for Root User

Open root user's crontab:
```bash
sudo crontab -e
```

Add the following entry:
```bash
*/5 * * * * echo hello > /tmp/cron_text
```

Save and exit the editor.


🔍 Verify Cron Job

List root user's cron jobs:
```bash
sudo crontab -l
```

Expected output:
```bash
*/5 * * * * echo hello > /tmp/cron_text
```

---

📖 Explanation
What is Cron?

Cron is a Linux scheduling utility used to automate repetitive tasks at fixed intervals.

```bash
Cron Format
* * * * * command
- - - - -
| | | | |
| | | | +---- Day of week
| | | +------ Month
| | +-------- Day of month
| +---------- Hour
+------------ Minute
```

Understanding the Cron Entry
```bash
*/5 * * * * echo hello > /tmp/cron_text
```
- */5 → Runs every 5 minutes
  
- echo hello → Prints the word hello
  
- ">" → Redirects output
  
- /tmp/cron_text → Stores the output in this file
  

Every 5 minutes, the file /tmp/cron_text will contain:
hello

---
✅ Conclusion

- cronie package installed successfully on all app servers.

- crond service started and enabled.
  
- Cron job added successfully for the root user.

- Scheduled task will execute every 5 minutes.
