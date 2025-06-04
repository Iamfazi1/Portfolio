

# 📅 Day 4 – Mastering Time Filtering in Splunk

## 🎯 Objective

Understand how to narrow your searches based on time using:

* `_time`
* `earliest`
* `latest`
* `relative_time()`

This helps you **zoom in** on the logs that matter, like finding failed logins **only from yesterday** or attacks **in the last 15 minutes**.

---

## ⏰ What is `_time` in Splunk?

Every event in Splunk has a **timestamp**. This is stored in a field called `_time`.

### 🔎 Think of `_time` like:

> The exact moment the log event was recorded.

🧠 **Analogy**: If events are diary entries, `_time` is the date/time written at the top of each page.

### Example Event:

```
_time=2025-06-03T14:22:03.000+05:00
host=webserver1
sourcetype=apache:access
event=User login successful
```

---

## 🧪 Why Use Time Filtering?

Without time filtering, you’re searching **ALL events** — past days, weeks, months.

That’s slow and noisy. You want **surgical precision**.

---

## 🛠️ Time Filter Methods in Splunk

### 1. **`earliest`** and **`latest`** – Basic Time Filtering

These tell Splunk *when to start* and *when to stop* the search.

```spl
index=* sourcetype=* fail earliest=-15m latest=now
```

📌 **Translation**: Show all failed events from the last 15 minutes.

⏱ Common Time Shortcuts:
<div align="center">

| Shortcut | Meaning            |
| -------- | ------------------ |
| `-15m`   | 15 minutes ago     |
| `-1h`    | 1 hour ago         |
| `-24h`   | 24 hours ago       |
| `-7d`    | 7 days ago         |
| `@d`     | Start of today     |
| `@w`     | Start of this week |
| `now`    | Current moment     |

</div>

### ✅ Example: Last 24 Hours of SSH Failures

```spl
index=linux_logs sourcetype=linux_secure "Failed password" earliest=-24h latest=now
```

🎯 You’ll see only failed logins that occurred in the past 24 hours.

---

### 2. **Using the Time Picker (GUI Method)**

When you search in Splunk’s Search App, use the **Time Picker** in the top-right corner.

Select presets like:

* Last 15 minutes
* Today
* Last 7 days
* Custom range

Splunk automatically applies `earliest` and `latest` under the hood.

---

### 3. **`relative_time()` Function – Time Math Inside Search**

Used when you want to do **time-based comparisons** inside the search pipeline.

#### Example:

Find events that happened in the *last hour only*:

```spl
index=web_logs 
| where _time > relative_time(now(), "-1h")
```

💡 `relative_time(now(), "-1h")` = 1 hour ago from now

---

## 🎥 Example Log Events with `_time`

### SSH Failure

```
_time=2025-06-03T13:12:20
sshd[2014]: Failed password for root from 10.0.0.5 port 22 ssh2
```

### Email Bounce

```
_time=2025-06-03T09:43:10
status=bounced, to=user@example.com, reason=user not found
```

Now you can ask:

> “Show me all bounce events in the last 6 hours”

```spl
index=mail sourcetype=postfix status=bounced earliest=-6h
```

---

<div align="center">

| Search Example            | What You Should See                           |                             |
| ------------------------- | --------------------------------------------- | --------------------------- |
| `earliest=-1h latest=now` | Events from the last 60 minutes               |                             |
| `earliest=-7d@d`          | Events from 7 days ago starting at midnight   |                             |
| `earliest=@w`             | Events from the beginning of this week        |                             |
| `where _time > relative_time(now(), "-2d")` | Events from the last 2 days |                             |

</div>

---

## 🧠 Memory Hack – Splunk Time Tricks

🧩 Think of `earliest` as the "start gate"
🧩 Think of `latest` as the "finish line"

🧠 **Analogy**: You're watching CCTV footage. `earliest` is when you hit “Play,” `latest` is when you hit “Pause.”

---

## ✅ Summary – Day 4 Takeaways

* `_time` is the timestamp of each event.
* Use `earliest` and `latest` in your search to filter based on time.
* Use `-15m`, `-24h`, `@d` for relative time filtering.
* Use `relative_time()` in search pipelines for flexible filtering.
* Expected results depend on your defined time window — precise, fast, and relevant.


