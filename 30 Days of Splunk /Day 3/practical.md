
# 📅 Day 3: Basic Filtering — Show Me the Fails!

In this practical, I’m going to show how to use simple Splunk searches to find failed logins and extract useful events using basic keywords and fields. No complex magic — just raw hunting power.

---

## 📸 Practical 1: Finding Failed Login Attempts

![Failed Logins](https://github.com/Iamfazi1/Portfolio/blob/main/60%20Days%20of%20SOC%20Challenge%20/img%20folder/image%20(8).png)

Here, I used this basic search:
```spl
index=* sourcetype=* fail OR failed
````

### 🔍 What it does:

* Shows any event that contains the word **fail** or **failed**
* Works great for catching logs like:

  ```
  Failed password for root from 192.168.x.x
  ```
* Helps you find **unauthorized access attempts** or **brute force activity**

💡 *Tip:* Use wildcards like `fail*` if you want to catch more variations (failed, failing, failure).

---

## 📸 Practical 2: Finding Logs with `url` Field

![URL Field Search](https://github.com/Iamfazi1/Portfolio/blob/main/60%20Days%20of%20SOC%20Challenge%20/img%20folder/image%20\(9\).png)

Here, I filtered for events that contain a `url` field using:

```spl
index=* sourcetype=* url=*
```

### 🔍 What it does:

* Pulls all events where a `url` field exists (like access logs)
* Helps you spot:

  * GET/POST requests
  * Suspicious URLs
  * Potential LFI/SQLi probes

---

## ✅ Summary Table

| Practical | Focus Area       | What You Searched For | Use Case                             |
| --------- | ---------------- | --------------------- | ------------------------------------ |
| 1️⃣       | Failed Logins    | `fail OR failed`      | Catch brute force/unauthorized tries |
| 2️⃣       | URL Field Events | `url=*`               | Analyze web access or attacks        |

---

That’s it for Day 3 — just basic filtering but super useful when you're first diving into real logs as a SOC analyst.

```

