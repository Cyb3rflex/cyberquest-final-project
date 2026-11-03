# CyberQuest Documentation & Markdown Governance Guide (`AGENTS.md`)

> **Mandatory Instruction:** This file serves as the central documentation governance and formatting guide for all Markdown (`.md`) files created, edited, updated, reviewed, or formatted within this repository. Always read and follow these rules before modifying or generating any documentation.

---

## 1. Project Context & Overview

**Project Name:** CodeVerse CyberQuest: Junior Cybersecurity Analyst Challenge

**Target Audience:** Beginner-level cybersecurity students who have completed introductory cybersecurity training, as well as instructors and evaluators reviewing capstone submissions.

**Project Purpose:**  
CyberQuest is a hands-on cybersecurity capstone project that bridges foundational theory and practical security analysis. Students complete practical exercises, document technical findings, capture verification screenshots, compile formal security assessment reports, build cybersecurity portfolios, and deliver group presentations across three core learning platforms:

1. **SkillBit** — Web application security (identifying, analyzing, and remediating web vulnerabilities).
2. **CryptoHack** — Cryptography fundamentals (encoding, decoding, cryptographic operations, and XOR analysis).
3. **pwn.college** — Linux fundamentals, command-line proficiency, file permissions, and practical system security exercises.

### Repository Directory Architecture

All documentation must align with the established repository layout and directory conventions:

| Path / Directory | Purpose & Expected Content |
| :--- | :--- |
| [`README.md`](README.md) | Root project overview, capstone objectives, repository map, and portfolio navigation. |
| [`01-web-security/`](01-web-security/) | **SkillBit** web application security write-ups (e.g., [`vulnerability-1.md`](01-web-security/vulnerability-1.md), [`vulnerability-2.md`](01-web-security/vulnerability-2.md)) and [`screenshots/`](01-web-security/screenshots/). |
| [`02-Cryptography/`](02-Cryptography/) | **CryptoHack** cryptography challenge documentation (e.g., [`encoding.md`](02-Cryptography/encoding.md), [`xor.md`](02-Cryptography/xor.md)) and [`screenshots/`](02-Cryptography/screenshots/). |
| [`03-Linux-Security/`](03-Linux-Security/) | **pwn.college** Linux security documentation (e.g., [`linux-commands.md`](03-Linux-Security/linux-commands.md), [`permissions.md`](03-Linux-Security/permissions.md)) and [`screenshots/`](03-Linux-Security/screenshots/). |
| [`04-Final-Report/`](04-Final-Report/) | Formal capstone technical assessment reports and deliverables (e.g., [`security-assessment-report.pdf`](04-Final-Report/security-assessment-report.pdf) and supporting Markdown drafts). |
| [`05-Reflection/`](05-Reflection/) | Student learning reflections, portfolio summaries, and group presentation notes. |

---

## 2. Markdown Formatting Standards

### Headings
- **Single H1 (`#`):** Use exactly one `#` heading at the very top of each document as the document title.
- **Major Sections (`##`):** Use `##` headings for primary structural sections.
- **Subsections (`###` and `####`):** Use `###` for subsections and `####` only when deeper granularity is necessary.
- **Logical Hierarchy:** Never skip heading levels (for example, do not jump from `#` directly to `###`).

### Writing Style & Tone
- **Clear & Beginner-Friendly:** Write in clear, professional, and accessible English suitable for junior cybersecurity analysts.
- **Define Technical Terms:** Avoid unnecessary jargon. When introducing a technical concept or security acronym (such as `SQLi`, `XSS`, `XOR`, `SUID`, or `chmod`) for the first time in a document, briefly explain its meaning.
- **Context-Appropriate Voice:**
  - **Student Assignments & Exercise Guides:** Use direct, actionable, imperative instructions (e.g., *"Inspect the HTTP request headers"*).
  - **Technical Reports & Assessments:** Use formal, objective, analytical language (e.g., *"The login endpoint failed to sanitize user-supplied input"*).
  - **Portfolio Reflections:** Use professional first-person analysis focused on methodology, challenges overcome, and skills acquired.
- **Conciseness:** Eliminate repetitive explanations, conversational fluff, and unnecessary filler text.

