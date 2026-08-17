# Linux File Permissions Management

> **Portfolio Project**  
> **Category:** Linux | System Administration | Access Control | Cybersecurity  
> **Skills Demonstrated:** Linux, File Permissions, Access Control, Least Privilege, `chmod`, `ls`, Hidden Files

---

## Project Description

As a security professional supporting a research team, I was responsible for reviewing and updating Linux file permissions to ensure that only authorized users could access project resources. The objective was to verify existing permissions, identify unauthorized access, and modify file and directory permissions using Linux commands while following the organization's security policy.

---

# Checking File and Directory Permissions

## Command Used

```bash
ls -la
```

## Explanation

The `ls -la` command displays all files and directories, including hidden files, along with detailed information such as permissions, ownership, file size, and modification timestamps.

| Option | Description |
|---------|-------------|
| `ls` | Lists directory contents |
| `-l` | Displays information in long format |
| `-a` | Includes hidden files and directories |

### Example Output

```text
drwxr-xr-x 2 researcher2 research_team 4096 Apr 10 09:30 drafts
-rw-rw-r-- 1 researcher2 research_team 1024 Apr 10 09:28 project_k.txt
-rw-r----- 1 researcher2 research_team 2048 Apr 10 09:25 project_m.txt
-rw-rw-r-- 1 researcher2 research_team 1536 Apr 10 09:27 project_r.txt
-rw-rw-r-- 1 researcher2 research_team 1800 Apr 10 09:29 .project_x.txt
```

---

# Current Permissions

| File / Directory | Permissions |
|------------------|-------------|
| `drafts` | `drwxr-xr-x` |
| `project_k.txt` | `-rw-rw-r--` |
| `project_m.txt` | `-rw-r-----` |
| `project_r.txt` | `-rw-rw-r--` |
| `.project_x.txt` | `-rw-rw-r--` |

---

# Understanding the Linux Permission String

Example permission string:

```text
-rw-rw-r--
```

### Permission Breakdown

| Characters | Meaning |
|------------|---------|
| `-` | Regular file |
| `rw-` | Owner: Read + Write |
| `rw-` | Group: Read + Write |
| `r--` | Others: Read only |

### Explanation

Linux represents permissions using a 10-character string.

The **first character** identifies the object type:

- `-` = Regular file
- `d` = Directory

The remaining **nine characters** are divided into three permission groups:

1. Owner
2. Group
3. Others

Each group contains three permission bits:

| Symbol | Permission |
|--------|------------|
| `r` | Read |
| `w` | Write |
| `x` | Execute |
| `-` | Permission not granted |

---

# Updating File Permissions

## Scenario

The organization's security policy states that users classified as **others** must never have write permission on project files.

## Command

```bash
chmod o-w project_k.txt
```

## Explanation

The `chmod` command changes file permissions.

Permission breakdown:

- `o` = Others
- `-` = Remove permission
- `w` = Write permission

This command removes write access from users outside the owner and group while preserving all other permissions.

### Result

**Before**

```text
-rw-rw-r--
```

**After**

```text
-rw-rw-r--
```

In this case, no changes were necessary because the file already complied with the organization's security policy.

---

# Updating Permissions on a Hidden File

## Scenario

The archived file `.project_x.txt` is a hidden file and should have the following permissions:

- Owner: Read and Write
- Group: Read only
- Others: No access

## Command

```bash
chmod u=rw,g=r,o= .project_x.txt
```

## Explanation

This command explicitly assigns permissions for each user category.

| Option | Meaning |
|--------|---------|
| `u=rw` | Owner can read and write |
| `g=r` | Group can read only |
| `o=` | Others receive no permissions |

Files beginning with a period (`.`) are considered **hidden files** in Linux and are only displayed when using commands such as `ls -a` or `ls -la`.

### Result

**Before**

```text
-rw-rw-r--
```

**After**

```text
-rw-r-----
```

---

# Restricting Directory Access

## Scenario

Only the file owner (`researcher2`) should have access to the `drafts` directory and everything contained within it.

## Command

```bash
chmod 700 drafts
```

## Explanation

The numeric permission `700` grants:

| Value | Permissions |
|-------|-------------|
| **7** | Read, Write, Execute (Owner) |
| **0** | No permissions (Group) |
| **0** | No permissions (Others) |

Directories require the **execute (`x`) permission** to allow users to enter or traverse the directory. Removing permissions from both the group and others ensures that only the owner can access the directory and its contents.

### Result

**Before**

```text
drwxr-xr-x
```

**After**

```text
drwx------
```

---

# Linux Commands Summary

| Command | Purpose |
|----------|---------|
| `ls -la` | Display detailed information for all files, including hidden files |
| `chmod o-w project_k.txt` | Remove write permission from others |
| `chmod u=rw,g=r,o= .project_x.txt` | Configure permissions for the hidden archived file |
| `chmod 700 drafts` | Restrict directory access to the owner only |

---

# Key Concepts Demonstrated

- Viewing Linux file permissions
- Understanding the Linux permission string
- Managing user, group, and others permissions
- Working with hidden files
- Applying the Principle of Least Privilege
- Securing directories using numeric permissions
- Using `chmod` to modify access control
- Using `ls -la` to inspect file metadata

---

# Skills Demonstrated

- Linux System Administration
- File Permission Management
- Access Control
- Principle of Least Privilege
- Command Line Operations
- Security Hardening
- Cybersecurity Fundamentals

---

# Summary

In this project, I examined Linux file and directory permissions using the `ls -la` command, interpreted Linux permission strings, and modified permissions using `chmod` to comply with organizational security policies. I updated permissions for standard files, hidden files, and restricted directories to ensure only authorized users retained access. This exercise demonstrates practical Linux administration skills and reinforces core cybersecurity concepts such as access control and the Principle of Least Privilege.
