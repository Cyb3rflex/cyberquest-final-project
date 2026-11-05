# CodeVerse CyberQuest: Junior Cybersecurity Analyst Challenge (`cyberquest-final-project`)

> **Capstone Portfolio & Technical Security Assessment Repository**  
> **Author:** Cyberflex (Junior Cybersecurity Analyst)

---

## 1. Description

**CodeVerse CyberQuest: Junior Cybersecurity Analyst Challenge** is a comprehensive, hands-on cybersecurity capstone portfolio designed for junior analysts transitioning from foundational security theory to practical security analysis. This repository consolidates technical challenge write-ups, verification screenshots, custom Python cryptanalysis scripts, Linux system hardening exercises, and a formal technical security assessment report across three core training platforms:

1. **SkillBit** — Web Application Security & Vulnerability Exploitation.
2. **CryptoHack** — Applied Cryptography, Encoding/Decoding, and Symmetric `XOR` Cryptanalysis.
3. **pwn.college** — Linux Command-Line Fundamentals, File Permissions (`chmod`), and Privilege Escalation (`SUID`).

> **Warning & Ethical Scope Notice:** All vulnerability assessments, SQL injection payloads, cryptographic scripts, and Linux permission exercises documented in this repository were conducted strictly within authorized educational sandbox environments (**SkillBit**, **CryptoHack**, and **pwn.college**). Never execute offensive security techniques against systems without explicit written authorization.

---

## 2. Purpose

The purpose of this capstone project is to demonstrate end-to-end readiness as a **Junior Cybersecurity Analyst** by:

- **Identifying & Exploiting Vulnerabilities Safely:** Analyzing real-world security flaws—such as **SQL Injection (`SQLi`)**, cryptographic **key reuse (Two-Time Pad)**, and **insecure Linux file permissions**—within controlled training labs.
- **Maintaining Evidence Integrity:** Capturing reproducible terminal outputs, HTTP headers, database dumps, and annotated verification screenshots for every finding.
- **Translating Findings into Remediations:** Formulating actionable, standards-aligned engineering recommendations (such as parameterized SQL queries, salted password hashing, authenticated encryption with unique nonces, and least-privilege access controls).
- **Establishing Documentation Governance:** Following a standardized Markdown documentation methodology defined in [`AGENTS.md`](./AGENTS.md).

---

## 3. Learning Objectives & Core Competencies

### Domain 1: Web Application Security (`SkillBit`)
- Inspect HTTP response headers (`Apache`, `Debian`, `Caddy`, `PHP`) and HTML source code using browser Developer Tools (`F12`).
- Distinguish between **authentication** (verifying user identity) and **authorization** (verifying access permissions).
- Identify unsanitized SQL string concatenation and execute boolean tautology payloads (`' OR '1'='1' --`) to bypass authentication and extract database records.
- Recommend defense-in-depth remediations including **PDO Prepared Statements**, **password hashing (`Argon2id` / `bcrypt`)**, and suppression of verbose SQL debug output.

### Domain 2: Cryptography Fundamentals (`CryptoHack`)
- Distinguish clearly between **encoding** (`ASCII`, `Hexadecimal`), **encryption** (`XOR`, `AES`), and **hashing** (`SHA-256`, `bcrypt`).
- Decode 7-bit ASCII integer arrays and hexadecimal byte streams using Python (`chr()`, `ord()`, `bytes.fromhex()`).
- Perform a **known-plaintext attack (`KPA`)** against a repeating-key XOR cipher by leveraging predictable flag headers (`crypto{...}`) to recover the secret key (`myXORkey`).
- Exploit a **Two-Time Pad (Key Reuse)** vulnerability across two encrypted PNG images (`lemur.png` and `flag.png`) by performing pixel-level RGB channel XOR ($C_1 \oplus C_2 = I_{\text{lemur}} \oplus I_{\text{flag}}$) using Python's `Pillow` library.

### Domain 3: Linux System Security (`pwn.college`)
- Navigate the Linux command-line shell, interpret prompt metadata (`user@host:directory$`), and verify active user context (`whoami`, `id`, `ls`, `cd`).
- Analyze Linux Discretionary Access Control (`DAC`) mode strings (`-rw-r-----`) across **Owner (`u`)**, **Group (`g`)**, and **Others (`o`)**.
- Modify file permissions using both symbolic (`chmod u+r`) and octal (`chmod 0600`, `0644`) notation, and audit **Set Owner User ID (`SUID`, `chmod u+s`)** binaries to prevent unauthorized privilege escalation.

---

## 4. Portfolio Summary & Challenge Tracker

| ID | Platform | Domain | Challenge Name | Document Link | Status |
| :--- | :--- | :--- | :--- | :--- | :---: |
| **CQ-01** | **SkillBit** | Web Security | *Seriously Questionable Coding* (`SQLi` Auth Bypass) | [`01-web-security/vulnerability-1.md`](./01-web-security/vulnerability-1.md) | Completed |
| **CQ-02** | **CryptoHack** | Cryptography | *ASCII* (7-Bit Integer Encoding) | [`02-Cryptography/encoding.md`](./02-Cryptography/encoding.md) | Completed |
| **CQ-03** | **CryptoHack** | Cryptography | *You either know, XOR you don't* (Known-Plaintext XOR) | [`02-Cryptography/encoding.md`](./02-Cryptography/encoding.md) | Completed |
| **CQ-04** | **CryptoHack** | Cryptography | *Lemur XOR* (Visual RGB Two-Time Pad Attack) | [`02-Cryptography/xor.md`](./02-Cryptography/xor.md) | Completed |
| **CQ-05a** | **pwn.college** | Linux Security | *Intro to Commands* (`hello` / Shell Fundamentals) | [`03-Linux-Security/linux-commands.md`](./03-Linux-Security/linux-commands.md) | Completed |
| **CQ-05b** | **pwn.college** | Linux Security | *Comprehending Permissions* (`chmod` & `SUID` Task) | [`03-Linux-Security/permissions.md`](./03-Linux-Security/permissions.md) | Task Assigned |
| **Report** | **All Platforms** | Capstone Deliverable | *Comprehensive Technical Security Assessment Report* | [`04-Final-Report/security-assessment-report.md`](./04-Final-Report/security-assessment-report.md) | Completed |

