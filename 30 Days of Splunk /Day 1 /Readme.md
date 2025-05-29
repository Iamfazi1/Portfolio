# 📅 Day 1 – Introduction to Splunk Search

## 🗓️ So It Begins...
Welcome to **Day 1** of the Splunk 30-Day Challenge! This is the start of your deep dive into one of the most powerful log analysis tools out there. 
You're basically about to become the Sherlock Holmes of cybersecurity.

---

## 🎯 What’s the Goal Today?
Let’s not overcomplicate it — you’re just gonna learn how to search logs in Splunk using `index=*`. Think of it like telling Splunk: *“Yo, show me everything you’ve got.”*  
And then we’ll narrow that down using `head` to avoid getting buried in a flood of data.

---

## 🧪 Lab Setup (If You’re Not Already Rolling)
If you don’t have Splunk running yet, don’t panic. You’ve got options:
- Use the [Splunk Free Trial](https://www.splunk.com/en_us/download.html) (easy and fast)
- TryHackMe’s [Splunk 101 Room](https://tryhackme.com/room/splunk101) (they basically set it up for you)
- Or just install it locally (Kali/Windows — your call)

---

## 🎬 Let’s Get Searching

### ✅ Step 1: Log into Splunk Web
- Open your browser and go to: `http://localhost:8000`
- Login with:
  - Username: `admin`
  - Password: the one you (hopefully) didn’t forget

*If you're already logged in, congrats — you're 10% done with today's task just by showing up.*

---

### ✅ Step 2: Run Your First Search
Paste this bad boy into the search bar:

```
index=*
```
🧠 What it means:
“Show me everything in all indexes, I wanna see the chaos.”

It’s like saying “Google, tell me literally everything about everything.” Not very specific, but hey — we’re learning.


✅ Step 3: Don’t Get Drowned – Use head
spl
Always show details

Copy

```
index=* | head 10
```

💡 Why?
This trims the madness. It’s like telling Splunk: “Okay chill, just give me the first 10 logs so I can actually breathe.”

Pro Tip: If nothing shows up, click on “Last 24 hours” and change it to “All time.” Sometimes logs are just shy.

✅ Step 4: Look at the Fields Panel
On the left sidebar, you’ll see “Interesting Fields.” And no, that’s not sarcasm — these fields are interesting. You’ll spot things like:

host

sourcetype

source

user, src_ip, etc.

Clicking one will filter your logs to those containing that field. Super handy.

🕵️ Real SOC Vibes
Pretend your boss walks up and says:

“Hey, check if anything weird happened today.”

You panic. Then you type:

spl
Always show details

Copy
```
index=* | head 20
```
You look like a wizard. Confidence level: 100.
You're basically just scoping out what's flowing into your environment.

🧾 What You Learned (a.k.a. Look How Smart You Are Now)
✅ How to log into Splunk Web

✅ How to use index=* to grab logs

✅ How to tame it with head

✅ How to browse and click fields like a pro

✅ How this ties into real-world analyst work
