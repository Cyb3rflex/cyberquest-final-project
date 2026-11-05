# Linux File Permissions & Access Control: Practical Exercise & Task Guide

## Platform & Metadata

| Field | Details |
| :--- | :--- |
| **Platform** | [pwn.college](https://pwn.college/) |
| **Dojo / Module** | Linux Luminarium — Comprehending Permissions (`permissions`) |
| **Category** | Linux System Security & Access Control |
| **Difficulty** | Beginner |
| **Key Commands** | `ls -l`, `id`, `chmod`, `chown`, `chgrp`, `cat`, `find` |

> **Warning:** Complete all permission modification and privilege escalation tasks strictly within your authorized **pwn.college** container environment. Never modify file permissions or abuse `SUID` binaries on unauthorized systems.

---

## Objective

Master Linux Discretionary Access Control (`DAC`) by inspecting file ownership and permission bits (`rwx`), modifying permissions using both symbolic and octal modes with `chmod`, and leveraging the **Set Owner User ID (`SUID`)** special permission bit to read restricted files such as `/flag` in **pwn.college**.

---

## Prerequisites

- Completion of the [Linux Command-Line Fundamentals (`linux-commands.md`)](./linux-commands.md) exercise.
- An active session in the **pwn.college** `Comprehending Permissions` module.
- Basic familiarity with navigating directories and reading files (`ls`, `cd`, `cat`).

---

## Concept & Security Overview

### Authentication vs. Authorization in Linux
- **Authentication** verifies *who* you are on the system (for example, logging in as the `hacker` user, confirmed via `whoami` or `id`).
- **Authorization** determines *what* files, directories, and processes the authenticated `hacker` account is permitted to read, write, or execute. In Linux, standard file authorization is enforced through **ownership** and **permission bits**.

### Understanding `ls -l` Output and Permission Bits
Running `ls -l /flag` displays a 10-character file mode string followed by the owner and group:

```text
-rw-r----- 1 root hacker 58 Nov 05 10:00 /flag
```

| Segment | Value | Meaning |
| :--- | :--- | :--- |
| **File Type (`1st char`)** | `-` | Regular file (`d` = directory, `l` = symbolic link). |
| **User / Owner (`chars 2–4`)** | `rw-` | The file owner (`root`) has **Read (`r`)** and **Write (`w`)** permissions, but not Execute (`-`). |
| **Group (`chars 5–7`)** | `r--` | Members of the file's group (`hacker`) have **Read (`r`)** permission only. |
| **Others (`chars 8–10`)** | `---` | All other users on the system have **no permissions**. |

### Symbolic vs. Octal Permission Notation (`chmod`)
The `chmod` (*change mode*) command modifies file permissions using either **symbolic** or **octal (numeric)** notation:

| Permission | Symbol | Binary | Octal Value | Meaning for Files |
| :--- | :---: | :---: | :---: | :--- |
| **Read** | `r` | `100` | `4` | View the file's contents (e.g., with `cat`). |
| **Write** | `w` | `010` | `2` | Modify or overwrite the file's contents. |
| **Execute** | `x` | `001` | `1` | Run the file as a program or script. |
| **None** | `-` | `000` | `0` | No access permitted. |

- **Octal Example:** `chmod 644 file.txt` sets Owner to `4+2 = 6` (`rw-`), Group to `4` (`r--`), and Others to `4` (`r--`).
- **Symbolic Example:** `chmod u+r,g+r,o-rwx /flag` adds read access for User (`u`) and Group (`g`), and removes all permissions for Others (`o`).

### Special Permission: The `SUID` Bit (`s`)
Normally, when a user runs a program, the process runs with that user's own permissions (`hacker`). However, when the **Set Owner User ID (`SUID`)** bit is set on a binary owned by `root` (indicated by an `s` in the owner's execute slot, such as `-rwsr-xr-x` or octal `4755`), executing that binary causes it to run with the effective privileges of the file's owner (`root`).

---

## Student Tasks & Step-by-Step Instructions

Complete the following practical tasks in the **pwn.college** `Permissions` module and document your evidence in the placeholders below.

### Task 1: Inspect File Ownership and Permissions
1. Start the first level of the **Comprehending Permissions** module on **pwn.college**.
2. Check your current user ID and group memberships:
   ```bash
   id
   ```