---

## 5. Project Structure

```text
cyberquest-final-project/
├── AGENTS.md                                      # Global Markdown documentation & governance guide
├── README.md                                      # Project overview, portfolio map, and usage guide
├── 01-web-security/                               # SkillBit Web Application Security module
│   ├── vulnerability-1.md                         # SQL Injection authentication bypass write-up
│   ├── vulnerability-2.md                         # Secondary web vulnerability placeholder
│   └── screenshots/                               # Verification screenshots for SkillBit challenges
├── 02-Cryptography/                               # CryptoHack Cryptography module
│   ├── encoding.md                                # ASCII encoding & known-plaintext XOR write-up
│   ├── xor.md                                     # Visual RGB XOR (Lemur XOR) cryptanalysis write-up
│   └── screenshots/                               # Challenge images, recovered.png, and terminal proof
├── 03-Linux-Security/                             # pwn.college Linux Security module
│   ├── linux-commands.md                          # Linux command-line fundamentals write-up
│   ├── permissions.md                             # Linux file permissions (chmod/SUID) exercise & task guide
│   └── screenshots/                               # pwn.college terminal session screenshots
├── 04-Final-Report/                               # Capstone Technical Assessment Reports
│   ├── security-assessment-report.md              # Full Markdown security assessment report
│   └── security-assessment-report.pdf             # Final report deliverable
└── 05-Reflection/                                 # Student learning reflections & presentation notes
```

---

## 6. Requirements & Tools Used

### Training Platforms
- **[SkillBit](https://skillbit.io/)**: Web exploitation and authentication bypass lab environment.
- **[CryptoHack](https://cryptohack.org/)**: Interactive cryptography and cryptanalysis challenges.
- **[pwn.college](https://pwn.college/)**: Linux Luminarium dojo (`hello` and `permissions` modules).

### Local Analysis & Scripting Environment
- **Operating System:** Windows with **Ubuntu on WSL (Windows Subsystem for Linux)**.
- **Web Inspection:** Modern web browser with **Developer Tools (`F12`)** (`Network` and `Inspector` tabs).
- **Programming Language:** `Python 3.x` running inside an isolated virtual environment (`.venv`).
- **Python Libraries:** `Pillow` (`PIL`) for RGB pixel manipulation in visual XOR cryptanalysis.
- **Command-Line Utilities:** `bash`, `nano`, `whoami`, `id`, `ls`, `cd`, `chmod`, `chown`, `find`, `strings`, `grep`.

---

## 7. Setup & Usage Instructions

### Navigating the Portfolio
1. Start with the **[Comprehensive Technical Security Assessment Report (`04-Final-Report/security-assessment-report.md`)](./04-Final-Report/security-assessment-report.md)** for an executive summary, consolidated findings, risk ratings, and remediation controls across all challenges.
2. Browse the individual domain directories ([`01-web-security/`](./01-web-security/), [`02-Cryptography/`](./02-Cryptography/), and [`03-Linux-Security/`](./03-Linux-Security/)) for step-by-step methodologies, code snippets, and embedded screenshots.

### Reproducing the Cryptography Scripts Locally
To run the Python decryption scripts documented in [`02-Cryptography/encoding.md`](./02-Cryptography/encoding.md) and [`02-Cryptography/xor.md`](./02-Cryptography/xor.md):

1. Open a terminal in the project workspace and create a Python virtual environment:
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```
2. Install the `Pillow` image-processing library required for the visual XOR challenge:
   ```bash
   pip install pillow
   ```
3. Run the scripts inside [`02-Cryptography/`](./02-Cryptography/) to verify flag recovery from the challenge ciphertexts and PNG files.

---

## 8. Resources & References

- **[CryptoHack — Introduction to CryptoHack](https://cryptohack.org/challenges/introduction/)**: Official encoding and XOR cryptography exercises.
- **[pwn.college — Linux Luminarium](https://pwn.college/linux-luminarium/)**: Interactive Linux command-line and permissions curriculum.
- **[OWASP Top 10:2021](https://owasp.org/Top10/)**: Industry standard for web application security risks (`A03:2021 Injection` and `A07:2021 Identification and Authentication Failures`).
- **[OWASP SQL Injection Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/SQL_Injection_Prevention_Cheat_Sheet.html)**: Defensive coding standards for parameterized queries.
- **[NIST SP 800-63B Digital Identity Guidelines](https://pages.nist.gov/800-63-3/sp800-63b.html)**: Standards for authentication and salted password hashing.

---

## 9. Documentation Governance & Submission Guidelines

All documentation in this repository is governed by [`AGENTS.md`](./AGENTS.md):

- **Formatting Consistency:** Every Markdown file uses a single `#` title, logical `##`/`###` section hierarchy, language-tagged fenced code blocks, and relative screenshot links with descriptive alt text.
- **Evidence Integrity (Zero Fabrication Policy):** Practical findings, terminal transcripts, and flags (`MetaCTF{...}`, `crypto{...}`, `pwn.college{...}`) reflect verified lab outputs only. Uncompleted student tasks use explicit `[TODO]` placeholders until completed in the lab.
- **Credential Hygiene:** No personal passwords, live session tokens, or private SSH keys are stored in this repository.