### Lists & Task Tracking
- **Numbered Lists (`1.`, `2.`, `3.`):** Use only for sequential steps, ordered workflows, or prioritized recommendations.
- **Bullet Points (`-`):** Use `-` consistently for unordered lists of related concepts, prerequisites, or observations.
- **Checkboxes (`- [ ]` / `- [x]`):** Use Markdown task lists for actionable checklists, student deliverables, and verification steps.
- **Consistent Indentation:** Maintain uniform indentation and spacing across nested list items.

### Code Blocks & Inline Code
- **Fenced Code Blocks:** Always use triple backticks (` ``` `) with an explicit language identifier (`bash`, `python`, `http`, `sql`, `html`, `javascript`, `json`, or `text`).
- **Inline Code:** Wrap terminal commands, flags, filenames, directory paths, URLs/endpoints under test, environment variables, permissions strings (e.g., `rwxr-xr-x`, `0644`), and technical identifiers in single backticks (`` ` ``).
- **Readability Rule:** Never embed multi-part terminal commands, scripts, or command outputs inside ordinary prose paragraphs when a fenced code block improves readability.

### Tables
- Use Markdown tables for grading rubrics, vulnerability summaries, command reference sheets, cryptographic comparisons, daily schedules, and structured metadata.
- Keep column text concise so tables remain readable in both raw Markdown and rendered views.
- Use alignment colons (`:---`, `:---:`, `---:`) consistently.

### Links & Screenshot References
- **Descriptive Link Text:** Always use meaningful link text instead of raw URLs (e.g., `[CryptoHack Encoding Challenges](https://cryptohack.org/)` rather than pasting a bare URL).
- **Relative Project Links:** Use clean relative paths when linking to other files or screenshots in this repository (e.g., `![XOR Challenge Solution](./screenshots/xor-solution.png)`).
- **Descriptive Alt Text:** Every embedded screenshot must include clear alt text describing what the evidence shows.

### Callouts & Emphasis
- **Bold (`**text**`):** Use for key terms, critical instructions, and metadata labels.
- **Blockquotes (`>`):** Use for important notices, hints, or contextual notes.
- **Safety & Warning Sections:** Use explicit blockquote warnings (`> **Warning:** ...`) for authorization boundaries and safety restrictions.
- **Restraint:** Do not overuse bold, italics, all-caps, or decorative symbols/emojis.

---

## 3. Document-Specific Structures

Always select the document structure that best matches the file's actual purpose. Do **not** force every document into an identical template.

### A. Project Briefs
Use when defining capstone requirements, module instructions, or assignment specifications:
1. **Project Title (`#`)**
2. **Overview** — Context and summary of the challenge.
3. **Objectives** — Primary goals of the assignment.
4. **Learning Outcomes** — Specific skills students will demonstrate.
5. **Requirements** — Tools, platform accounts (SkillBit, CryptoHack, pwn.college), and preparation needed.
6. **Tasks** — Step-by-step instructions or checklist (`- [ ]`) of required work.
7. **Deliverables** — Exact files, screenshots, and reports required.
8. **Submission Instructions** — Naming conventions, repository structure, and deadlines.
9. **Rules and Restrictions** — Ethical boundaries, scope limits, and academic integrity rules.

### B. Practical Exercise Guides & Challenge Write-Ups
Use for platform exercises and lab documentation in [`01-web-security/`](01-web-security/), [`02-Cryptography/`](02-Cryptography/), and [`03-Linux-Security/`](03-Linux-Security/):
1. **Exercise Title (`#`)**
2. **Platform & Metadata** — Platform (`SkillBit`, `CryptoHack`, or `pwn.college`), category, and difficulty level.
3. **Objective** — What the exercise or vulnerability assessment aims to achieve.
4. **Prerequisites** — Required background knowledge, tools, or environment setup.
5. **Concept / Vulnerability Overview** — Accurate technical explanation of the underlying mechanism or vulnerability.
6. **Instructions / Methodology** — Numbered, step-by-step walkthrough of the commands, scripts, or requests used.
7. **Expected Result / Findings** — Clear explanation of the outcome obtained.
8. **Evidence Requirements** — Embedded screenshots from the local `screenshots/` folder and relevant command/script output blocks.
9. **Remediation / Security Takeaway** *(especially for web & Linux security)* — How to fix the vulnerability or secure the system.
10. **Learning Outcomes** — Key lessons reinforced by completing the exercise.

