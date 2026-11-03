# Day 04: Linux Process, Service and Log Management

## Objective
Practice Linux process monitoring, service management, and log inspection using Killercoda Ubuntu terminal.

## 1. Process Management

### Command 1: `top`
**Purpose:** Displays real-time system processes and resource usage.

**Observation:**
- Total tasks: 136
- Running tasks: 1
- Sleeping tasks: 135
- Zombie tasks: 0
- CPU idle: 96.6%
- Total memory: approximately 1903 MiB

### Command 2: `ps aux | head -10`
**Purpose:** Displays the first 10 entries from the running process list.

**Observation:**
- Displayed process details such as USER, PID, CPU usage, memory usage and command.
- PID 1 was `/sbin/init`.

### Command 3: `pgrep -a systemd`
**Purpose:** Finds processes related to systemd.

**Observation:**
Found systemd-related processes, including:
- PID 1 – `/sbin/init`
- systemd-journald
- systemd-udevd
- systemd-networkd
- systemd-logind
- systemd-timesyncd
- systemd-resolved

## 2. Service Management

### Command 4: `systemctl status`
**Purpose:** Displays the overall systemd status.

**Observation:**
- System state: running
- Loaded units: 424
- Failed units: 0

### Command 5: `systemctl list-units --type=service --state=running`
**Purpose:** Lists currently running services.

**Observation:**
- 20 loaded service units were listed.
- Services included cron, docker, ssh, dbus and containerd.

### Command 6: `systemctl status cron`
**Purpose:** Checks the status of the cron service.

**Observation:**
- Service: cron.service
- Loaded: loaded and enabled
- Active: active (running)
- Main PID: 726
- Tasks: 8
- Memory: 6.4 MB

**Conclusion:** The cron service is running successfully.

## 3. Log Management

### Command 7: `journalctl -u cron -n 20 --no-pager`
**Purpose:** Displays the latest 20 log entries for the cron service.

**Observation:**
- Cron job execution entries were displayed.
- Logs showed PAM session opened and closed messages.
- A Debian system maintenance command was executed.

### Command 8: `journalctl -p warning -n 20 --no-pager`
**Purpose:** Displays the latest 20 warning-level and higher-priority log entries.

**Observation:**
- SSH service left-over process warnings were found.
- An rsyslog service failure message appeared.
- DHCP and IPv6-related messages were displayed.
- Cron environment variable warning was also found.

## 4. Key Learnings

- Learned how to monitor Linux processes using `top` and `ps`.
- Learned how to find specific processes using `pgrep`.
- Practiced checking and listing services using `systemctl`.
- Inspected the cron service and verified that it was running.
- Learned to view service-specific and system warning logs using `journalctl`.

  ## 5. Mini Troubleshooting Flow

### Scenario: Checking Cron Service Health

**Step 1: Check service status**

```bash
systemctl status cron
```

Result: Cron service was active (running).

**Step 2: Inspect service logs**

```bash
journalctl -u cron -n 20 --no-pager
```

Result: Reviewed recent Cron service activity and job execution logs.

**Step 3: Verify the service**

Confirmed that `cron.service` was active and enabled.

**Conclusion:** Used service status and journal logs together to inspect Cron service health.

## Conclusion

Successfully completed Day 04 Linux practice using Killercoda Ubuntu terminal. Practiced process monitoring, service inspection, and system log analysis.
