# Day 15 – Networking Concepts: DNS, IP, Subnets & Ports

## Task
Build on Day 14 by understanding the building blocks of networking every DevOps engineer must know.

You will:
- Understand how **DNS** resolves names to IPs
- Learn **IP addressing** (IPv4, public vs private)
- Break down **CIDR notation** and **subnetting** basics
- Know common **ports** and why they matter

This is concept-focused — research, understand, and document in your own words.

---

## Task 1: DNS – How Names Become IPs

### Explain in 3–4 lines: what happens when you type `google.com` in a browser?

- First, the browser checks if it already knows the IP from its own cache.
- If not, the OS checks its DNS cache.
- If still not found, the system sends a DNS query to the configured DNS resolver.
- The resolver finds the IP address and sends it back.
- Then the browser opens a TCP connection to that IP and starts loading the website.

### What are these record types? Write one line each:
  
- `A`, `AAAA`, `CNAME`, `MX`, `NS`
- `A`: Maps a domain name to an IPv4 address.
- `AAAA`: Maps a domain name to an IPv6 address.
- `CNAME`: Points one domain name to another domain name (alias).
- `MX`: Specifies the mail server responsible for receiving emails for a domain.
- `NS`: Defines the authoritative name servers for a domain.

### Run: `dig google.com` — identify the A record and TTL from the output

<img width="1307" height="492" alt="image" src="https://github.com/user-attachments/assets/3581584d-7245-47be-8a1a-77561fd09533" />

- **`A` record:** 142.250.206.174
- **TTL (time to leave):** 54 sec

---

## Task 2: IP Addressing

### What is an IPv4 address? How is it structured? (e.g., `192.168.1.10`)

   <img width="272" height="259" alt="image" src="https://github.com/user-attachments/assets/9d5e65ba-648a-452f-8684-54e49191377b" />
   
- IPV4 is a 32-bit address divided into 4 parts (octets), each octet consists of 8bits ranges from 0-255

### Difference between **public** and **private** IPs — give one example of each

- **Public IP**:
  
  - Used to communicate over the internet and is globally routable.
  - Assigned by an Internet Service Provider (ISP).
  - Example: 142.250.183.14 (Public IP of Google server) OR 8.8.8.8 (Google Public DNS)

- **Private IP**:
  
  - Used inside a local network (LAN) for communication between devices like computers, phones, and printers.
  - Not accessible from the internet; requires NAT to communicate outside the network.
  - Example: 192.168.1.10

### What are the private IP ranges?
   - `10.x.x.x` - `10.0.0.0 – 10.255.255.255`
   - `172.16.x.x – 172.31.x.x` - `172.16.0.0 – 172.31.255.255`
   - `192.168.x.x` - `192.168.0.0 – 192.168.255.255`

### Run: `ip addr show` — identify which of your IPs are private

<img width="1332" height="468" alt="image" src="https://github.com/user-attachments/assets/912c55dd-8c0b-4a68-87a1-25124c56167f" />

- **Private IP** - 172.31.42.78, Range 172.16.0.0 – 172.31.255.255

---

## Task 3: CIDR & Subnetting

### 1. What does `/24` mean in `192.168.1.0/24`?**

- `/24` denotes that number of bits used for network

### 2. How many usable hosts in a `/24`? A `/16`? A `/28`?

- To calculate usable Host we can use the forumla `2^host bits -2`
- `/24` - `32 - 24 (Bits used for Network) = 8`, so usable host will be `2^8 - 2 = 254`
- `/16` - `32 - 16 (Bits used for Network) = 16`, so usable host will be `2^16 - 2 = 65534`
- `/28` - `32 - 28 (Bits used for Network) = 4`, so usable host will be `2^4 - 2 = 14`
  
### 3. Explain in your own words: why do we subnet?

- Subnetting is the process of splitting one large network into smaller networks (subnets).
- Makes networks easier to manage
- Improves security by isolating resources
- Reduces network traffic

### 4. Quick exercise — fill in:

| CIDR | Subnet Mask     | Total IPs | Usable Hosts |
|------|-----------------|-----------|--------------|
| /24  | 255.255.255.0   | 256       | 254          |
| /16  | 255.255.0.0     | 65536     | 65534        |
| /28  | 255.255.255.240 | 16        | 14           |

---

## Task 4: Ports – The Doors to Services

### 1. What is a port? Why do we need them?

- An IP address identifies a machine, but a port identifies the application running on that machine.
- Because one machine runs multiple services at the same time.
  
### 2. Document these common ports:

| Port | Service |
|------|---------|
| 22   | SSH     |
| 80   | HTTP    |
| 443  | HTTPS   |
| 53   | DNS     |
| 3306 | MSSQL   |
| 6379 | Redis   |
| 27017| MongoDB |

### 3. Run `ss -tulpn` — match at least 2 listening ports to their services

<img width="1794" height="474" alt="image" src="https://github.com/user-attachments/assets/fa433b1a-c858-407e-a88d-0cad02930363" />

---

## Task 5: Putting It Together
Answer in 2–3 lines each:

### You run `curl http://myapp.com:8080` — what networking concepts from today are involved?
- Concepts involved:
    - DNS resolution
    - IP routing
    - TCP connection
    - Port 8080
    - HTTP protocol

### Your app can't reach a database at `10.0.1.50:3306` — what would you check first?

- First checks:
  - Ping 10.0.1.50
  - Port 3306 open?
  - Service running?
  - Firewall/security group?

---
