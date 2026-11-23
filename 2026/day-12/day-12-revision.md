# Day 12 – Revision & Consolidation (Days 01–11)

## Objective
Review and consolidate Linux fundamentals, process management, file operations, permissions, users, groups, and ownership learned during Days 01–11.

## Task 1: Mindset & Learning Plan Review

Revisited my Day 01 – 90 Days of DevOps & Cloud Engineering Learning Plan.

### My 3 Main Goals
1. Linux & Automation – Learn Linux administration, Bash scripting, and troubleshooting.
2. Cloud & DevOps Tools – Learn AWS, Git, GitHub, Docker, CI/CD, and Terraform.
3. Real-World Project – Build and deploy a cloud application using DevOps practices.

### Revision Observations
- Practiced Linux commands through hands-on activities.
- Improved understanding of file permissions and ownership.
- Practiced process and service monitoring.
- Need to continue improving automation, Docker, CI/CD, and Terraform skills.

## Task 2: Process & Service Management

### Commands Practiced

**1. Check running processes**
```bash
ps aux
```
Observation: Displayed running processes with user, PID, CPU, memory, and command information.

**2. Check SSH service status**
```bash
systemctl status ssh
```
Observation:
- SSH service status: Active (running)
- Main PID: 1316
- SSH server listening on port 22.

### Key Learning
Learned how to inspect running processes and verify whether a Linux service is active.

## Task 3: File Operations & Permissions

### Commands Practiced

**1. Create directory**
```bash
mkdir -p /tmp/day12-revision
```

**2. Create a file and write content**
```bash
echo "day 12 linux operation practise" > notes.txt
```

**3. Append content**
```bash
echo "Practiced append operation" >> notes.txt
```

**4. Read file**
```bash
cat notes.txt
```

**5. Create backup**
```bash
cp notes.txt backup.txt
```

**6. Change file permissions**
```bash
chmod 640 notes.txt
```

**7. Verify permissions**
```bash
ls -l notes.txt
```

Expected permission:
```text
-rw-r-----
```

### Key Learning
Practiced creating files, appending content, copying files, and modifying file permissions.

## Task 4: Linux First-Response Cheat Sheet

Revised five important commands from the Day 03 Linux command practice.

| Command | Purpose |
|---|---|
| `ps aux` | Check running processes |
| `top` | Monitor CPU and memory usage |
| `df -h` | Check disk space |
| `free -h` | Check available memory |
| `ip addr` | Check network interfaces and IP addresses |

### Key Learning
These commands help in identifying common system and resource issues during troubleshooting.

## Task 5: User & Ownership Practice

### Commands Practiced

**1. Check whether user exists**
```bash
id day12user
```
Observation: User did not exist initially.

**2. Create a new user**
```bash
useradd -m day12user
```

**3. Verify user details**
```bash
id day12user
```
Output:
```text
uid=1001(day12user) gid=1001(day12user) groups=1001(day12user)
```

**4. Change file ownership**
```bash
chown day12user:day12user notes.txt
```

**5. Verify ownership**
```bash
ls -l notes.txt
```

Output:
```text
-rw-r----- 1 day12user day12user 59 notes.txt
```

### Key Learning
Learned how to create a Linux user, verify UID and GID, and change file ownership safely on a test file.

## Mini Self-Check

### 1. Which 3 commands save the most time and why?

- `ps aux` – Quickly identifies running processes.
- `df -h` – Helps identify disk space problems.
- `systemctl status ssh` – Helps verify service health.

### 2. How do you check whether a service is healthy?

```bash
systemctl status ssh
ps aux
journalctl -u ssh -n 10 --no-pager
```

### 3. How do you safely change ownership and permissions without breaking access?

Use `chown` and `chmod` carefully on the required file only.

Example:
```bash
chown day12user:day12user notes.txt
chmod 640 notes.txt
```

### 4. What will you improve in the next 3 days?

- Practice more Linux troubleshooting commands.
- Improve understanding of processes and services.
- Continue learning Linux administration and DevOps fundamentals.

## Day 12 Conclusion

Completed revision and hands-on practice covering Linux processes, services, file operations, permissions, user management, and ownership.

**Consistency over perfection – Learn, Practise, Build, Improve.**

#90DaysOfDevOps #DevOpsKaJosh #TrainWithShubham