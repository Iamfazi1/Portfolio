# 🛠️ Day 2 Practical – Manually Finding Indexes & Sourcetypes via Settings

In the Day 2 guide, we already talked about how to discover available indexes and sourcetypes using search commands (`eventcount`, `metadata`, etc.). But if you don’t want to use the Sigma/search way, here's how you can do it manually from the Splunk UI.

> This is helpful especially if you're new and just want to explore what's already set up without touching search yet.

---

## 📍 Step-by-Step (No Commands, Just Settings)

### 🔹 Step 1: Go to Settings
Click the gear icon in the top-right corner or just hover over the "Settings" menu.

📸 ![Settings](https://github.com/Iamfazi1/Portfolio/blob/main/60%20Days%20of%20SOC%20Challenge%20/img%20folder/image%20(4).png)

---

### 🔹 Step 2: View Indexes
Under the “Data” section, click on **Indexes**. This will show you all the indexes available in your Splunk environment. Each one is clickable — though we’re not diving into them just yet.

📸 ![Indexes List](https://github.com/Iamfazi1/Portfolio/blob/main/60%20Days%20of%20SOC%20Challenge%20/img%20folder/image%20(7).png)

---

### 🔹 Step 3: View Sourcetypes
Next, click on **Sourcetypes** under the “Data” section as well. This gives you a list of all the sourcetypes (log formats) currently configured in Splunk.

📸 ![Sourcetypes](https://github.com/Iamfazi1/Portfolio/blob/main/60%20Days%20of%20SOC%20Challenge%20/img%20folder/image%20(6).png)

---

### 🧪 Example: Using Search to Confirm (Optional)
Just for reference, if you *do* want to try the search method, here’s how it looks:

📸 ![Search Example](https://github.com/Iamfazi1/Portfolio/blob/main/60%20Days%20of%20SOC%20Challenge%20/img%20folder/image%20(3).png)

---

## ✅ That’s It
So yeah, if you don’t feel like typing search commands or just want to explore with clicks, Splunk Settings makes it easy to peek into the environment and see what's going on.

We'll be using these indexes and sourcetypes in future searches and threat hunting — so make sure you get familiar with them.

---

