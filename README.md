# SOC Log Monitoring Dashboard (Splunk)

## 📌 Overview

This project simulates a **Security Operations Center (SOC)** dashboard using Splunk to monitor and analyze authentication logs.

The dashboard helps detect failed login attempts, identify suspicious IP addresses, and analyze targeted user accounts — similar to real-world SOC Level 1 analyst workflows.

---

## 🚀 Features

* 🔐 Login Status Overview (Success vs Failed)
* 🌐 Top Failed Login IPs
* 📊 Failed Login Activity Over Time
* 👤 Most Targeted Users

---

## 🛠 Technologies Used

* Splunk Enterprise
* SPL (Search Processing Language)
* Regex (`rex` command)

---

## 🔍 Key Queries

### Extract IP Addresses

```
index=* FAILED
| rex field=_raw "(?<ip>\d+\.\d+\.\d+\.\d+)"
| stats count by ip
```

### 🧾 Sample Log Format

2026-04-23 10:01:00, 192.168.1.10, admin, FAILED
2026-04-23 10:01:05, 192.168.1.10, admin, FAILED
2026-04-23 10:01:10, 192.168.1.20, john, FAILED


### Failed Login Activity Over Time

```
index=* FAILED
| timechart count
```

### Most Targeted Users

```
index=* FAILED
| rex field=_raw "(?<time>\d{4}-\d{2}-\d{2} \d{2}:\d{2}:\d{2}),\s*(?<ip>\d+\.\d+\.\d+\.\d+),\s*(?<user>\w+),\s*(?<status>\w+)"
| stats count by user
| sort -count
```

---

## 📸 Dashboard Preview
![SOC Dashboard](https://github.com/user-attachments/assets/785b0cd7-9b9b-40b5-8c58-91fdbbd0ac9b)


---

## 🎯 Key Detection Use Case

This dashboard helps identify potential **brute-force login attacks** by highlighting repeated failed login attempts from the same IP address or user account.

---

## 📚 What I Learned

* Log parsing and field extraction using regex
* Building dashboards in Splunk
* Identifying attack patterns from logs
* SOC-level monitoring and analysis

---

## ▶️ How to Reproduce

1. Install Splunk Enterprise (local instance)
2. Ingest sample authentication logs (CSV or text)
3. Run the SPL queries from the **Key Queries** section
4. Create dashboard panels for:
   - Login Status Overview
   - Top Failed Login IPs
   - Failed Login Activity Over Time
   - Most Targeted Users

## 🧠 Why This Matters

This project demonstrates how SOC analysts:
- Monitor authentication logs in real time
- Detect brute-force login attempts
- Identify high-risk IP addresses and user accounts
- Use SIEM tools (Splunk) for security analysis


## 🔮 Future Improvements

* 🚨 Add real-time alerting for brute-force attacks
* 📡 Integrate real-world log sources
* 🔍 Add drill-down investigation features
* 📈 Enhance dashboards with more advanced visualizations

---

## 👨‍💻 Author

📌 Open to SOC Analyst & Cybersecurity Internship Opportunities  

Dipan Khatri  
Cybersecurity Enthusiast | Aspiring SOC Analyst  

GitHub: https://github.com/Dipan-Khatri  
LinkedIn: https://www.linkedin.com/in/dipan-khatri/
