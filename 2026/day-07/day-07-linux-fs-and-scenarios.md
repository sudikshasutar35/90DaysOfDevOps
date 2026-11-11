# Day 07 – Linux File System Hierarchy & Scenario-Based Practice

## Objective

Understand the Linux File System Hierarchy and practice basic real-world troubleshooting scenarios commonly handled by DevOps engineers.

---

## Part 1: Linux File System Hierarchy

Linux follows a hierarchical file system structure starting from the root directory `/`.

### 1. `/` – Root Directory

- The top-level directory of the Linux file system.
- All files and directories are located under this directory.
- I used `ls -l /` to explore the root directory.

**When I would use it:** To understand the overall Linux directory structure and locate important system directories.

### 2. `/home` – User Home Directories

- Stores personal directories and files for regular users.
- I used `ls -l /home` and `ls -la /home` to inspect its contents.
- The `ubuntu` user directory was present in my environment.

**When I would use it:** To locate user files, personal scripts, and project directories.

### 3. `/root` – Root User's Home Directory

- The home directory of the root user.
- Stores root user's configuration files and personal data.
- I used `ls -l /root` and `ls -la /root` to inspect its contents.

**When I would use it:** To access root user's configuration files and administrative scripts.

### 4. `/etc` – Configuration Files

- Contains system-wide configuration files.
- I used `ls -l /etc` to explore configuration directories.
- I also checked the hostname using `cat /etc/hostname`.
- The hostname displayed was `ubuntu`.

**When I would use it:** To troubleshoot system configuration, network settings, and service configuration issues.

### 5. `/var/log` – System Log Files

- Stores system and application log files.
- I explored it using `ls -lh /var/log`.
- Observed log files included `syslog`, `auth.log`, `kern.log`, and `dpkg.log`.
- Used `du -sh /var/log/* 2>/dev/null | sort -h | tail -5` to identify larger log files and directories.

**When I would use it:** To investigate system errors, service failures, authentication issues, and application problems.

### 6. `/tmp` – Temporary Files

- Stores temporary files created by applications and processes.
- Temporary files may be removed automatically by the system.
- I used `ls -la /tmp` to inspect its contents.

**When I would use it:** To store temporary troubleshooting files and test scripts.

### 7. `/bin` – Essential User Commands

- Contains essential executable commands.
- In my environment, `/bin` was a symbolic link to `/usr/bin`.
- I checked it using `ls -l /bin`.

**When I would use it:** To understand where essential Linux commands are located.

### 8. `/usr/bin` – User Commands and Utilities

- Contains many executable programs and command-line utilities.
- I explored it using `ls -l /usr/bin | head -10`.

**When I would use it:** To locate and understand commonly used Linux commands and utilities.

### 9. `/opt` – Optional Software

- Used for additional or third-party software packages.
- I explored it using `ls -l /opt`.

**When I would use it:** To locate optional applications and manually installed software.

---

## Part 2: Scenario-Based Troubleshooting Practice

### Scenario 1: Service Not Starting

**Objective:** Check whether a service exists and investigate its status.

Commands used:

```bash
systemctl status myapp
journalctl -u myapp -n 50
systemctl is-enabled myapp
systemctl --failed
```

**Observation:**

- The `myapp` service was not found in the environment.
- No journal entries were available for this service.
- `systemctl --failed` showed zero failed units.

**Conclusion:**

The `myapp` service was not installed or registered in this environment. This demonstrated how to check service availability, status, and related logs before troubleshooting further.

### Scenario 2: High CPU Usage

**Objective:** Monitor CPU and memory usage and identify resource-intensive processes.

Commands used:

```bash
top
ps aux --sort=-%cpu | head -10
```

**Observation:**

- CPU usage was approximately 4.3%.
- CPU idle time was approximately 95.7%.
- Memory usage and running processes were visible.
- No process showed unusually high CPU consumption.

**Conclusion:**

The system was healthy during this check. I learned how to monitor system resources and identify processes consuming CPU.

### Scenario 3: Finding Service Logs

**Objective:** Check Docker service status and investigate its logs.

Commands used:

```bash
systemctl status docker
journalctl -u docker -n 50
journalctl -u docker -f
```

**Observation:**

- Docker service was active and running.
- The Docker daemon initialized successfully.
- Logs showed container restoration and daemon initialization messages.
- Live logs were monitored using `journalctl -f`.

**Conclusion:**

I learned how to check service status, inspect historical logs, and monitor live logs using `journalctl`.

### Scenario 4: File Permission Issues

**Objective:** Understand Linux file permissions and fix an execution permission issue.

**Step 1: Create a directory**

```bash
mkdir -p /home/user
```

**Step 2: Create a shell script**

```bash
echo '#!/bin/bash
echo "Backup script executed successfully"' > /home/user/backup.sh
```

**Step 3: Check file permissions**

```bash
ls -l /home/user/backup.sh
```

**Step 4: Try executing the script**

```bash
/home/user/backup.sh
```

**Observation:** Received `Permission denied` because the script did not have execute permission.

**Step 5: Add execute permission**

```bash
chmod +x /home/user/backup.sh
```

**Step 6: Verify permissions**

```bash
ls -l /home/user/backup.sh
```

The file permissions showed the execute (`x`) permission.

**Step 7: Execute the script again**

```bash
/home/user/backup.sh
```

**Output:**

```text
Backup script executed successfully
```

**Conclusion:**

I learned how to identify a file permission issue and resolve it using `chmod +x`.

---

## Key Learnings

- Understood the Linux File System Hierarchy.
- Explored important directories and their purposes.
- Practiced checking service status using `systemctl`.
- Learned to monitor CPU and memory using `top` and `ps`.
- Practiced viewing service logs using `journalctl`.
- Understood Linux file permissions and executable permissions.
- Improved basic Linux troubleshooting skills.

## Conclusion

Day 07 helped me strengthen my Linux fundamentals through hands-on practice. Understanding the file system, monitoring processes, investigating service logs, and managing file permissions are important skills for real-world DevOps troubleshooting.