# Day 15 – Networking Concepts: DNS, IP, Subnets & Ports

## Task 1: DNS – How Names Become IPs

### 1. How DNS works

1. When we type `google.com` in a browser, the computer checks its DNS cache.
2. If the IP address is not cached, a DNS resolver finds the IP address of the domain.
3. DNS returns the IP address to the browser.
4. The browser connects to the server using that IP address and loads the website.

### 2. DNS Record Types

| Record | Description |
|---|---|
| A | Maps a domain name to an IPv4 address. |
| AAAA | Maps a domain name to an IPv6 address. |
| CNAME | Maps one domain name to another domain name (alias). |
| MX | Specifies the mail servers responsible for receiving emails. |
| NS | Specifies the authoritative name servers for a domain. |

### 3. DNS Practical Commands

**Command:**
```bash
dig google.com
```

**A Records:**
```text
74.125.130.100
74.125.130.101
74.125.130.113
74.125.130.139
74.125.130.138
74.125.130.102
```

- Query Type: A
- TTL: 67 seconds
- DNS Server: 8.8.8.8
- Query Status: NOERROR

**Additional Command:**
```bash
dig google.com AAAA
```

**IPv6 Addresses:**
```text
2404:6800:4003:c11::64
2404:6800:4003:c11::66
2404:6800:4003:c11::71
2404:6800:4003:c11::8b
```

- Query Type: AAAA
- TTL: 155 seconds
- DNS Server: 8.8.8.8
- Query Status: NOERROR

## Task 2: IP Addressing

### 1. What is IPv4?

IPv4 (Internet Protocol Version 4) is a 32-bit address used to identify devices on a network. It consists of four octets separated by dots. Each octet ranges from 0 to 255.

Example: `192.168.1.10`

### 2. Public IP vs Private IP

| Public IP | Private IP |
|---|---|
| Used for communication over the internet. | Used inside private networks. |
| Example: 8.8.8.8 | Example: 192.168.1.10 |

### 3. Private IP Ranges

| Private Range | CIDR |
|---|---|
| 10.0.0.0 – 10.255.255.255 | 10.0.0.0/8 |
| 172.16.0.0 – 172.31.255.255 | 172.16.0.0/12 |
| 192.168.0.0 – 192.168.255.255 | 192.168.0.0/16 |

### 4. IP Address Practical

**Command:**
```bash
ip addr show
```

**Observed IP Addresses:**

| Interface | IP Address | Type |
|---|---|---|
| lo | 127.0.0.1/8 | Loopback |
| enp1s0 | 172.30.1.2/24 | Private IPv4 |
| docker0 | 172.17.0.1/16 | Private IPv4 |

Both `172.30.1.2` and `172.17.0.1` belong to the private IP range `172.16.0.0/12`.

### Additional Command: IP Route

```bash
ip route
```

- Default Gateway: 172.30.1.1
- Network Interface: enp1s0
- Source IP: 172.30.1.2
- Docker Network: 172.17.0.0/16
- Main Network: 172.30.1.0/24

## Task 3: CIDR & Subnetting

### 1. What does /24 mean?

In `192.168.1.0/24`, the `/24` means that 24 bits are used for the network portion and the remaining 8 bits are used for the host portion.

### 2. CIDR Table

| CIDR | Subnet Mask | Total IPs | Usable Hosts |
|---|---|---:|---:|
| /24 | 255.255.255.0 | 256 | 254 |
| /16 | 255.255.0.0 | 65,536 | 65,534 |
| /28 | 255.255.255.240 | 16 | 14 |

Formula:

- Total IPs = 2^(32 - prefix)
- Usable Hosts = Total IPs - 2

### 3. Why do we subnet?

Subnetting divides a large network into smaller networks. It helps manage IP addresses efficiently, improves network security, reduces unnecessary traffic, and makes network management easier.

## Task 4: Ports – The Doors to Services

### 1. What is a Port?

A port is a logical communication endpoint used by applications and services on a device. IP addresses identify devices, while port numbers identify specific services or applications.

### 2. Common Ports

| Port | Service | Purpose |
|---:|---|---|
| 22 | SSH | Secure remote login |
| 80 | HTTP | Web traffic |
| 443 | HTTPS | Secure web traffic |
| 53 | DNS | Domain name resolution |
| 3306 | MySQL | Database service |
| 6379 | Redis | In-memory database/cache |
| 27017 | MongoDB | NoSQL database |

### 3. Listening Ports Practical

**Command:**
```bash
ss -tulpn
```

**Observed Listening Ports:**

| Port | Protocol | Process / Service |
|---:|---|---|
| 53 | TCP/UDP | systemd-resolve (DNS) |
| 22 | TCP | sshd (SSH) |
| 40200 | TCP | kc-terminal |
| 40205 | TCP | node |
| 40300 | TCP | runtime-scenari |
| 36669 | TCP | containerd |

Two identified services:

- Port 22 – SSH service (sshd)
- Port 53 – DNS service (systemd-resolve)

Note: Ports 40200, 40205 and 40300 are environment-specific ports in Killercoda.

## Task 5: Putting It Together

### 1. What happens when you run curl http://myapp.com:8080?

- DNS resolves `myapp.com` into an IP address.
- The IP address identifies the destination server.
- Port 8080 identifies the application service.
- HTTP is used to communicate with the web server.

### 2. App cannot reach database at 10.0.1.50:3306

First, check whether the database server IP is reachable. Then verify whether MySQL is running and listening on port 3306. Also check firewall rules, network connectivity, and database configuration.

## What I Learned – 3 Key Points

1. DNS translates domain names into IP addresses using different DNS record types.
2. IP addressing and subnetting help identify devices and organize networks efficiently.
3. Ports allow multiple services to communicate on the same device, and tools like `ss` help identify listening services.

---

**Day 15 – Networking Concepts Completed**

#90DaysOfDevOps #DevOpsKaJosh #TrainWithShubham