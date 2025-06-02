# 📅 Day 3 – Basic Filtering in Splunk

## 🎯 Objective

Learn how to use basic search filters in Splunk to find failed or error-related events using `index=*` and `sourcetype=*`.

---

## 🤔 What are Events?

An **event** in Splunk is basically one entry from your log files. Think of it like one line in a diary entry — something happened, and it got recorded. Examples:

* SSH login attempt
* Email delivery status
* Firewall blocking a connection

Each of these moments becomes an **event** in Splunk once it’s indexed.

---

## 🔥 Real Examples of Events

### SSH Event

```text
Jun 1 12:21:15 kali sshd[1042]: Failed password for root from 192.168.1.101 port 22 ssh2
```

### Email Log Event

```text
Jun 1 13:42:11 mail postfix/smtp[3827]: 9C49F40234: to=<user@example.com>, relay=gmail-smtp-in.l.google.com[74.125.140.27]:25, status=sent
```

In both examples, a single line = one event.

---

## 💡 Splunk Search Basics

To search everything (every log line Splunk knows about):

```spl
index=* sourcetype=*
```

But that’s like looking for a needle in a stack of needles.

So let’s **filter**!

### 🔍 Find Failed Events

```spl
index=* sourcetype=* (error OR fail)
```

This search looks through **all indexes** and **all sourcetypes**, but narrows it down to logs containing `error` or `fail`.

### Example Output:

* Failed login to server
* Mail delivery failed
* Application crashed

---

## 🧪 Test it Yourself

1. Open Splunk Search & Reporting app.
2. Type:

```spl
index=* sourcetype=* fail
```

3. Look through results and try identifying:

   * What system did this come from?
   * Was it a login failure? Application error?

---

## ✉️ Email Log Breakdown Example

Here’s what a typical email event might look like:

```text
status=bounced, to=user@example.com, reason=recipient not found
```

| Field  | Value                                       |
| ------ | ------------------------------------------- |
| status | bounced                                     |
| to     | [user@example.com](mailto:user@example.com) |
| reason | recipient not found                         |

These fields are searchable too:

```spl
index=email_logs status=bounced
```

---

## 🧠 Final Notes

* **index**: Tells Splunk where to search.
* **sourcetype**: Tells Splunk what type of data this is (firewall logs, email logs, etc).
* **error/fail**: Are just keywords. You’re looking for any event that mentions them.

---

## ✅ Mission Accomplished

You now know how to:

* Understand what events are
* Use basic filters in Splunk
* Find failed/error logs across different sources


