# Linux User Access Management Lab

> A hands-on Linux Bash shell lab demonstrating user authentication and authorization management using `useradd`, `usermod`, `userdel`, and `chown`.

---

## Overview

This lab covers the complete lifecycle of managing user access in a Linux environment — from onboarding a new employee to modifying their permissions and eventually offboarding them from the system.

**Key Concepts:**
- **Authentication** — verifying a user's identity
- **Authorization** — granting access to specific resources
- **User lifecycle management** — add, modify, and delete users
- **File ownership & group permissions**

---

## Scenario

A new employee, `researcher9`, joins the Research department. Over time, their role evolves — they take ownership of a project file, join a secondary department (Sales), and eventually leave the organization. Each stage requires updating their system access accordingly.

> **Environment:** Logged in as `analyst` with home directory `/home/analyst`.
> All user/group management commands require `sudo` (root privileges).

---

## Lab Tasks

### Task 1: Add a New User

Create a new user `researcher9` and set their primary group to `research_team`.

```bash
# Add the user to the system
sudo useradd researcher9

# Set primary group to research_team
sudo usermod -g research_team researcher9
```

**Verification:**
```bash
id researcher9
# Expected output: uid=... researcher9 gid=... research_team
```

---

### Task 2: Assign File Ownership

Transfer ownership of the project file `project_r.txt` from `researcher2` to `researcher9`.

```bash
sudo chown researcher9 /home/researcher2/projects/project_r.txt
```

**Verification:**
```bash
ls -l /home/researcher2/projects/project_r.txt
# Expected output: -rw-r--r-- 1 researcher9 ... project_r.txt
```

---

### Task 3: Add User to a Secondary Group

`researcher9` now works in both Research and Sales. Add them to `sales_team` as a supplementary group while keeping `research_team` as the primary group.

```bash
sudo usermod -a -G sales_team researcher9
```

> **Note:** `-a` (append) is lowercase and `-G` (supplementary group) is uppercase. Omitting `-a` would overwrite all existing secondary groups.

**Verification:**
```bash
groups researcher9
# Expected output: researcher9 : research_team sales_team
```

---

### Task 4: Delete a User

Offboard `researcher9` from the system and clean up the orphaned user group.

```bash
# Remove the user from the system
sudo userdel researcher9

# Clean up the empty user group (expected message: "Group researcher9 not removed because it is not the primary group")
sudo groupdel researcher9
```

**Verification:**
```bash
id researcher9
# Expected output: id: 'researcher9': no such user
```

---

## Commands Reference

| Command | Purpose | Key Flags |
|---------|---------|-----------|
| `useradd` | Create a new user | — |
| `usermod` | Modify an existing user | `-g` primary group, `-aG` append secondary group |
| `userdel` | Delete a user | — |
| `groupdel` | Delete a group | — |
| `chown` | Change file owner | `<user> <file>` |
| `id` | Display user identity info | — |
| `groups` | Display user's group memberships | — |

---

## Key Takeaways

- **Root privileges required:** All user/group management tasks need `sudo`.
- **Primary vs. Secondary groups:** A user has one primary group (`-g`) and can belong to multiple supplementary groups (`-aG`).
- **File ownership (`chown`):** Critical for enforcing least-privilege access to project resources.
- **Cleanup discipline:** After deleting a user, always remove orphaned groups with `groupdel`.
- **Case-sensitive flags:** `-a` vs. `-A` and `-g` vs. `-G` behave very differently.

---

## Skills Demonstrated

- Linux user lifecycle management
- Group-based access control
- File permission & ownership management
- Security best practices (least privilege, cleanup)
- Bash shell proficiency

---

*Completed as part of Google Cybersecurity Certificate — Linux & Bash Fundamentals*
