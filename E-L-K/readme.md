# Elastic Malware Detection Lab

Welcome to the **Elastic Malware Detection & Analysis Project**. This lab walks through the full lifecycle of preparing a safe lab environment, creating and testing detection rules, using both benign and malware samples, and refining detection logic based on observed events. This README provides structure, explanations, and a bit of humor with GIF placeholders to keep the experience fun.

---

## <p align="center">

  <img src="https://media.giphy.com/media/3o7aD2saalBwwftBIY/giphy.gif" />
</p> Harden and Verify Your Lab Setup
Before testing malware, ensure your lab is isolated, safe, and controlled.
- Use a **virtualized environment** (VMWare, VirtualBox, Hyper-V).
- Disable network bridging unless required.
- Snapshot the VM for easy rollback.

> *"When you think your VM is safe... and then you realize you forgot to disable shared folders."*

<p align="center">
  <img src="https://media.giphy.com/media/l46Cy1rHbQ92uuLXa/giphy.gif" />
</p>

---

## <p align="center">

  <img src="https://media.giphy.com/media/26gslU06gE2I7UOHm/giphy.gif" />
</p> Add & Configure Integrations for Security Data
Integrate Elastic with:
- **Elastic Agent**
- **Endpoint Security**
- **Sysmon** (optional but recommended)
- **Fleet Server**

This enables collecting logs, process events, file integrity monitoring, registry changes, etc.

---

## <p align="center">

  <img src="https://media.giphy.com/media/xT9IgzoKnwFNmISR8I/giphy.gif" />
</p> Create a Basic Pre-built Detection Rule in Kibana
Start with an out-of-the-box detection rule.
- Enable a pre-built rule (e.g., malware, privilege escalation, suspicious process).
- Understand its logic and expected trigger conditions.

> *"Clicking **Enable Rule** like a pro hacker... even though it's pre-built."*

<p align="center">
  <img src="https://media.giphy.com/media/26u4cqiYI30juCOGY/giphy.gif" />
</p>

---

## <p align="center">

  <img src="https://media.giphy.com/media/26xBKqeFFIYpMZQ8w/giphy.gif" />
</p> Test the Basic Rule with Benign Activity (FP/TP Check)
Simulate harmless activity similar to malware behavior:
- Run PowerShell commands
- Create harmless files
- Trigger simple alerts

Analyze alerts:

* **False Positive (FP)**: Rule fired on clean/expected behavior
* **True Positive (TP)**: Rule correctly flagged abnormal behavior

---

## <p align="center">

  <img src="https://media.giphy.com/media/3orifdG7m3HyIlXqRa/giphy.gif" />
</p> Prepare a Harmless Test Malware (EICAR)
Download the **EICAR test file** — a safe industry-standard anti-malware test pattern.
- Store it in various locations
- Observe endpoint behavior

> **EICAR is NOT malware** — it's literally a text string. But your tools treat it like a threat.

<p align="center">
  <img src="https://media.giphy.com/media/13borq7Zo2kulO/giphy.gif" />
</p>

---

## Execute the Test Malware & Capture Initial Events

Run the EICAR file:

* Observe alerts from Elastic Endpoint
* Check process → file → alert relationships
* Validate if the rule catches it

---

## Analyze Captured Events and Refine Queries

Break down the captured telemetry:

* Process execution metadata
* File writes & hashes
* Parent-child process chains
* Network behavior (if applicable)

Refine your rule query to:

* Reduce false positives
* Improve coverage for malicious behavior

---

## <p align="center">

  <img src="https://media.giphy.com/media/l0HlPjezGYXzGJfN6/giphy.gif" />
</p> Create a Custom Advanced Detection Rule
Build an advanced rule using:
- KQL
- EQL (for process sequences)
- Threshold logic
- Behavior-based detections

Example behaviors:

* Mass encryption attempts
* Suspicious PowerShell decoding
* Persistence creation

---

## Select, Download, and Execute a Real Malware Sample (e.g., WannaCry)

> ⚠️ **WARNING: Use a secure, isolated malware analysis lab. NEVER run real malware on your host machine.**

Choose a real sample from trusted research sources like:

* MalwareBazaar
* TheZoo
* VX-underground (research only)

Execute it safely and capture:

* Process trees
* Encryption behavior
* DLL loads
* Network calls

<p align="center">
  <img src="https://media.giphy.com/media/3oEjHP8ELRNNlnlLGM/giphy.gif" />
</p>

---

## Perform Detailed Analysis & Verdict (FP/TP)

For each alert:

* **True Positive (TP)** → Indicators match expected malicious behavior
* **False Positive (FP)** → Expected or normal behavior triggered the rule

Refine rules to:

* Reduce noise
* Increase detection accuracy

Examples:

* Add parent process constraints
* Remove noisy paths (Dev tools, admin tools)
* Add behavioral sequences

---

## Final Outcome

By the end of this project you will have:

* A fully hardened malware testing lab
* Working Elastic integrations
* Basic + advanced detection rules
* Clear understanding of FP vs TP analysis
* Event telemetry for EICAR and real malware
* Optimized detection logic

---

## 🎉 Closing GIF

<p align="center">
  <img src="https://media.giphy.com/media/111ebonMs90YLu/giphy.gif" />
</p>

---


  <img src="https://media.giphy.com/media/111ebonMs90YLu/giphy.gif" />
</p>

Enjoy your malware detection journey — safely!
