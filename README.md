# Networkwalks Cybersecurity Internship – Week 3 Password Cracking & Hash Security Auditing

A comprehensive documentation repository covering offline CLI password cracking with **John the Ripper (JTR)** (**W3-PM1**) and browser-based hash auditing via **Networkwalks Web Tools** (**W3-PM2**) executed as part of the **Networkwalks Cybersecurity Internship Program**.

---

## 👤 Internship & Author Details

- **Intern Name:** [Azeez Umar Opeyemi](https://www.linkedin.com/in/azeez-umar-opeyemi-201a433a4/) 
- **Intern ID:** NW-83-ODU
- **Instructor / Mentor:** [Waqas Karim (CCIE)](https://www.linkedin.com/in/waqaskarim/)
- **Domain:** Cybersecurity & Penetration Testing
- **Organization:** Networkwalks Technologies
- **Internship Period:** September 6, 2026 – October 3, 2026

---

## 📌 Repository Overview

This repository documents the practical execution of Week 3 modules focusing on **Password Hash Extraction, Offline Dictionary Attacks, and Flag Capture**. The objective is to evaluate encrypted document security, compare command-line auditing tools with web-based cracking interfaces, and capture hidden flags.

```text
├── 🔑 Module 1 (W3-PM1): Password Cracking with John the Ripper (JTR CLI)
└── 🌐 Module 2 (W3-PM2): Password Cracking with Networkwalks Web Tools
```

---

## 🛠️ Prerequisites & Tools Summary

| Tool / Platform | Environment | Usage / Purpose |
| :--- | :--- | :--- |
| **John the Ripper (JTR)** | Kali Linux CLI | Multi-threaded offline hash cracking and dictionary attacks. |
| **`rockyou.txt`** | Kali Linux Wordlists | Standard wordlist used for password dictionary matching. |
| **Online HashCrack** | Web Browser | Online `pdf2john` hash extraction utility for PDF files. |
| **Networkwalks Hash Calculator** | Web Portal | Client-side `$pdf$` hash generator (`networkwalks.com/hash_calculator/`). |
| **Networkwalks Password Cracker** | Web Portal | Web-based real-time dictionary attack tool (`networkwalks.com/password_cracker/`). |

---

## 🔑 Module 1: Password Cracking with John the Ripper (W3-PM1)

* **Objective:** Extract hash signatures from password-protected PDF files, execute dictionary attacks using `john` and `rockyou.txt`, unlock documents, and recover embedded flags.

### Technical Steps Executed

1. **Hash Extraction:** Extracted `$pdf$` hashes from locked PDF documents (`My_Locked_PDF1.pdf`, `My_Locked_PDF2.pdf`, `My_Locked_PDF3.pdf`) into text hash files (`hash1.txt`, `hash2.txt`, `hash3.txt`).
2. **CLI Dictionary Attack Execution:**
   ```bash
   sudo john --wordlist=/usr/share/wordlists/rockyou.txt hash1.txt
   sudo john --wordlist=/usr/share/wordlists/rockyou.txt hash2.txt
   sudo john --wordlist=/usr/share/wordlists/rockyou.txt hash3.txt
   ```

---

## 🌐 Module 2: Password Cracking with Networkwalks Web Tools (W3-PM2)

* **Objective:** Perform end-to-end web-based password cracking using Networkwalks' custom client-side tools (`networkwalks.com/password_cracker/`).

### Technical Steps Executed

1. **Web Hash Calculation:** Uploaded encrypted PDF files directly to the **Networkwalks Hash Calculator** to generate crackable `$pdf$` hash strings.
2. **Browser-Based Dictionary Attack:** Pasted extracted hashes into the **Password Cracker** interface, ran real-time wordlist matching, unlocked PDF documents, and retrieved embedded flags.

---

## 📊 Summary of Results & Flag Capture Inventory

| Target Document | Module 1 (JTR CLI) | Module 2 (NW Web Tool) | Recovered Plaintext Password | Captured Flag |
| :--- | :--- | :--- | :--- | :--- |
| **`My_Locked_PDF1.pdf`** | Cracked (`hash1.txt`) | Cracked (`Hash Cracker`) | `good-luck` | `nw{cybersecurity_flag_captured_2608}` |
| **`My_Locked_PDF2.pdf`** | Cracked (`hash2.txt`) | Cracked (`Hash Cracker`) | `password1` | `nw{networkwalks_persistence_jtr_270521}` |
| **`My_Locked_PDF3.pdf`** | Cracked (`hash3.txt`) | Cracked (`Hash Cracker`) | `1qaz2wsx` | `nw{networkwalks_flag_260321_1}` |

---

## ⚡ Technical Comparison: JTR CLI vs. Networkwalks Web Tool

| Feature / Aspect | John the Ripper (JTR CLI) | Networkwalks Web Cracker Tool |
| :--- | :--- | :--- |
| **User Interface** | Linux Terminal (Command Line) | Interactive Web Dashboard |
| **Hash Extraction** | `pdf2john.pl` / `pdf2john.py` | Browser Web Crypto API |
| **Execution Engine** | Native OpenMP CPU Multi-threading | JavaScript / Web Worker Threads |
| **Workflow Complexity** | Manual terminal syntax required | Drag-and-drop interactive GUI |

---

## 📁 Repository Structure

```text
.
├── My_Locked_PDF/
│   ├── My_Locked_PDF1.pdf
│   ├── My_Locked_PDF2.pdf
│   └── My_Locked_PDF3.pdf
├── PM1_JTR_CLI/
│   ├── hash1.txt
│   ├── hash2.txt
│   ├── hash3.txt
│   ├── jtr_terminal_crack1.png
│   ├── jtr_terminal_crack2.png
│   └── jtr_terminal_crack3.png
├── PM2_NW_Web_Tools/
│   ├── nw_hash_calculator.png
│   ├── nw_password_cracker1.png
│   ├── nw_password_cracker2.png
│   └── nw_password_cracker3.png
└── README.md
```

---

## 💡 Key Security Insights & Recommendations

1. **Password Entropy & Complexity:** Simple dictionary terms (`good-luck`), common defaults (`password1`), and keyboard patterns (`1qaz2wsx`) offer zero resistance against dictionary attacks.
2. **Modern Password Hashing:** Systems must implement slow, memory-hard key derivation functions like **Argon2**, **bcrypt**, or **PBKDF2** with high work factors to prevent rapid offline cracking.
3. **Encrypted Document Policies:** Organization-wide policies should enforce passphrases of 14+ characters combining mixed casing, numbers, and symbols for protected files.
