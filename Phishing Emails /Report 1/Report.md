# **Phishing Email Analysis Report**  
**Analyzed by:** Faizan Shakir  
**Date:** April 28, 2025  

---

## **1. Executive Summary**  
A phishing email impersonating **MetaMask Support** was analyzed. The email falsely claims that unverified wallets will be "terminated" and directs victims to a malicious link (`420.bio/NtRIA`) designed to steal credentials.  

### **Key Findings**  
- ✅ **Confirmed Malicious** by multiple vendors (VirusTotal)  
- ✅ **Spoofed Domain:** `netwrksecurity.com` (not affiliated with MetaMask)  
- ✅ **Credential Harvesting:** Fake "verification" page mimics MetaMask  
- ✅ **Urgency Tactics:** Fake deadline (September 12, 2022) to pressure victims  

---

## **2. Email Preview**  
<p align="center">
  <img src="https://github.com/Iamfazi1/Portfolio/blob/main/Phishing%20Emails%20/Report%201/img/Screenshot_2025-04-28_04-24-31.png" alt="Email Screenshot" width="600">
</p>

---

## **3. Technical Analysis**  

### **Sender Details**  
- **From:** `Metamask_TeamSupport31612220446@netwrksecurity.com`  
- **Subject:** "Alerts" (generic to avoid spam filters)  
- **Reply-To:** None (prevents tracing)  

### **Malicious Link**  
- **URL:** `https://420.bio/NtRIA` (shortened to hide destination)  
<p align="center">
  <img src="https://github.com/Iamfazi1/Portfolio/blob/main/Phishing%20Emails%20/Report%201/img/Screenshot_2025-04-28_04-30-53.png" alt="VirusTotal Results" width="600">
</p>  
**VirusTotal Report:**  
- **Detection:** Flagged by multiple vendors as phishing  

### **Header Artifacts**  
- **IP:** `94.231.103.45` (Germany, Hetzner ISP - common for spam)  
- **Fake Authentication:** SPF/DKIM/DMARC spoofed for `netwrksecurity.com`  

---

## **4. Attack Workflow**  
1. **Bait:** Email threatens wallet termination to create urgency.  
2. **Hook:** Victims click `420.bio/NtRIA` or scan the QR code.  
3. **Steal:** Fake MetaMask page harvests credentials/seed phrases.  

---

## **5. Indicators of Compromise (IOCs)**  

| Type       | Value                          | Description                |  
|------------|--------------------------------|----------------------------|  
| **URL**    | `https://420.bio/NtRIA`        | Credential harvesting page |  
| **Domain** | `netwrksecurity.com`           | Spoofed sender domain      |  
| **IP**     | `94.231.103.45`                | Malicious server           |  

<p align="center">
  <em>Table 1: Confirmed IOCs</em>  
</p>

---

## **6. Recommendations**  
- **For Users:**  
  - Never click links in unsolicited emails.  
  - Verify MetaMask communications via official app only.  
- **For Organizations:**  
  - Block `420.bio` and `netwrksecurity.com` at firewall level.  
  - Train employees to identify urgency-based phishing.  

---

**Report Generated Using:**  
- **VirusTotal** (URL scanning)  
- **Email Header Analysis**  
- **WHOIS Lookup**  

<p align="center">
  <strong>Disclaimer:</strong> This report is for educational purposes only.  
</p>
