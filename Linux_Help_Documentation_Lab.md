# Linux Help & Documentation Lab

> A hands-on Linux Bash shell lab demonstrating how to use built-in help commands — `whatis`, `man`, and `apropos` — to discover, understand, and differentiate Linux commands.

---

## Overview

As a security analyst, you won't always know every command or flag off the top of your head. Linux provides built-in documentation tools that let you find answers directly from the command line — without leaving the terminal or searching the web.

**Key Concepts:**
- **`whatis`** — get a one-line summary of a command
- **`man`** — display the full manual page for a command
- **`apropos`** — search manual pages by keyword to find relevant commands

---

## Scenario

You need to find information about Linux commands, discover their options, and identify the right command for a specific task — all using only the shell's built-in help resources.

---

## Lab Tasks

### Task 1: Learn More About Commands

#### 1a — Get a quick description of `cat`

```bash
whatis cat
```

**Output:**
```
cat (1)  - concatenate files and print on the standard output
```

**First two words of the description:** `concatenate files`

---

#### 1b — Explore `cat` options in detail

```bash
man cat
```

**Key finding:** To number the output lines of the `cat` command, use the `-n` (or `--number`) option.

```bash
cat -n file.txt
```

> **Navigation tip:** Press `ENTER` to scroll line by line, `SPACE` for the next page, and `Q` to quit the man page.

---

#### 1c — Find a command that returns the first part of a file

```bash
apropos -a first part file
```

**Result:** `head` — prints the first 10 lines of a file by default.

```bash
head file.txt
```

---

### Task 2: Explore the `useradd` Command

You need to set an expiration date for a temporary user account. Use the manual page to find the correct option.

```bash
man useradd
```

**Key finding:** The `-e` option sets the account expiration date.

```bash
sudo useradd -e 2026-12-31 tempuser
```

> **Navigation tip:** Press `Q` to exit the man page.

---

### Task 3: Explore `rm` vs. `rmdir`

Quickly remind yourself what each command does using `whatis`.

```bash
whatis rm
whatis rmdir
```

**Output:**
```
rm (1)     - remove files or directories
rmdir (1)  - remove empty directories
```

**Key difference:** `rmdir` removes **only empty directories**. `rm` removes files and can remove directories recursively with `-r`.

---

### Task 4: Determine Which Command to Use

You need to create a new group but can't remember the command. Search by keyword.

```bash
apropos "create new group"
```

**Result:** `groupadd` — creates a new group.

```bash
sudo groupadd newgroup
```

---

## Commands Reference

| Command | Purpose | Example |
|---------|---------|---------|
| `whatis <cmd>` | One-line summary of a command | `whatis cat` |
| `man <cmd>` | Full manual page with all options | `man useradd` |
| `apropos <keyword>` | Search manual pages by keyword | `apropos "create group"` |
| `apropos -a <kw1> <kw2>` | Match all supplied keywords | `apropos -a first part file` |

---

## Key Takeaways

- **`whatis`** is your fastest tool for a quick reminder of what a command does.
- **`man`** is the definitive reference — use it when you need to understand every option and flag.
- **`apropos`** is your discovery tool — use it when you know what you want to do but can't remember the command name.
- All three commands work offline and are available on virtually every Linux system.
- Man pages are navigated with `ENTER` (line), `SPACE` (page), and `Q` (quit).

---

## Skills Demonstrated

- Self-sufficient command-line research
- Reading and interpreting Linux manual pages
- Discovering commands by functional keywords
- Differentiating similar commands (`rm` vs. `rmdir`)
- Bash shell proficiency & documentation literacy

---

*Completed as part of Google Cybersecurity Certificate — Linux & Bash Fundamentals*