3. Inspect the current ownership and permissions of the `/flag` file:
   ```bash
   ls -l /flag
   ```
4. Attempt to read `/flag` directly using `cat /flag` and observe why the system returns `Permission denied`.

### Task 2: Modify File Permissions with `chmod` (Changing Permissions Challenge)
In levels where the `hacker` user owns `/flag` (or is granted capability to modify its mode) but lacks read permissions (`---------- 1 hacker hacker /flag`):
1. Grant yourself read permission using either **symbolic** or **octal** mode:
   ```bash
   chmod u+r /flag
   ```
   *(Alternatively, in octal mode: `chmod 400 /flag` or `chmod 644 /flag`)*
2. Verify that the permission string updated to `-r--------` using `ls -l /flag`.
3. Read the flag:
   ```bash
   cat /flag
   ```

### Task 3: Execute a `SUID` Binary to Read `/flag` (SetUID Challenge)
In levels where `/flag` is owned by `root` (`-r-------- 1 root root /flag`) and a challenge program allows you to set the `SUID` bit on a binary (such as `/bin/cat`):
1. Inspect the permissions of `/challenge` and target utilities:
   ```bash
   ls -l /challenge
   ```
2. Apply the `SUID` bit (`u+s` or octal `4755`) as required by the level challenge:
   ```bash
   chmod u+s <target_binary>
   ```
3. Verify that the owner execute bit now displays `s` (`-rwsr-xr-x`):
   ```bash
   ls -l <target_binary>
   ```
4. Execute the `SUID` binary to read `/flag` with effective `root` privileges.

---

## Task Checklist

- [ ] Launch the **Comprehending Permissions** module on **pwn.college**.
- [ ] Run `id` and `ls -l /flag` to inspect user identity, group membership, and file mode bits.
- [ ] Complete the **`chmod`** permission modification challenge and capture the flag.
- [ ] Complete the **`SUID` (`u+s`)** permission challenge and capture the flag.
- [ ] Save verification screenshots into `./screenshots/` and embed them in the **Findings & Evidence** section below.

---

## Findings & Evidence

### Terminal Output

> **[TODO: Paste your actual terminal session output from pwn.college (`id`, `ls -l /flag`, `chmod`, and `cat /flag`) inside the code block below]**

```text
[TODO: Insert pwn.college terminal output here]
```

### Captured Flag(s)

> **[TODO: Replace the placeholder below with the actual `pwn.college{...}` flag(s) obtained from the lab]**

```text
[TODO: Insert captured pwn.college{...} flag here]
```

### Verification Screenshots

> **[TODO: Save your screenshot(s) in `03-Linux-Security/screenshots/` and update the image link below]**
>
> `![pwn.college Permissions Challenge Solution](./screenshots/<your-screenshot-filename>.png)`

---

## Remediation & Linux Hardening Takeaways

1. **Enforce the Principle of Least Privilege:** Sensitive configuration and credential files (such as `/etc/shadow` or SSH private keys `~/.ssh/id_ed25519`) must restrict read/write permissions exclusively to their owner (`chmod 600` or `chmod 640`) and never be world-readable (`o+r`) or world-writable (`o+w` / `chmod 777`).
2. **Audit and Remove Unnecessary `SUID` Binaries:** Misconfigured `SUID` binaries owned by `root` (such as `cat`, `vim`, `find`, `bash`, or `python3`) allow any local user to read arbitrary files or spawn a privileged `root` shell. System administrators should regularly audit the filesystem for `SUID` binaries using:
   ```bash
   find / -perm -4000 -type f 2>/dev/null
   ```
   and strip unnecessary `SUID` bits using `chmod u-s <binary_path>`.

---

## Learning Outcomes

- Distinguished between **authentication** (`id`, `whoami`) and **authorization** (Linux `rwx` permission bits for User, Group, and Others).
- Translated between symbolic (`u+rwx`, `g+rx`, `o-rwx`) and octal (`0600`, `0644`, `0755`, `4755`) permission modes.
- Demonstrated how the `SUID` bit (`u+s`) elevates effective process privileges and how to audit systems against `SUID` misconfigurations.

