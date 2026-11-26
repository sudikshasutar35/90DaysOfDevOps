# Day 14 – Networking Fundamentals & Hands-on Checks

## 1. Objective

Learn basic networking concepts and practice essential Linux networking commands for troubleshooting connectivity, DNS, ports, and HTTP services.

## 2. OSI Model vs TCP/IP Model

### OSI Model – 7 Layers

| Layer | Name | Function |
|---|---|---|
| L7 | Application | Provides network services to applications |
| L6 | Presentation | Data formatting and encryption |
| L5 | Session | Manages communication sessions |
| L4 | Transport | Reliable data transfer using TCP/UDP |
| L3 | Network | IP addressing and routing |
| L2 | Data Link | MAC addressing and frames |
| L1 | Physical | Physical transmission of signals |

### TCP/IP Model – 4 Layers

| TCP/IP Layer | OSI Layers |
|---|---|
| Application | L5, L6, L7 |
| Transport | L4 |
| Internet | L3 |
| Link | L1, L2 |

### Network Protocols

- IP – Internet / Network Layer
- TCP and UDP – Transport Layer
- HTTP and HTTPS – Application Layer
- DNS – Application Layer

### Real Example

`curl https://example.com`

This command uses HTTPS at the Application Layer over TCP at the Transport Layer and IP at the Internet Layer.

## 3. Hands-on Networking Commands

### 1. Network Identity

Command:

`hostname -I`

Output:

`172.30.1.2 172.17.0.1`

Observation:

The command displayed the IP addresses assigned to the Linux machine and its network interfaces.

### 2. Network Reachability

Command:

`ping -c 4 google.com`

Observation:

- Resolved IP: 192.178.183.101
- Packets transmitted: 4
- Packets received: 4
- Packet loss: 0%
- Average latency: 13.075 ms

Google connectivity was successful with no packet loss.

### 3. Network Path

Command:

`tracepath google.com`

Observation:

The command displayed multiple network hops between the local machine and Google's network. Some intermediate hops showed no reply because routers may filter or ignore probe responses.

### 4. Listening Ports

Command:

`ss -tulpn`

Observation:

The command displayed listening TCP and UDP services.

Examples:
- SSH – Port 22
- DNS – Port 53
- Killercoda terminal – Port 40200
- Node.js – Port 40205

### 5. DNS Name Resolution

Command:

`nslookup google.com`

Observation:

The DNS server 8.8.8.8 successfully resolved google.com into multiple IPv4 and IPv6 addresses.

### 6. HTTP Check

Command:

`curl -I https://google.com`

Output:

`HTTP/2 301`

Observation:

Google returned a 301 Permanent Redirect response to https://www.google.com/.

Additional HTTP test:

`curl https://example.com`

Observation:

The server returned HTML content containing the page title "Example Domain".

### 7. Connections Snapshot

Command:

`netstat -an | head`

Observation:

The first 10 displayed lines included:
- 6 LISTEN entries
- 1 ESTABLISHED entry
- 1 TIME_WAIT entry

LISTEN indicates services waiting for connections. ESTABLISHED indicates an active TCP connection.

Note: These counts are only from the displayed output, not the complete connection table.

## 4. Mini Task – Port Probe & Interpret

Listening service identified:

SSH – Port 22

Command:

`nc -zv localhost 22`

Output:

`Connection to localhost (127.0.0.1) 22 port [tcp/ssh] succeeded!`

Observation:

The SSH port was reachable from localhost and the TCP connection test succeeded.

## 5. Reflection

### Which command gives the fastest signal when something is broken?

Ping provides a quick check of network reachability and packet loss.

### Which layer would you inspect if DNS fails?

I would inspect the Application Layer, including DNS configuration, DNS server availability, and name resolution.

### Which layer would you inspect if HTTP 500 appears?

I would inspect the Application Layer, including web server logs and application errors.

### Two follow-up checks during a real incident

1. Check service status using `systemctl status`.
2. Check application and system logs using `journalctl`.

## 6. Conclusion

Practiced essential Linux networking commands for checking IP addresses, connectivity, network paths, listening ports, DNS resolution, HTTP responses, and TCP connections.

This hands-on exercise improved my understanding of networking fundamentals and basic troubleshooting.

#90DaysOfDevOps #DevOpsKaJosh #TrainWithShubham