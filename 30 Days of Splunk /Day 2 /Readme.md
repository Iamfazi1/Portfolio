
# 📅 Day 2 – Meet the Log Family: Index, Sourcetype & Host

<p align="center">
  <img src="https://media.giphy.com/media/l0MYt5jPR6QX5pnqM/giphy.gif" alt="Searching logs" />
</p>

---

## 🏷️ What Are Index, Sourcetype, and Host?

Before diving in, let’s break down these three Splunk keywords — because you'll use them in almost every search:

| Field          | What It Means                            | Real-World Analogy                        | Example Search Syntax       |
| -------------- | ---------------------------------------- | ----------------------------------------- | --------------------------- |
| **Index**      | The storage location (bucket) for logs   | Filing cabinet (e.g. Sales, HR, IT files) | `index=security_logs`       |
| **Sourcetype** | The format/type of the incoming log data | Type of document (Invoice, Resume, Alert) | `sourcetype=aws:cloudtrail` |
| **Host**       | The system or device that sent the log   | Sender of the document (PC, Server, etc.) | `host="web-02-server"`      |

✨ **Simple Analogy**:

* **Index** = Folder the log goes into
* **Sourcetype** = What kind of paper it is
* **Host** = Who sent it

---

## 🧭 Situation: You’re New and Need to Explore What’s in Splunk

Let’s say you’ve just started in a new SOC role.

You open Splunk and realize… you have **no idea** what logs are coming in.

You don’t know what **indexes** are available, and you don’t know what **sourcetypes** are in use.

💡 That’s okay — Splunk has your back.

To discover this, you can run two simple commands to list **all available indexes** and the **sourcetypes each one contains**.

---

## 🔍 How to List Indexes and Sourcetypes in Your Splunk

Here’s the quick command that gives you both indexes and their sourcetypes in one table:

```spl
| tstats values(sourcetype) as sourcetypes where index=* by index
```

🧾 **What This Does:**

* `tstats` — a super-fast command that works on indexed data.
* `values(sourcetype)` — grabs all sourcetypes seen in each index (no count, just unique names).
* `where index=*` — filters data from all indexes.
* `by index` — groups the results by each index name.

This gives you a clean table like:

| index          | sourcetypes                           |
| -------------- | ------------------------------------- |
| security_logs  | WinEventLog:Security, xmlwineventlog |
| aws            | aws:cloudtrail, aws:s3              |
| firewall_logs  | cisco:asa, palo:traffic             |

📌 **Don’t worry about how `tstats` works in detail — we’ll break it down in future lessons. For now, just think of it as your Splunk radar scanner.**

---

## 🔎 How to Know What Logs Are Stored Under Each Sourcetype?

Now you might ask:
**“Okay... so I know my indexes and sourcetypes, but how do I know what kind of logs are inside them?”**

It’s actually a bit complex (since every company configures Splunk differently), but here are some **typical log types and their matching sourcetypes** used in most environments:

---

## 🧠 Common Sourcetypes Based on Log Category

| Log Category    | Typical Sourcetypes              | Example Events                |
| --------------- | -------------------------------- | ----------------------------- |
| **Firewall**    | `cisco:asa`, `palo:traffic`      | "Deny TCP", URL filtering     |
| **Windows**     | `WinEventLog:Security`, `System` | EventCode 4625 (Failed Login) |
| **Web Servers** | `apache:access`, `iis:www`       | POST requests, 500 errors     |
| **Databases**   | `mysql:error`, `mssql:audit`     | Deadlocks, failed logins      |
  
</p>

🎯 **Quick Lookup Tips:**

* Want login activity? → Try `WinEventLog:Security`
* Want blocked traffic? → Try `cisco:asa` or `palo:traffic`
* Want website issues? → Try `apache:access` or `iis:www`

---

## ✅ Day 2 Summary – Getting Oriented in Splunk

* 🧭 Use the `tstats` command to explore all available indexes and their sourcetypes.
* 🏷️ Understand the three core metadata fields:

  * `index` — where the log is stored
  * `sourcetype` — what kind of log it is
  * `host` — where the log came from
* 📚 Use the sourcetype cheat sheet above to understand what type of logs you’re looking at.

➡️ **Next stop:** Learn how to filter by time.
