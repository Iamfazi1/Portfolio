

# Faizan Email Analyzer

A powerful email analysis tool built to assist SOC analysts and incident responders in quickly identifying threats hidden in emails. This tool extracts key information, automates threat intelligence lookups, and offers user-friendly features to speed up phishing investigations.

---
## 🔥 Live Demo  
**Try it now:** [faizanshakir.space](https://www.faizanshakir.space)

---
<p align="center">
  <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExcWk0dGQ5c3V3NnJ1a2J0dXZtZ3R3dGJtYjV4eDZ6dWJ4b3R5a2N5eCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/l0HlNaQ6gWfllcjDO/giphy.gif" alt="Phishing Detection" />
</p>


## 🧠 Key Features

### ✅ Sender Information Extraction
- Automatically extracts the sender's name, email address, and IP address for quick attribution and triage.

### ✅ VirusTotal Hash Lookup
- Calculates the hashes of email attachments.
- Automatically checks these hashes against **VirusTotal** to detect known malware.

![VirusTotal Hash Check](https://github.com/Iamfazi1/faizan-email-analyzer/blob/main/img/Screenshot_2025-04-30_23-55-53.png)

### ✅ URL Extraction & Checking
- Detects all URLs embedded in the email.
- Offers automatic URL checking for malicious indicators.

![URL Checking](https://github.com/Iamfazi1/faizan-email-analyzer/blob/main/img/Screenshot_2025-04-30_23-56-37.png)

### ✅ Email Preview as Image
- Displays a clean, readable preview of the email.
- Lets users **download the email preview as a PNG** for reports or records.

![Email Preview](https://github.com/Iamfazi1/faizan-email-analyzer/blob/main/img/Screenshot_2025-04-30_23-57-10.png)

### ✅ Base64 Extraction and Decoding
- Automatically extracts base64 encoded content.
- Users can decode base64 with a single button click.

![Base64 Decoding](https://github.com/Iamfazi1/faizan-email-analyzer/blob/main/img/Screenshot_2025-04-30_23-57-42.png)

### ✅ Report Generation
- Users can **generate PDF or text reports** for documentation, case tracking, or sharing with teams.

![PDF and Text Report](https://github.com/Iamfazi1/faizan-email-analyzer/blob/main/img/Screenshot_2025-04-30_23-58-09.png)

---

## ⚙️ Technologies Used
- **Python** (Backend)
- **Flask** (Web Framework)
- **HTML/CSS/JS** (Frontend)
- **VirusTotal API** (Threat Intel)
- **Base64 & Email Libraries** (Parsing and decoding)

---

## 🚀 How to Run Locally
1. Clone the repo:
   ```bash
   git clone https://github.com/Iamfazi1/faizan-email-analyzer.git
   cd faizan-email-analyzer
   ```
2. Install requirements:
   ```bash
   pip install -r requirements.txt
   ```
3. Run the app:
   ```bash
   python app.py
   ```
4. Open in browser: `http://127.0.0.1:5000`

---

## 📄 License
This project is licensed under the MIT License.

---

## 🤝 Connect With Me
- **LinkedIn:** [Muhammad Faizan Shakir](https://www.linkedin.com/in/muhmmadfaizanshakir/)
- **GitHub:** [Iamfazi1](https://github.com/Iamfazi1)
- **TryHackMe:** [faizanshakir123](https://tryhackme.com/p/faizanshakir123)

---

Feel free to contribute, raise issues, or star the repo if you find it useful! ⭐
