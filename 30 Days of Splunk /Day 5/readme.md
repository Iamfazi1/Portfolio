# 📊 Day 5 – Stats Command Mastery

---

## 🧠 What You’ll Learn Today

The `stats` command is like Excel’s Pivot Table inside Splunk. It helps you **summarize, count, and average** your data in super powerful ways.

Today, we’ll break down two popular examples:

* `stats count by host`
* `stats avg(bytes) by src_ip`

But that’s just the start. We’ll expand with real-world use cases like failed login tracking and identifying top data senders.

---

## 🧰 The Basics – What These Do

### 🔹 `stats count by host`

* Groups all events **by host**
* Shows the **number of events** from each host

```spl
index=* | stats count by host
```

📊 Output Example:

<div align="center">

| host            | count |
| --------------- | ----- |
| server01        | 5234  |
| 10.10.10.2      | 2121  |
| webserver.local | 892   |

</div>

---

### 🔹 `stats avg(bytes) by src_ip`

* Averages the `bytes` field for each `src_ip`
* Useful for network monitoring and data exfil detection

```spl
index=* | stats avg(bytes) by src_ip
```

📊 Output Example:

<div align="center">

| src\_ip     | avg(bytes) |
| ----------- | ---------- |
| 192.168.1.5 | 348        |
| 8.8.8.8     | 5891       |
| 10.0.0.2    | 193        |

</div>

---

## 🎯 5 Real-World Use Cases Using `stats`

These aren’t just examples—they're common SOC analyst moves in the field:

### 🔐 1. Which user had the most failed login attempts?

```spl
index=win_events sourcetype=WinEventLog:Security EventCode=4625
| stats count by user
| sort -count
```

👉 Shows usernames with the highest number of failed login attempts.

---

### 🌐 2. Which user sent the most data?

```spl
index=network sourcetype=proxy_logs
| stats sum(bytes) as total_bytes by user
| sort -total_bytes
```

👉 Tracks total outbound data by user — great for finding potential data leaks.

---

### 🧑‍💻 3. Which IP addresses triggered the most alerts?

```spl
index=alerts sourcetype=security_alerts
| stats count by src_ip
| sort -count
```

👉 Spot the most noisy or malicious source IPs.

---

### 🕵️‍♂️ 4. Average login failures per host

```spl
index=win_events sourcetype=WinEventLog:Security EventCode=4625
| stats avg(count) by host
```

👉 Detects hosts that are repeatedly failing authentication.

---

### 📨 5. How many emails were sent per user?

```spl
index=o365 sourcetype=o365:email
| stats count by user
```

👉 Can be used to monitor email usage or potential abuse.

---

## 📝 Summary

<div align="center">

| What You Did | Command Example                             | Use Case                   |
| ------------ | ------------------------------------------- | -------------------------- |
| Count Events | `stats count by host`                       | See event volume per host  |
| Average Size | `stats avg(bytes) by src_ip`                | Detect large senders       |
| Failed Users | `stats count by user`                       | Find failed login users    |
| Data Volume  | `stats sum(bytes) by user`                  | Identify top data senders  |
| Mail Volume  | `stats count by user` (on email sourcetype) | Track sent emails per user |

</div>

---

✅ With these tricks, you're now getting serious visibility into **who did what**, **where**, and **how much** — one of the core skills of any SOC analyst.
