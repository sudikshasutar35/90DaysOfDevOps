# Day 11 – File Ownership Challenge (chown & chgrp)

## Objective
Learn how to view and manage Linux file and directory ownership using `ls -l`, `chown`, `chgrp`, and recursive ownership changes.

## Task 1: Understanding Ownership

Commands used:
```bash
whoami
pwd
ls -l
ls -ld /root
```

Observations:
- Current user: `root`
- Current directory: `/root`
- The `ls -l` command displays file permissions, owner, group, size, date, and filename.
- The owner is the user who owns the file.
- The group represents the group associated with the file.

## Task 2: Basic chown Operations

Created `devops-file.txt` and changed its owner.

Commands:
```bash
touch devops-file.txt
useradd tokyo
chown tokyo devops-file.txt
useradd berlin
chown berlin devops-file.txt
ls -l devops-file.txt
```

Result:
- Initial owner: `root`
- First owner: `tokyo`
- Final owner: `berlin`
- Group: `root`

## Task 3: Basic chgrp Operations

Created `team-notes.txt` and changed its group.

Commands:
```bash
touch team-notes