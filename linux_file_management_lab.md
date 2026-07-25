# Linux File Management Lab

**Google Cybersecurity Professional Certificate — Ungraded Activity**

---

## Overview

Practical exercise in Linux Bash shell commands for directory and file management within the `/home/analyst` environment.

## Scenario

Reorganize the `/home/analyst` directory structure to support cleaner data management for security operations.

### Initial Structure
```
/home/analyst/
├── notes/
│   ├── Q3patches.txt
│   └── tempnotes.txt
├── reports/
│   ├── Q1patches.txt
│   └── Q2patches.txt
└── temp/
```

### Target Structure
```
/home/analyst/
├── logs/
├── notes/
│   └── tasks.txt
└── reports/
    ├── Q1patches.txt
    ├── Q2patches.txt
    └── Q3patches.txt
```

---

## Commands Executed

| Task | Command | Purpose |
|------|---------|---------|
| Create directory | `mkdir /home/analyst/logs` | Create `logs` subdirectory |
| Remove directory | `rm -r /home/analyst/temp` | Delete unused `temp` directory |
| Move file | `mv /home/analyst/notes/Q3patches.txt /home/analyst/reports/` | Relocate Q3 report to `reports` |
| Remove file | `rm /home/analyst/notes/tempnotes.txt` | Delete obsolete notes file |
| Create file | `touch /home/analyst/notes/tasks.txt` | Create documentation file |
| Edit file | `nano /home/analyst/notes/tasks.txt` | Add completion notes via nano |
| Verify | `cat /home/analyst/notes/tasks.txt` | Confirm file contents |

---

## File Content

**`tasks.txt`**
```
  Completed tasks
  1. Managed file structure in /home/analyst
```

---

## Skills Demonstrated

- Directory creation and deletion (`mkdir`, `rm -r`)
- File operations (`mv`, `rm`, `touch`)
- Text editing with `nano`
- File content verification (`cat`, `ls`)
- Bash shell navigation and command execution

---

*Completed as part of the Google Cybersecurity Professional Certificate curriculum.*
