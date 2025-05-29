# 🧠 Splunk 30-Day Challenge: From Logs to Mastery

Welcome to my **Splunk 30-Day Learning Challenge** — a hands-on journey to mastering Splunk, one query at a time. This self-paced challenge is part of my **SOC Analyst portfolio** to demonstrate practical skills in **log analysis**, **threat detection**, and **security operations** using Splunk.

### 🔥 Why I’m Doing This

Splunk is one of the most powerful tools in the SOC world. Every day for 30 days, I’ll focus on a new concept, query, or detection technique using real-life logs, SPL (Search Processing Language), and investigation practices. By the end of this challenge, I’ll have a strong foundation in:
- Building powerful searches
- Detecting real-world attacks
- Creating alerts and dashboards
- Performing incident investigations like a true SOC analyst

---

## 🗓️ Daily Progress Table

| Day | Title                                  | Task Description                                                                 | Skill Level     |
|-----|----------------------------------------|----------------------------------------------------------------------------------|-----------------|
| 1   | Introduction to Splunk Search          | Use `index=*` and explore Splunk Web. Use `head` to see 10 events.              | 🟢 Beginner      |
| 2   | Index, Sourcetype, and Fields          | Search `index=*` and understand what `index`, `sourcetype`, and `host` mean.    | 🟢 Beginner      |
| 3   | Basic Filtering                        | Use `index=* sourcetype=* error OR fail` to find failed events.                 | 🟢 Beginner      |
| 4   | Time Filtering                         | Use `_time`, `earliest`, `latest` and `relative_time` to search specific dates. | 🟢 Beginner      |
| 5   | Stats Command                          | Use `stats count by host` and `stats avg(bytes) by src_ip`.                     | 🟢 Beginner      |
| 6   | Fields Discovery                       | Use `fields`, `table`, and `rename` commands.                                   | 🟢 Beginner      |
| 7   | Count Failed Logins (Windows)          | Search `EventCode=4625` and group by user.                                      | 🟢 Beginner      |
| 8   | Top Talkers in Firewall Logs           | Search `index=firewall` and use `top src_ip`.                                   | 🟢 Beginner      |
| 9   | Where vs Search                        | Learn the difference using `where` and `search` filters.                        | 🟢 Beginner      |
| 10  | Detect PowerShell Execution            | Search `index=wineventlog EventCode=4104 OR 4688` and extract commands.         | 🟡 Intermediate  |
| 11  | Detect USB Insertion                   | Use `EventCode=2003` or relevant Device ID logs to find USB use.                | 🟡 Intermediate  |
| 12  | Detect RDP Logins                      | Search `EventCode=4624` with `LogonType=10` (RDP).                              | 🟡 Intermediate  |
| 13  | SSH Failed Logins (Linux)              | Search `/var/log/auth.log` using `sshd` and `Failed password`.                  | 🟡 Intermediate  |
| 14  | Brute-force Detection                  | Count multiple failed logins from same IP/user.                                 | 🟡 Intermediate  |
| 15  | GeoIP Lookup for Suspicious IPs        | Use `iplocation src_ip` and `stats count by Country`.                           | 🟡 Intermediate  |
| 16  | Search with rex and regex              | Extract fields manually using `rex field=_raw`.                                 | 🟡 Intermediate  |
| 17  | Detect Scheduled Tasks / Persistence   | Search for `schtasks.exe` or `EventCode=4698`.                                  | 🟡 Intermediate  |
| 18  | Search with tstats                     | Use `tstats count where index=* by sourcetype` to save license.                 | 🟡 Intermediate  |
| 19  | Detect File Access                     | Use `EventCode=4663` to find file opens/deletes.                                | 🟡 Intermediate  |
| 20  | Alert on Repeated Failures             | Build SPL that alerts if >5 failed logins from same user in 5 min.              | 🟡 Intermediate  |
| 21  | Detect Lateral Movement                | Combine RDP login and PowerShell activity across hosts.                         | 🔴 Advanced      |
| 22  | Data Model Search                      | Use `tstats summariesonly=true count from datamodel=Authentication...`          | 🔴 Advanced      |
| 23  | Detect Web Shell or Reverse Shell      | Search `cmd.exe` or `powershell` + suspicious IPs.                              | 🔴 Advanced      |
| 24  | Timeline of User Activity              | Create user activity timeline using `timechart`.                                | 🔴 Advanced      |
| 25  | Detect Data Exfiltration               | Monitor upload volume using `stats sum(bytes_out) by user`.                     | 🔴 Advanced      |
| 26  | Splunk Lookup Table                    | Add a lookup of bad IPs and match against logs.                                 | 🔴 Advanced      |
| 27  | Build Dashboard Panel                  | Visualize failed logins by user and by location.                                | 🔴 Advanced      |
| 28  | Create an Alert                        | Set up an alert for multiple failed logins from unknown IPs.                    | 🔴 Advanced      |
| 29  | Report Generation                      | Schedule a PDF report for login activity summary.                               | 🔴 Advanced      |
| 30  | Mock Interview Use-Case Investigation | Use given logs to investigate compromise scenario with multiple queries.        | 🟣 Expert        |

---

### 📁 Repo Structure (Coming Soon)

- `/daily-logs`: Daily SPL queries and notes
- `/dashboards`: JSON or XML Splunk dashboard exports
- `/alerts`: Reusable alert templates
- `/reports`: Sample PDF/CSV reports

---

### ✅ Goals

- 🔍 Build real-world detection logic  
- 📊 Create reusable dashboards & alerts  
- 🧠 Understand core Splunk concepts deeply  
- 💼 Add SOC analyst-ready projects to my portfolio  

---

### 📌 Notes

- 🔄 This challenge is self-paced but designed to be **one task per day**
- 🧪 All searches tested in a local Splunk lab (Free license)
- 📈 Each day will help build toward full confidence in **SPL** and **incident investigation**

---

### 🙋‍♂️ About Me

I’m **Faizan**, an aspiring **SOC Analyst** passionate about threat detection, automation, and blue teaming. This challenge is part of my hands-on learning journey, and you're welcome to follow along or fork the project.

📫 [LinkedIn](https://www.linkedin.com/in/muhmmadfaizanshakir/)  
🔗 [TryHackMe](https://tryhackme.com/p/faizanshakir123)  
💻 [GitHub Portfolio](https://github.com/Iamfazi1)

---

> ⭐️ Star this repo if you'd like to take the challenge too!  
> 📩 Open an issue if you want me to make this into a public template.

