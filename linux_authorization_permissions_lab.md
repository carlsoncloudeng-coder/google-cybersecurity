# Linux Authorization & Permissions Lab

**Google Cybersecurity Professional Certificate — Ungraded Activity**

---

## Overview

Practical exercise in Linux file and directory permission management to enforce proper authorization and protect sensitive data.

## Scenario

Audit and correct permissions in `/home/researcher2/projects` for the `researcher2` user (member of `research_team` group). Ensure files and directories align with least-privilege access principles.

---

## Initial State

```bash
ls -la /home/researcher2/projects
```

```
drwx--x---  researcher2 research_team  drafts
-rw-rw-rw-  researcher2 research_team  project_k.txt
-rw-r-----  researcher2 research_team  project_m.txt
-rw-rw-r--  researcher2 research_team  project_r.txt
-rw-rw-r--  researcher2 research_team  project_t.txt
-rw-rw-r--  researcher2 research_team  .project_x.txt  (hidden)
```

---

## Tasks & Commands

### Task 1 — Inspect Files and Hidden Files
```bash
cd /home/researcher2/projects
ls -la
```
- Identified group owner: `research_team`
- Identified hidden file: `.project_x.txt`

### Task 2 — Correct File Permissions
```bash
# Remove write permission for "other" on project_k.txt
chmod o-w project_k.txt

# Restrict project_m.txt: only user can read/write
chmod g-rw project_m.txt
```

### Task 3 — Secure Hidden File
```bash
# .project_x.txt is archived — remove write for user and group, keep read
chmod u-w,g-w .project_x.txt
```

### Task 4 — Lock Down Directory
```bash
# Remove group execute on drafts directory — only user may access
chmod g-x drafts
```

---

## Final State

| File/Directory | Permissions | Owner | Group | Notes |
|----------------|-------------|-------|-------|-------|
| `drafts/` | `drwx------` | researcher2 | research_team | User only |
| `project_k.txt` | `-rw-rw-r--` | researcher2 | research_team | Other write removed |
| `project_m.txt` | `-rw-------` | researcher2 | research_team | User only |
| `project_r.txt` | `-rw-rw-r--` | researcher2 | research_team | Unchanged |
| `project_t.txt` | `-rw-rw-r--` | researcher2 | research_team | Unchanged |
| `.project_x.txt` | `-r--r-----` | researcher2 | research_team | Read-only, archived |

---

## Skills Demonstrated

- Permission inspection (`ls -la`)
- Symbolic permission modification (`chmod`)
- Understanding of user / group / other ownership
- Hidden file handling
- Directory execute permission control
- Least-privilege access enforcement

---

*Completed as part of the Google Cybersecurity Professional Certificate curriculum.*
