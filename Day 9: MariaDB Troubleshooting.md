# Task-10: MariaDB Troubleshooting on Database Server

## 📌 Objective

The Nautilus application was unable to connect to the database because the MariaDB service was down on the database server.

The goal of this task is to:

- Diagnose the MariaDB service issue
- Fix the root cause
- Restore database connectivity
- Ensure the MariaDB service starts successfully

---

# 🛠️ Troubleshooting and Resolution Steps

## 1. Check MariaDB Service Status

Verify whether the MariaDB service is running:

```bash
systemctl status mariadb
```
Observation:

Service was found in a failed/down state.

## 2. Attempt to Start MariaDB Service

Try starting the service manually:
```bash
systemctl start mariadb
```
The service failed to start.

## 3. Check Detailed Error Logs

Inspect MariaDB service logs for the root cause:
```bash
journalctl -xeu mariadb.service
```
Observation:

Errors indicated issues related to the MariaDB data directory.

## 4. Verify MySQL Data Directory

Check whether the MariaDB data directory exists:
```bash
ls -l /var/lib/mysql
```
Observation:

`/var/lib/mysql` directory was missing.

## 5. Create Missing Data Directory

Create the required MariaDB data directory:
```bash
mkdir /var/lib/mysql
```
## 6. Set Correct Ownership

Assign proper ownership to the MySQL user:
```bash
chown -R mysql:mysql /var/lib/mysql
```
This ensures MariaDB has permission to access the directory.

## 7. Initialize MariaDB Database Files

Initialize the MariaDB data directory:
```bash
mariadb-install-db --user=mysql --datadir=/var/lib/mysql
```
This command creates:

System database files
Default tables
Initial database structure

## 8. Start MariaDB Service Again

Start the MariaDB service:
```bash
systemctl start mariadb
```
The service started successfully.

## 9. Verify MariaDB Service Status

Check the service status again:
```bash
systemctl status mariadb
```
Expected output:

`active (running)`

## 10. Enable MariaDB Service at Boot

Enable MariaDB service to start automatically after reboot:
```bash
systemctl enable mariadb
```

---

✅ Conclusion

- MariaDB service issue diagnosed successfully
- Missing data directory recreated
- Database initialized correctly
- MariaDB service restored and running
- Service enabled for automatic startup
- Nautilus application database connectivity restored

