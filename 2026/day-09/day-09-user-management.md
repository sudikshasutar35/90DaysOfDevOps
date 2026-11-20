# Day 09 – Linux User & Group Management Challenge

## Users & Groups Created

### Users
- tokyo
- berlin
- professor
- nairobi

### Groups
- developers
- admins
- project-team

## Group Assignments

| User | Groups |
|---|---|
| tokyo | developers, project-team |
| berlin | developers, admins |
| professor | admins |
| nairobi | project-team |

## Directories Created

| Directory | Group Owner | Permissions |
|---|---|---|
| /opt/dev-project | developers | 775 (rwxrwxr-x) |
| /opt/team-workspace | project-team | 775 (rwxrwxr-x) |

## File Creation Testing

- Created `tokyo.txt` as tokyo.
- Created `berlin.txt` as berlin.
- Created `nairobi.txt` as nairobi.

## Commands Used

### User Management
- `useradd -m`
- `passwd`
- `usermod -aG`
- `cat /etc/passwd`
- `id`
- `groups`

### Group Management
- `groupadd`
- `cat /etc/group`

### Directory & Permissions
- `mkdir -p`
- `chgrp`
- `chmod 775`
- `ls -ld`
- `ls -l`
- `sudo -u`

## What I Learned

1. How to create Linux users and manage their passwords.
2. How to create groups and assign multiple users to supplementary groups.
3. How to configure shared directories using group ownership and Linux permissions.

## Practical Outcome

Successfully completed the Linux User & Group Management Challenge by creating users, managing groups, configuring shared directories, and testing file creation with different user accounts as part of the 90DaysOfDevOps challenge.