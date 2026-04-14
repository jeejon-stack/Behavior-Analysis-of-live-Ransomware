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

---

## ⚠️ FIRST — Safety Rules (VERY IMPORTANT)

Before anything:

	    •	❌ NEVER run ransomware on your main PC
        •	❌ NO internet in the VM
    	•	✅ Use isolated/host-only network only
    	•	✅ Take a snapshot before execution
    	•	✅ Use fake test files only

## 🧪 STEP 1 — Create Your Safe Lab (VM Setup)


	1.	Create a Windows VM (Windows 10 preferred)
	2.	Allocate:
	      •	RAM: 2GB+
	      •	Storage: 30GB+

## STEP 1.1 — Disable Internet

Inside your VM settings:

	•	Set Network to:
	•	Host-only OR
	•	Internal Network

👉 This prevents ransomware from spreading or calling home.

## STEP 1.2 — Take Snapshot
	•	In VirtualBox/VMware:
	•	Click Snapshot → Take Snapshot
	•	Name it: Clean State

## 🛠️ STEP 2 — Install Your Tools

Inside the VM, install:

1. Process Monitor (Procmon)
	•	Tracks file + registry activity

2. Regshot
	•	Takes before/after registry snapshots

3. Wireshark
	•	Optional (since no internet, but useful)

## 📂 STEP 3 — Create Test Files (IMPORTANT)

Inside VM:
	1.	Create folder:

C:\Users\Public\Documents\TestFiles


	2.	Add files:
	•	test1.txt
	•	test2.docx
	•	test3.jpg

👉 These are what ransomware will encrypt.

##  STEP 4 — Get a SAFE Sample

Go to:
	•	Malware Traffic Analysis.net(you can download from 2016-12-23)

Download:
	•	Password-protected ZIP (usually password = infected_yearmonthday.. eg. infected_20161223)

⚠️ Extract ONLY inside VM.

## 🔍 STEP 5 — Start Monitoring

## 5.1 Start Regshot
	1.	Open Regshot
	2.	Click:
	•	1st Shot → Take Snapshot

## 5.2 Start Procmon
	1.	Open Procmon
	2.	Press:
	•	Ctrl + X (clear logs)
	•	Ctrl + E (start capture)

👉 Optional filter:
	•	Filter by process name (e.g. cmd.exe, malware name.exe)

## ▶️ STEP 6 — Execute the Malware
	1.	Run the ransomware sample
	2.	Watch:

In Procmon:
	•	File creation
	•	File renaming
	•	Registry edits

In Folder:
	•	Your test files will:
	•	Change extension (e.g. .wnry, .lockbit)
	•	Become unreadable

## 📊 STEP 7 — Capture Changes

## 7.1 Regshot After Execution

	•	Click:
	•	2nd Shot → Take Snapshot
	•	Compare

👉 You’ll see:
	•	Registry persistence keys like:

HKCU\Software\Microsoft\Windows\CurrentVersion\Run

## 7.2 Procmon Analysis

Look for:

🔹 First Process Spawned
	•	Parent → Child relationship

Example:

explorer.exe → malware.exe

🔹 File Encryption Behavior

Look for:
	•	CreateFile
	•	WriteFile
	•	SetRenameInformationFile

🔹 Extension Change

Example:
	•	.txt → .OSIRIS

## 🧾 STEP 8 — Find Ransom Note

Check:
	•	Desktop
	•	Documents
	•	Root folders

## Common names:
	•	README.txt
	•	HOW_TO_DECRYPT.txt
	•	@Please_Read_Me@.txt

## 🧠 STEP 9 — Identify Kill Switch

Example:
	•	OSIRIS checks a domain before running

👉 In Procmon or Wireshark:

	•	Look for:
	•	DNS requests
	•	Failed connections

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
