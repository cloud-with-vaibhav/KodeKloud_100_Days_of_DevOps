Question: Following security audits, the xFusionCorp Industries security team has rolled out new protocols, including the restriction of direct root SSH login.

Your task is to disable direct SSH root login on all app servers within the Stratos Datacenter.

Solution:
1. Edit SSH Configuration on each app server:
```sudo vi /etc/ssh/sshd_config```
2. Find this line:
```PermitRootLogin yes```
3. Change it to:
```PermitRootLogin no```
4. Restart sshd service:
   ```sudo systemctl restart sshd```
