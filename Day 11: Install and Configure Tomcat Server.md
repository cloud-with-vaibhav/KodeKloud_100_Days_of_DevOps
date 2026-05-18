# Task-11: Install and Configure Tomcat on App Server 1

## 📌 Objective

Deploy the Nautilus Java-based application on App Server 1 using Apache Tomcat.

Requirements:

- Install Tomcat server
- Configure Tomcat to run on port `3000`
- Deploy the provided `ROOT.war` application
- Ensure the application is accessible directly using:

```bash
curl http://stapp01:3000
```
---
## 🛠️ Implementation Steps
### 1. Login to App Server 1
`ssh tony@stapp01`

📦 Install Tomcat Server
### 2. Install Required Packages

Install Java and Tomcat:
```bash
sudo yum install -y tomcat
```

### 3. Verify Tomcat Installation

Check installed Tomcat version:
```bash
rpm -qa | grep tomcat
```


### ⚙️ Configure Tomcat to Run on Port 3000
### 4. Edit Tomcat Configuration File

Open Tomcat server configuration:
```bash
sudo vi /etc/tomcat/server.xml
```
Find the following connector configuration:
```xml
<Connector port="8080" protocol="HTTP/1.1"
           connectionTimeout="20000"
           redirectPort="8443" />
```
Change port 8080 to 3000:
```xml
<Connector port="3000" protocol="HTTP/1.1"
           connectionTimeout="20000"
           redirectPort="8443" />
```

Save and exit the file.

---
### 📁 Deploy the Application
### 5. Copy ROOT.war from Jump Host

From Jump host, copy the WAR file to App Server:
```bash
scp /tmp/ROOT.war tony@stapp01:/tmp/
```

Enter password if prompted.

### 6. Deploy ROOT.war to Tomcat

Copy the WAR file to Tomcat webapps directory:
```bash
sudo cp /tmp/ROOT.war /usr/share/tomcat/webapps/
```


### ▶️ Start and Enable Tomcat Service
### 7. Start Tomcat Service
```bash
sudo systemctl start tomcat
```

### 8. Enable Tomcat Service
```bash
sudo systemctl enable tomcat
```
### 9. Verify Tomcat Service Status
```bash
sudo systemctl status tomcat
```

### 10. Verify Application Access
```bash
curl http://stapp01:3000
```
---

✅ Conclusion
- Tomcat installed successfully on App Server 1
- Tomcat configured to run on port 3000
- ROOT.war deployed successfully
- Tomcat service started and enabled
- Application accessible successfully using:


