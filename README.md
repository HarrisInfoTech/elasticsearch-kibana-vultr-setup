# 🟢 Elasticsearch & Kibana Deployment — **Vultr Cloud**

This project demonstrates how I deployed and configured **Elasticsearch** and **Kibana** on an **Ubuntu 22.04 server** hosted on **Vultr**.  
The goal is to simulate a **Security Information & Event Management (SIEM)** environment for log collection, monitoring, and visualization.

---

## **📌 Project Overview**
- **Cloud Provider:** Vultr  
- **Operating System:** Ubuntu 22.04 LTS  
- **Tools Installed:** Elasticsearch & Kibana  
- **Use Case:** Log ingestion, monitoring, and visualization  
- **Portfolio Type:** SOC Analyst / IT Technician / Cybersecurity  

---

## **📂 Lab Architecture**

| **Component**      | **Purpose**                | **OS / Tool** |
|--------------------|---------------------------|---------------|
| Vultr Cloud Server | Host environment          | Ubuntu 22.04 |
| Elasticsearch      | Data indexing & storage  | v8.x.x |
| Kibana             | Visualization dashboard  | v8.x.x |
| Analyst Machine    | Access & monitoring      | Windows 11 |

📸 *Screenshot Placeholder: Architecture Diagram*  
![Architecture Diagram](./screenshots/lab-architecture.png)

---

## **⚡ Prerequisites**
Before starting, make sure you have:
- A **Vultr account** with **VPC 2.0** enabled  
- A deployed **Ubuntu 22.04 server**  
- Opened **ports 9200** (Elasticsearch) & **5601** (Kibana) in Vultr firewall  
- SSH access via PowerShell, Terminal, or PuTTY  

---

## **🛠️ Installation & Configuration**

### **Step 1 — Deploy Server on Vultr**
1. Go to [Vultr Dashboard](https://my.vultr.com/).  
2. Deploy an **Ubuntu 22.04 x64** instance.  
3. Assign a hostname and enable **VPC 2.0 networking**.  

📸 *Screenshot:*  
![Vultr Instance Summary](./screenshots/vultr-instance-summary.png)

---

### Step 2 — Update the Server
```bash
sudo apt update && sudo apt upgrade -y
```

📸 *Screenshot:*  
![Server Updates](./screenshots/server-update.png)

### Step 3 — Install Elasticsearch
```bash
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-8.x.x-amd64.deb
sudo dpkg -i elasticsearch-8.x.x-amd64.deb
```
📸 *Screenshot:*  
![Install Elasticsearch](./screenshots/elasticsearch-install-success.png)

Step 4 — Configure Elasticsearch
```bash
sudo nano /etc/elasticsearch/elasticsearch.yml
```
Inside the config file, I made the following changes:

Changed network.host to my Elasticsearch server’s IP address (removed the # to enable it).

Removed the # before http.port: 9200 to enable the HTTP port.

network.host: 144.*.*.*
http.port: 9200

📸 *Screenshot:*  
![Elasticsearch Config](./screenshots/elasticsearch-config.png)

### Step 5 — Secure Access with Vultr Firewall Rules
To improve security, I updated my **Vultr Firewall Group** so that only **my IP address** could connect to the server:

- **Port 22 (SSH)** → Allowed from my IP only  
- All other ports → Blocked by default  

This prevents unauthorized access while I continue configuring Elasticsearch and Kibana.

📸 *Screenshot:*  
![Vultr Firewall Rules](./screenshots/vultr-firewall-rule.png)


