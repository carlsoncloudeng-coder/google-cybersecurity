# Linux File Permissions & Authorization Management

> **Project:** Manage Authorization in Linux  
> **Environment:** Bash Shell — `/home/researcher2/projects`  
> **Role:** Security Analyst | Research Team Support

---

## Table of Contents
- [Project Description](#project-description)
- [Check File and Directory Details](#check-file-and-directory-details)
- [Describe the Permissions String](#describe-the-permissions-string)
- [Change File Permissions](#change-file-permissions)
- [Change File Permissions on a Hidden File](#change-file-permissions-on-a-hidden-file)
- [Change Directory Permissions](#change-directory-permissions)
- [Summary](#summary)

---

## Project Description

As a security professional supporting a large organization's research team, I was responsible for auditing and managing file system authorization to protect sensitive research data. Using Linux Bash commands, I examined permissions in the `/home/researcher2/projects` directory, identified files and directories with excessive access rights, and applied the **principle of least privilege** to restrict unauthorized access. By adjusting permissions on standard files, a hidden archived file, and a restricted subdirectory, I ensured that only appropriately authorized users and groups could access critical system resources.

---

## Check File and Directory Details

### Command Used
```bash
cd /home/researcher2/projects
ls -la
```

### Output
```
drwx--x--- 2 researcher2 research_team 4096 Oct 14 18:40 drafts
-rw-rw-rw- 1 researcher2 research_team   46 Oct 14 18:40 project_k.txt
-rw-r----- 1 researcher2 research_team   46 Oct 14 18:40 project_m.txt
-rw-rw-r-- 1 researcher2 research_team   46 Oct 14 18:40 project_r.txt
-rw-rw-r-- 1 researcher2 research_team   46 Oct 14 18:40 project_t.txt
-rw-rw-r-- 1 researcher2 research_team   46 Oct 14 18:40 .project_x.txt
```

### Explanation
The `ls -la` command lists **all** files and directories (including hidden files via the `-a` flag) in **long format** (via the `-l` flag). This reveals the 10-character permission string, owner, group, file size, modification date, and filename for every item in the directory.

---

## Describe the Permissions String

### Example: `drwx--x---` (drafts directory)

| Position | Characters | Meaning |
|----------|-----------|---------|
| **1st** | `d` | **File type:** `d` indicates a **directory** (a hyphen `-` would indicate a regular file). |
| **2nd–4th** | `rwx` | **User** (`researcher2`) has **read**, **write**, and **execute** permissions. |
| **5th–7th** | `--x` | **Group** (`research_team`) has **execute** permission only, allowing members to access the directory but not list or modify its contents. |
| **8th–10th** | `---` | **Other** users have **no permissions** at all. |

### Key Takeaway
The 10-character string is the foundation of Linux discretionary access control (DAC). Each triplet (user, group, other) determines exactly who can read (`r`), write (`w`), or execute (`x`) a file or directory.

---

## Change File Permissions

### Issue Identified
The organization does **not** allow **other** users to have write access to any file. The file `project_k.txt` had permissions `-rw-rw-rw-`, which granted write access to others.

### Command Used
```bash
chmod o-w project_k.txt
```

### Verification
```bash
ls -la project_k.txt
```

### Result
```
-rw-rw-r-- 1 researcher2 research_team 46 Oct 14 18:40 project_k.txt
```

### Explanation
The `chmod o-w` command removes (`-`) the **write** (`w`) permission for **others** (`o`). The resulting permissions (`-rw-rw-r--`) ensure that only the user and group retain write access, while others can only read the file.

---

## Change File Permissions on a Hidden File

### Issue Identified
The file `.project_x.txt` is a **hidden**, archived file and should **not** be written to by anyone. The user and group must retain **read** access.

> **Note:** Hidden files in Linux begin with a period (`.`). The filename must always include this prefix when referencing it in commands.

### Command Used
```bash
chmod 440 .project_x.txt
```

### Verification
```bash
ls -la .project_x.txt
```

### Result
```
-r--r----- 1 researcher2 research_team 46 Oct 14 18:40 .project_x.txt
```

### Explanation
The numeric mode `440` translates to:
- **4** = read only for the **user**
- **4** = read only for the **group**
- **0** = no permissions for **others**

This ensures the archived file remains readable by authorized personnel but is protected from any modification.

---

## Change Directory Permissions

### Issue Identified
Only the `researcher2` user should be allowed to access the `drafts` directory and its contents. The directory initially had group execute permissions (`drwx--x---`), allowing group members to enter it.

### Command Used
```bash
chmod g-x drafts
```

### Verification
```bash
ls -la
```

### Result
```
drwx------ 2 researcher2 research_team 4096 Oct 14 18:40 drafts
```

### Explanation
The `chmod g-x` command removes (`-`) the **execute** (`x`) permission for the **group** (`g`). On a directory, execute permission controls whether users can access its contents. The final permissions (`drwx------`) ensure that **only** `researcher2` can access the directory; the group and all other users are completely blocked.

---

## Summary

In this activity, I audited Linux file system permissions to enforce proper authorization for a research team. By using `ls -la` to inspect files—including hidden files—interpreting 10-character permission strings, and applying precise `chmod` commands, I eliminated unauthorized write access on project files, secured an archived hidden file as read-only, and restricted a sensitive directory to a single user. These steps strengthened the system's security posture by ensuring that access was granted strictly according to organizational policy and the **principle of least privilege**.

---

## Commands Reference

| Command | Purpose |
|---------|---------|
| `ls -la` | List all files (including hidden) with detailed permissions |
| `chmod o-w <file>` | Remove write permission for others |
| `chmod 440 <file>` | Set read-only for user and group, none for others |
| `chmod g-x <directory>` | Remove execute permission for group |

---

## Skills Demonstrated
- Linux Bash shell navigation
- File and directory permission auditing
- `chmod` symbolic and numeric permission management
- Hidden file handling
- Principle of least privilege implementation
- Security-focused access control