### C. Technical Reports
Use for formal security assessments and capstone report drafts in [`04-Final-Report/`](04-Final-Report/):
1. **Title Page Information (`#`)** — Report title, author/team, date, target environment, and version.
2. **Executive Summary** — High-level, non-technical summary of assessment goals, key findings, overall risk, and core recommendations.
3. **Introduction** — Background and context of the CyberQuest assessment.
4. **Scope** — Authorized targets and platforms covered (`SkillBit`, `CryptoHack`, `pwn.college`) and out-of-scope boundaries.
5. **Methodology** — Standards, analytical workflow, and tools applied during testing.
6. **Findings** — Detailed breakdown of each identified issue or completed domain analysis.
7. **Evidence** — Verified technical proof, payloads, logs, and annotated screenshots.
8. **Impact** — Technical and operational consequences of the identified vulnerabilities.
9. **Recommendations** — Actionable, prioritized remediation controls.
10. **Conclusion** — Summary of overall security posture and final wrap-up.
11. **References** — Standards, documentation, and learning resources cited (e.g., OWASP, man pages, NIST).

### D. Daily Schedules & Study Plans
Use when organizing daily training agendas or sprint plans:
1. **Day and Topic (`#`)**
2. **Objective** — Focus goal for the session.
3. **Required Activities** — Readings, lectures, or setup tasks.
4. **Practical Exercises** — Specific `SkillBit`, `CryptoHack`, or `pwn.college` labs assigned.
5. **Deliverables** — Notes, commits, or screenshots due at the end of the session.
6. **Expected Outcome** — Skills or milestones achieved by completion.

### E. README Files
Use for the root [`README.md`](README.md) or subfolder overview files:
1. **Project Title (`#`)**
2. **Description** — Clear summary of the repository and the CyberQuest capstone.
3. **Purpose** — Why this project exists and what it demonstrates.
4. **Learning Objectives / Features** — Core competencies covered across Web Security, Cryptography, and Linux Security.
5. **Project Structure** — Directory tree or table mapping all folders and files.
6. **Requirements** — Platforms and tools used (`SkillBit`, `CryptoHack`, `pwn.college`, Python, Linux shell, etc.).
7. **Setup / Usage Instructions** *(where applicable)* — How to navigate the portfolio or run included helper scripts.
8. **Resources** — Links to official training platforms and references.
9. **Submission / Contribution Guidelines** *(where applicable)* — Standards for maintaining and submitting work.

### F. Reflections & Presentation Notes
Use for files in [`05-Reflection/`](05-Reflection/):
1. **Reflection Title (`#`)**
2. **Summary of Completed Work** — Overview of exercises completed across `SkillBit`, `CryptoHack`, and `pwn.college`.
3. **Key Technical Insights** — Most important concepts mastered across web security, cryptography, and Linux security.
4. **Challenges & Problem-Solving** — Obstacles encountered and how they were resolved.
5. **Areas for Future Growth** — Next steps in the student's cybersecurity learning journey.

---

## 4. Cybersecurity Documentation Standards

Because this project is a cybersecurity capstone, all documentation must adhere to strict technical accuracy, evidence integrity, and ethical safety rules:

### Technical Accuracy & Terminology
- **Authentication vs. Authorization:** Always distinguish between **authentication** (verifying *who* a user is, such as logging in with credentials) and **authorization** (verifying *what* an authenticated user is permitted to access or perform, such as role-based access control or file permissions).
- **Encoding vs. Encryption vs. Hashing:**
  - **Encoding** (e.g., ASCII, Hex, Base64, URL encoding) transforms data into another format for usability or transport using a publicly known scheme; it provides **no confidentiality** and uses no secret key.
  - **Encryption** (e.g., AES, RSA, XOR with a secret key) transforms plaintext into ciphertext using a cryptographic algorithm and a secret key to protect **confidentiality**; it is reversible only with the appropriate key.
  - **Hashing** (e.g., SHA-256, MD5) is a **one-way** mathematical function that maps data of arbitrary size to a fixed-length digest to verify **integrity**; it is not reversible.
