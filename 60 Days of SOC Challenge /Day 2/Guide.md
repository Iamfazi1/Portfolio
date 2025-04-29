
# Task - Log Analysis Basics: Windows Security Logs

In this task, you will perform a basic log analysis by reviewing Windows Security logs. This will help you understand how to track logon events and detect suspicious activity in the system.

---

## Task Overview

In this task, we will:

1. Open and navigate the Event Viewer to locate Windows Security logs.
2. Filter logs to view successful and failed logon events.
3. Analyze logon events and identify potential security threats.
4. Document findings to help improve system security.

---

## Tools and Requirements

- **Windows OS** (any version with Event Viewer)
- **Event Viewer** to access Windows logs
- Basic understanding of Windows logon event IDs and their significance

---

## Step 1: Open Event Viewer

1. Press `Win + R` to open the **Run** dialog box.
2. Type `eventvwr.msc` and hit **Enter**. This will open **Event Viewer**.

---

## Step 2: Locate the Security Logs

1. In **Event Viewer**, expand the following:
   
   ```
   Applications and Services Logs > Microsoft > Windows > Security
   ```

2. Select **Security** under the Windows logs section. Here, you will find logs related to security events like logons, logoffs, account modifications, and more.

---

## Step 3: Filter Logs for Logon Events

1. Right-click on **Security** and choose **Filter Current Log**.

2. In the **Filter Current Log** window, enter the following Event IDs to filter logon events:
   - **4624** for successful logon attempts.
   - **4625** for failed logon attempts.

   These Event IDs will filter out unnecessary data and focus on logon events.

3. Click **OK** to apply the filter.

---

## Step 4: Review Logon Events

1. Now, the filtered logs will show only the logon events. Select an event from the list to view more details.

2. Focus on the following key information within each event:
   - **Account Name**: The user who attempted the logon.
   - **Logon Type**: Indicates the type of logon (e.g., interactive, remote).
   - **Source Network Address**: The IP address from where the logon attempt was made.
   - **Process Information**: The program used during the logon.

---

## Step 5: Analyze for Suspicious Activity

1. **Normal Activity**:
   - Logon attempts from known IP addresses (e.g., internal network or trusted locations).
   - Common logon types like **interactive** (direct login to the machine) or **remote interactive** (via RDP).

2. **Suspicious Activity**:
   - Logon attempts from unfamiliar or external IP addresses (e.g., from different countries or public networks).
   - Multiple failed logon attempts (Event ID 4625), which may indicate a brute force attack.
   - Unusual logon types such as **network** or **batch**, which could be suspicious depending on the scenario.

---

## Step 6: Document Findings

1. After analyzing the logs, make note of any suspicious patterns or activity you find (e.g., multiple failed logins, unexpected logon times).
2. Take screenshots or note down the log details to include in your report. This will be useful for further analysis or investigation.

---

## Key Takeaways

- **Event ID 4624**: Successful logon event.
- **Event ID 4625**: Failed logon attempt.
- Key fields to analyze: **Account Name**, **Logon Type**, **Source IP Address**.
- Identifying suspicious logon patterns can help detect unauthorized access attempts or attacks.

