# Task-10: Linux Bash Scripts



## 📌 Objective

- Create Bash Script for Website Content Archiving and named as:

```bash
news_archive.sh
```
on App Server 1 under:

`/scripts`

The script should:

- Create a zip archive of website content
- Store the archive locally
- Copy the archive to Nautilus Storage Server
- Perform password-less file transfer
- Allow the respective server user (tony) to execute the script
- Avoid using sudo inside the script

---

### 🛠️ Implementation Steps
## 1. Navigate to Scripts Directory
`cd /scripts/`
## 2. Create the Script File
`touch news_archive.sh`
## 3. Add Script Content

Open the script:

`vi news_archive.sh`

Add the following content:
```bash
#!/bin/bash

zip -r /archives/xfusioncorp_news.zip /var/www/html/news

scp /archives/xfusioncorp_news.zip natasha@ststor01:/archives/
```
Save and exit the file.

## 4. Make Script Executable
`chmod +x news_archive.sh`
## 5. Set Proper Ownership

Assign ownership to user tony:

`sudo chown tony:tony /scripts /archives/`

This ensures user tony can:

Execute the script
Create archives
Access required directories

## 🔐 Configure Password-less SSH Authentication

To avoid password prompts during scp, configure SSH key-based authentication.

## 6. Generate SSH Key

Run:

```ssh-keygen -t rsa```

Press Enter for all prompts.

This creates:

- Private key → `~/.ssh/id_rsa`
- Public key → `~/.ssh/id_rsa.pub`
## 7. Copy Public Key to Storage Server

Run:

```ssh-copy-id natasha@ststor01```

Enter password once when prompted.

This enables password-less SSH authentication.
---
▶️ Execute the Script

Run the script:
```bash
./news_archive.sh
```
---
✅ Conclusion
- Bash script news_archive.sh created successfully
- Website content archived into ZIP format
- Archive stored locally under /archives
- Archive copied successfully to Storage Server
- Password-less SSH authentication configured
- Script executable by user tony
- No sudo used inside the script