- **Accurate Vulnerability Definitions:** Define web and system vulnerabilities accurately (e.g., distinguishing Reflected vs. Stored Cross-Site Scripting (`XSS`), SQL Injection (`SQLi`), Broken Access Control / `IDOR`, Command Injection, and insecure Linux file permissions or `SUID` misconfigurations).
- **Remediation Guidance:** Whenever documenting a security vulnerability or misconfiguration, include clear remediation steps (e.g., parameterized queries for `SQLi`, context-aware output encoding for `XSS`, principle of least privilege and `chmod`/`chown` hardening for Linux permissions).

### Evidence Integrity & Anti-Fabrication Rules
- **Separate Theory from Practice:** Clearly distinguish theoretical explanations of how a concept works from the practical evidence showing what was actually executed in the lab.
- **Zero Fabrication Policy:** **Never** invent, guess, or fabricate challenge completion results, captured flags (`flag{...}`, `crypto{...}`, `pwn.college{...}`), terminal outputs, HTTP responses, screenshot filenames, vulnerability findings, or test outcomes.
- **Handling Missing Evidence:** When drafting or formatting a document where practical results, flags, or screenshots have not yet been provided by the user, insert an explicit, clearly marked placeholder (e.g., `> **[TODO: Insert actual command output / screenshot from SkillBit lab here]**`) rather than inventing data.

### Safety, Scope & Credential Hygiene
- **Authorized Environments Only:** Ensure all practical instructions, payloads, and commands explicitly remain within authorized training environments (`SkillBit`, `CryptoHack`, and `pwn.college`).
- **No Live Secrets:** Never commit or include real personal passwords, production API keys, session cookies from real-world services, SSH private keys, or private credentials. Sanitize or redact sensitive session tokens if they belong to personal accounts.

---

## 5. Automatic Markdown Assistance Workflow

Whenever you are asked to create, edit, update, review, or format any `.md` file in this project, execute the following 10-step workflow automatically:

1. **Understand Audience & Purpose:** Identify whether the target file is a practical lab write-up, technical report, project brief, schedule, reflection, or `README.md`, and tailor the tone accordingly.
2. **Consult `AGENTS.md` First:** Review and apply the standards in this guide before making any edits.
3. **Inspect Before Editing:** Read the existing target file and check sibling files in the same folder (including `screenshots/`) to understand existing content and context.
4. **Preserve Accurate Information:** Retain all accurate technical details, student observations, commands, and findings already present in the file.
5. **Fix Formatting & Hierarchy:** Correct inconsistent heading levels (`#`, `##`, `###`), list markers, code block language tags, table alignments, and spacing.
6. **Improve Clarity Without Altering Meaning:** Refine rough notes, incomplete sentences, or unstructured text into clear, professional, beginner-friendly Markdown while strictly preserving the author's original meaning and factual results.
7. **Apply Accurate Security Terminology:** Ensure terms like authentication/authorization and encoding/encryption/hashing are used accurately.
8. **Add Necessary Structure Sensibly:** Add missing structural sections only when they genuinely improve the document's completeness for its specific type; do not bloat short notes with unnecessary boilerplate.
9. **Maintain Cross-Project Consistency:** Keep terminology, relative links, file naming references, and formatting consistent across `01-web-security/`, `02-Cryptography/`, `03-Linux-Security/`, `04-Final-Report/`, `05-Reflection/`, and `README.md`.
10. **Verify Final Output:** Check the finished Markdown for broken links, unclosed code fences, skipped heading levels, or accidentally fabricated details.

> **Autonomous Decision-Making:** Do not ask the user to specify heading levels, list formats, or standard section templates when they provide rough notes or ask for a document update. Make sensible, standards-compliant documentation decisions independently based on this guide.

---

## 6. Global Restrictions

- **No Unsolicited Bulk Rewrites:** Do not automatically rewrite or overwrite other Markdown files unless specifically instructed by the user for a given task.
- **Protect Source Code & Existing Assets:** Do not modify application source code, delete existing documentation, or reorganize the repository's folder structure unnecessarily.
- **No Unnecessary Files:** Do not create extra Markdown files, templates, or scratch documentation in the project workspace unless requested.
- **Strict Scope Alignment:** Keep all documentation strictly aligned with the **CodeVerse CyberQuest: Junior Cybersecurity Analyst Challenge** and its three core platforms (**SkillBit**, **CryptoHack**, and **pwn.college**). Do not introduce unrelated technologies, frameworks, or external platforms.

