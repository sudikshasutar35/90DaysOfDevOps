# Day 08 – Cloud Server Setup: Docker, Nginx & Web Deployment

## Objective
Set up an AWS EC2 cloud server, install Docker and Nginx, deploy and verify the Nginx welcome page, and collect server logs.

## Cloud Server Details
- Cloud Provider: AWS EC2
- Instance Name: day8_server
- Instance Type: t3.micro
- Region: ap-south-1 (Mumbai)
- Operating System: Ubuntu 26.04.1 LTS
- Access Method: EC2 Instance Connect

## 1. Connect to EC2 Instance
Connected to the Ubuntu EC2 instance using AWS EC2 Instance Connect.

```bash
whoami
cat /etc/os-release
```

## 2. Update Package Lists

```bash
sudo apt update
```

## 3. Install Nginx

```bash
sudo apt install nginx -y
sudo systemctl enable --now nginx
sudo systemctl status nginx
```

Verified that the Nginx service was active and running.

## 4. Configure Security Group

Configured the following inbound rules:

| Type | Protocol | Port | Source |
|---|---|---:|---|
| SSH | TCP | 22 | My IP and EC2 Instance Connect prefix list |
| HTTP | TCP | 80 | 0.0.0.0/0 |

## 5. Verify Nginx Webpage

Opened the EC2 public IPv4 address in a browser using HTTP.

Successfully verified the default Nginx Welcome Page.

## 6. Install Docker

```bash
sudo apt install docker.io -y
sudo systemctl enable --now docker
docker --version
sudo systemctl status docker --no-pager
```

Docker version: 29.1.3

Verified that the Docker service was active and running.

## 7. Collect Nginx Logs

Collected access and error logs and saved them into a separate file.

```bash
sudo tail -n 50 /var/log/nginx/access.log
sudo tail -n 50 /var/log/nginx/error.log
```

Created the log file:

```bash
sudo sh -c '{
  echo "===== NGINX ACCESS LOGS ====="
  tail -n 50 /var/log/nginx/access.log
  echo
  echo "===== NGINX ERROR LOGS ====="
  tail -n 50 /var/log/nginx/error.log
} > /home/ubuntu/nginx-logs.txt'

sudo chown ubuntu:ubuntu /home/ubuntu/nginx-logs.txt
```

Verified the log file using:

```bash
cat ~/nginx-logs.txt
```

## 8. Verification Results

- EC2 instance status checks: Passed
- Nginx service: Active (running)
- Docker service: Active (running)
- Nginx webpage: Successfully accessible
- Nginx access and error logs: Collected successfully

## Key Learnings

- Launching and accessing an AWS EC2 instance.
- Configuring inbound Security Group rules.
- Installing and managing Nginx using systemd.
- Installing and verifying Docker.
- Accessing a public web server.
- Collecting and inspecting Nginx access and error logs.

## Files

- `day-08-cloud-deployment.md`
- `nginx-logs.txt`
- Screenshots of SSH connection, Nginx webpage, and Docker status.