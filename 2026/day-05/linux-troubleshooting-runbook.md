
# Day 05 - Linux Troubleshooting Runbook

## 1. Objective

Perform Linux troubleshooting checks and investigate the Apache2 web server and network services.

## 2. Environment Details

Commands:
- uname -a
- cat /etc/os-release

Environment:
- OS: Ubuntu 24.04.5 LTS
- Kernel: 6.8.0-146-generic
- Architecture: x86_64

## 3. Filesystem Checks

Commands:
- mkdir /tmp/runbook-demo
- cp /etc/hosts /tmp/runbook-demo/hosts-copy
- ls -l /tmp/runbook-demo

Observation:
- Created a temporary directory and attempted to copy the hosts file.
- The exact directory listing output was not retained.

## 4. CPU and Memory Checks

Commands:
- top -b -n 1 | head -20
- free -h

Observations:
- CPU and memory utilization were inspected.
- The recorded top output showed approximately 70% CPU idle.
- Memory availability and swap usage were checked.
- Exact output values were not retained.

## 5. Disk Usage Checks

Commands:
- df -h
- du -sh /var/log

Observations:
- Root filesystem: 19 GB total, 5.5 GB used, 13 GB available.
- Root filesystem utilization: 30%.
- /var/log directory size: 26 MB.
- Disk space was not critically low during the check.

## 6. Network Checks

Commands:
- ss -tulpn
- ping -c 5 google.com

Observations:
- Apache2 was listening on TCP port 80.
- SSH was listening on port 22.
- DNS services were listening on port 53.
- Ping test transmitted 5 packets and received all 5.
- Packet loss: 0%.
- Average ping response time: approximately 15.256 ms.

## 7. Apache2 and System Log Inspection

Commands:
- journalctl -u apache2 -n 50
- tail -n 50 /var/log/syslog

Observations:
- Apache2 started successfully.
- Apache logged an AH00558 warning because the fully qualified domain name was not configured.
- Nginx failed to bind to port 80 because the address was already in use.
- Apache2 was already listening on port 80, as confirmed by ss -tulpn.

## 8. Troubleshooting Findings

Problem:
Nginx could not start because port 80 was already occupied.

Evidence:
- Apache2 was listening on port 80.
- Nginx logs reported: Address already in use.
- Nginx service failed with result 'exit-code'.

Likely cause:
Both web servers attempted to use the same port.

## 9. If the Problem Gets Worse

1. Check Apache2 and Nginx service status.
2. Inspect service logs to identify new errors.
3. Check port usage and available disk and memory resources.

## 10. Conclusion

This practical covered Linux environment checks, filesystem operations, CPU and memory monitoring, disk usage, network connectivity and log inspection.

The main troubleshooting finding was a port 80 conflict between Apache2 and Nginx. Log inspection and listening-port checks helped identify the cause.
