# 📅 Day 2 – Meet the Log Family: Index, Sourcetype & Host

## 🗓️ Welcome Back, Data Detective

You survived Day 1 — congrats. Today we’re digging into **what those logs actually are** and **where they come from**. Because let’s be honest, searching `index=*` is cool and all... until you realize you have no clue what any of it means.

Time to meet the trio that keeps everything (barely) organized in Splunk: `index`, `sourcetype`, and `host`.

---

## 🎯 What’s the Goal Today?

Understand what the heck these mean:

* **index** – Where the logs are stored
* **sourcetype** – What kind of logs they are
* **host** – Where the logs came from

By the end of this, you’ll stop saying “What am I even looking at?” every time you run a search.

---

## 🧪 Lab Setup (Same as Yesterday — Don’t Skip This)

If Splunk isn’t running, pick your fighter:

* [Splunk Free Trial](https://www.splunk.com/en_us/download.html)
* [Splunk 101 Room on TryHackMe](https://tryhackme.com/room/splunk101)
* Local install on Kali/Windows

Once you’re in, you’re ready.

---

## 🕵️‍♂️ Step-by-Step Breakdown

### ✅ Step 1: Run the Usual Search

Paste this in the search bar:

```spl
index=*
```

Boom — a flood of logs. We’ve seen this before.



Now it’s time to decode the madness.

---

### ✅ Step 2: Look at the Left Sidebar (aka the "Fields Panel")

You’ll see fields like:

* `host`
* `sourcetype`
* `source`

These are your **keys to understanding** what the heck is going on in your logs.


<p align="center">
  <img src="https://media.giphy.com/media/l0MYt5jPR6QX5pnqM/giphy.gif" alt="Clicking through logs like a pro" />
</p>


Click on any of those to filter your logs by that value. It’s like going from total chaos to “Ohhh okay, now I get it.”

---

### ✅ Step 3: Break Down the Big Three

Let’s decode what each one means:

🧱 **Index**: Think of this like a folder full of logs. Different types of logs go into different indexes — kinda like sorting memes into folders. Helps you stay organized.

🗂️ **Sourcetype**: This tells Splunk what kind of data it’s looking at. Apache logs? Windows Event Logs? Syslog? This is the label for the type of data.

💻 **Host**: This one’s easy — it’s the machine or device that sent the log. Could be an IP, a hostname, or some box in your lab that won’t stop screaming.

---

### ✅ Step 4: Play Around With It

Try searching for specific values from your fields:

```spl
index=* sourcetype=YOUR_SOURCETYPE
```

```spl
index=* host=YOUR_HOST
```

Swap in actual values from your logs. Watch how it filters things beautifully.

---

### ✅ Bonus Flex: Use a Table

Want to look fancy? Use this:

```spl
index=* | table _time, host, sourcetype, source
```

Now it looks like you actually know what you're doing.

---

## 🧾 What You Learned Today (a.k.a. More Brain Muscles)

✅ What `index`, `sourcetype`, and `host` actually mean
✅ How to find them using the sidebar
✅ How to filter searches using them
✅ That you're already smarter than you were 10 minutes ago

Tomorrow? We start making this thing work for you with filtering and time ranges. You're gonna love it (or at least pretend you do).

