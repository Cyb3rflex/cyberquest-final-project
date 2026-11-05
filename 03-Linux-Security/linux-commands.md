# Linux Command-Line Fundamentals: Invoking Commands (`Intro to Commands`)

## Platform & Metadata

| Field | Details |
| :--- | :--- |
| **Platform** | [pwn.college](https://pwn.college/) |
| **Dojo / Module** | Linux Luminarium — `hello` (`intro-to-commands`) |
| **Category** | Linux Fundamentals & Command-Line Proficiency |
| **Difficulty** | Beginner |
| **Environment** | `hacker@hello~intro-to-commands` (pwn.college Workspace Terminal) |

> **Warning:** All commands and exercises documented in this write-up were performed strictly within the authorized **pwn.college** container environment.

---

## Objective

Understand how the Linux command-line shell (Bash) interprets and executes user commands, inspect the current user identity and directory contents using foundational commands (`whoami`, `ls`, `cd`), and invoke the target `hello` binary to retrieve the challenge flag.

---

## Prerequisites

- An active account on [pwn.college](https://pwn.college/).
- Access to the **pwn.college** web workspace or SSH terminal session.
- Basic familiarity with keyboard input in a terminal emulator.

---

## Concept Overview

### The Linux Shell & Prompt Structure
When interacting with a Linux system through a terminal, a **shell** (such as `bash`) reads the command typed by the user, executes the corresponding program, displays its output, and returns a prompt when the command finishes:

```text
hacker@hello~intro-to-commands:~$
```

- `hacker` — The currently **authenticated** username.
- `hello~intro-to-commands` — The hostname of the active pwn.college challenge container.
- `~` — The current working directory (`~` represents the user's home directory, `/home/hacker`).
- `$` — Indicates a standard (non-root) user session (whereas `#` indicates an administrative `root` shell).

### Case Sensitivity in Linux
Linux filesystems, commands, and arguments are strictly **case-sensitive**. Invoking `hello` executes a completely different command name than `HELLO` or `Hello`.

### Core Commands Used

| Command | Purpose |
| :--- | :--- |
| `whoami` | Prints the effective username of the current user (`hacker`). |
| `ls` | Lists files and subdirectories inside the current working directory. |
| `cd <directory>` | Changes the current working directory to `<directory>`. |
| `hello` | Challenge-specific executable in the system `PATH` that outputs the level flag. |

---

## Methodology & Step-by-Step Walkthrough

1. Launch the **Intro to Commands** challenge instance on **pwn.college** and open the terminal session.
2. Verify the current logged-in user identity by running `whoami`:

   ```bash
   whoami
   ```

   The shell outputs `hacker` and returns to the command prompt.

3. List the contents of the home directory (`~`) and navigate into the `Desktop` directory to explore the workspace:

   ```bash
   ls
   cd Desktop
   ls
   ```

4. Invoke the lowercase `hello` command as instructed by the challenge prompt:

   ```bash
   hello
   ```

---

## Findings & Evidence

### Terminal Session Output

```text
hacker@hello~intro-to-commands:~$ whoami
hacker
hacker@hello~intro-to-commands:~$ ls
Desktop
hacker@hello~intro-to-commands:~$ cd Desktop
hacker@hello~intro-to-commands:~/Desktop$ ls
hacker@hello~intro-to-commands:~/Desktop$ hello
Success! Here is your flag:
pwn.college{EnJ5mlqSTCVctJQNPa9imumcTKl.QX3YjM1wCM3IzN0IzW}
```

### Captured Flag

```text
pwn.college{EnJ5mlqSTCVctJQNPa9imumcTKl.QX3YjM1wCM3IzN0IzW}
```

### Verification Screenshot

![pwn.college Terminal Output for Intro to Commands Challenge](./screenshots/Screenshot%202026-11-05%20095759.png)

---

## Security Takeaways

1. **Verifying User Context (`whoami`):** In security assessments and incident response, checking the active user account (`whoami` and `id`) is always the first step to determine what privilege level the session currently holds.
2. **How the Shell Locates Executables (`PATH`):** Because `hello` was invoked without a file path (such as `./hello`) even after changing directories to `~/Desktop`, the shell located the executable using the `PATH` environment variable. Understanding `PATH` resolution is essential for preventing privilege escalation attacks such as **PATH Hijacking**.

---

## Learning Outcomes

- Interpreted the components of the Linux shell prompt (`user@host:directory$`).
- Executed foundational reconnaissance and navigation commands (`whoami`, `ls`, `cd`).
- Demonstrated awareness of Linux case sensitivity when invoking system binaries.
