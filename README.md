# Behavior-Analysis-of-live-Ransomware

# 🦠 Ransomware Analysis Lab (OSIRIS Variant)

## 📌 Overview
This project demonstrates the dynamic analysis of a ransomware sample executed in a controlled virtual lab environment. The objective was to observe malware behavior, including file encryption, system interaction and ransom note deployment.

---

## 🎯 Objectives
- Analyze ransomware behavior safely
- Identify file encryption patterns
- Detect registry and system activity
- Extract Indicators of Compromise (IOCs)

---

## 🖥️ Lab Environment
- OS: Windows 10 (Virtual Machine)
- Network: Isolated (No Internet)
- Tools Used:
  - Process Monitor (Procmon)
  - Regshot
  - Wireshark

## 🦠 Malware Behavior Observed

### 🔹 File Encryption
- Files were encrypted and renamed
- Extension changed to:

.OSIRIS

- File names replaced with unique IDs

---

### 🔹 Encryption Techniques
From ransom note analysis:
- AES-128 (File Encryption)
- RSA-2048 (Key Encryption)

---

### 🔹 Ransom Note
- Displayed on execution
- Instructions to install Tor Browser
- Payment required via onion (.onion) address
- Unique victim ID assigned

---

### 🔹 Process Activity
Observed using Procmon:
- High volume of:
- WriteFile
- RegOpenKey
- RegQueryValue

---

### 🔹 Registry Activity
- Access to system registry paths:

HKLM\SOFTWARE\Microsoft\WBEM

- Indicates system interaction and possible persistence attempts

---

## 🚨 Indicators of Compromise (IOCs)

### File Indicators:
- Extension: .OSIRIS
- Randomized filenames

### Behavioral Indicators:
- Rapid file modification
- File encryption activity
- Ransom note display

---

## 📸 Screenshots

### Ransom Note
![Ransom Note](screenshots/ransom_note.jpg)

### Encrypted Files
![Encrypted Files](screenshots/encrypted_files.jpg)

### Procmon Activity
![Procmon](screenshots/procmon.jpg)

---

## 🛡️ Mitigation Strategies
- Use Endpoint Detection & Response (EDR)
- Maintain regular backups
- Monitor file system activity
- Restrict unknown executables

---

## 📌 Conclusion
The ransomware sample demonstrated real-world attack techniques including file encryption, ransom demand, and system interaction. This project highlights the importance of proactive monitoring and cybersecurity defense strategies.

## ⚠️ Disclaimer
This project was conducted in a controlled lab environment for educational purposes only.
