# Day 14 – Networking Fundamentals & Hands-on Checks

---

## OSI Model:

<img width="741" height="344" alt="image" src="https://github.com/user-attachments/assets/efd02bbb-df62-409a-8e66-78067a176ba7" />

- **1. Physical:** Handels the **physical transmission of data**, deals with hardwares (cables, Network cards), and signals (voltage, bits (0's & 1's)), eg: ethernet cables, Wi-Fi Signals

- **2. Data Link:** It Ensures error free data transmission between 2 directly connected devices, eg: LAN

- **3. Network:** : It handels IP addressing & Routing. It decides where the data schould go accross different Networks

- **4. Transport:** : Ensures end-to-end communication i.e. data reaches the correct application
  - **TCP** : reliable communication
  - **UDP** : Fast but unreliable

- **5. Session:** : Manages sessions between applications

- **6. Presentation:** : Ensures data is in readable format, handles Encryption/Drcryption , Data Foramatting.

- **7. Application:** - Wehre user and applications interact with network, Protocols HTTP, FTP, SSH, DNS

## TCP/IP Model

<img width="551" height="640" alt="image" src="https://github.com/user-attachments/assets/5370d76d-474c-457c-a06d-9df55167bbb1" />

- **1. Network Access (Link)** : Equivalent to OSI **Data link + Physical**, handles hardware communication MAC addressing, ethernet

- **2. Internet** : Equivalent to **OSI Model Network layer**, handles IP addressing & Routing

- **3. Transport** : Ensures end-to-end communication i.e. data reaches the correct application
  - **TCP** : reliable communication
  - **UDP** : Fast but unreliable
  - **Port Numbers**
  - **Relibility**

- **4. Application** : It is equivalent to **Session + Presentation + Application** , handles HTTP, HTTPS, SSH, DNS. Manageges Physical transmission of data over the network.


- OSI = conceptual model

- TCP/IP = practical implementation

---

### Easy Memory trick:

- **P**lease
- **D**o
- **N**ot
- **T**hrow
- **S**ausage
- **P**izza
- **A**way

---

# Hands-on Networking Checks

---

## Step 1 – Identity

- `hostname -I` or `ip addr show` : 

<img width="1417" height="504" alt="image" src="https://github.com/user-attachments/assets/ce8fb840-ed12-402f-a8fa-77ef48197f30" />

- **IP Address** : 172.31.42.78 172.17.0.1

## Step 2 – Reachability

- `ping google.com`

<img width="1466" height="356" alt="image" src="https://github.com/user-attachments/assets/ea8e1522-edbd-43a9-bed1-0cf5f89f4d4e" />

- **icmp_seq=1** → Packet number

- **ttl=114** → Time To Live

- **time=1.76 ms** → Round Trip Time (RTT), or Latency

## Step 3 – Path

- `traceroute google.com`

<img width="1032" height="319" alt="image" src="https://github.com/user-attachments/assets/546e9ca3-afcd-4736-9753-d56db99c2596" />

- **Total hops** : 8
- **Timeouts at any hopes?** : Yes there are timeouts at hops 3, 4, and 5.
- **Any long delay?** : All values are between 1.7 ms – 2.4 ms, no long delay observed.

 ## Step 4 – Open Ports

- `ss -tulpn`
  
<img width="1874" height="472" alt="image" src="https://github.com/user-attachments/assets/9aac8188-846e-4fc5-bc34-13c5ee7c860c" />

- **Port number** : 80

- **Service name** : nginx, PID=589

- **Protocol (TCP/UDP)** : TCP

## Step 5 – DNS Resolution

- `dig google.com` or `nslookup google.com`

<img width="1073" height="683" alt="image" src="https://github.com/user-attachments/assets/c931c1e5-fbf7-4da6-92c5-7255688499d8" />

- **Resolved IP** : 142.250.70.78
- **TTL (Time to Leave)** : 148 Sec
- **Status Code:** NOERROR

## Step 7 – Connection Snapshot

- `netstat -an | head`

<img width="1073" height="386" alt="image" src="https://github.com/user-attachments/assets/d2ca658c-636a-4e1d-b4f8-dabb8feecc49" />

- All visible entries are listening

---

# Mini Port Probe

- `ss tulnp`

<img width="1872" height="439" alt="image" src="https://github.com/user-attachments/assets/9f7a230c-59f9-4b4d-b51a-38ca406f1618" />

- `nc -zv localhost 22`

<img width="1067" height="89" alt="image" src="https://github.com/user-attachments/assets/a0e9e6e6-d2e2-445f-8f52-e552b4552d59" />

- `curl -I http://localhost:80`

<img width="971" height="265" alt="image" src="https://github.com/user-attachments/assets/cd68a122-e87a-4524-aae5-7c56d954a5b5" />

- **Is port reachable?** : YES

- **If not → next check?**
    - check service status using  `systemctl status`
    - firewall

---

# Reflection 

- **Which command gives you the fastest signal when something is broken?**
  - `ping` or `curl -I <URL>`
  - **why?** - It is fast, simple, Immediate connection check.
    
- **What layer (OSI/TCP-IP) would you inspect next if DNS fails? If HTTP 500 shows up?**
  - **CASE 1: DNS Fails** - will run `dig google.com`
  - Problem is at Application Layer of OSI/TCP IP model
 
  - **Case 2: HTTP 500 Shows Up** : Internal server error so problem must be at Application Layer likely Backend application, Database, Permission issue or code crash
    
- **Two follow-up checks you’d run in a real incident.**
  - `curl -I <url>` or `ss -tulpn | grep 80`
  - To check:
      - Is the service listening?
      - Is the port open?
      - Is the app responding?
  - `journalctl -u nginx -n 50` or `tail -n 50 /var/log/nginx/error.log`
      - Logs usually give the fastest root cause clue.
   
### So the Flow will be

- 1. `ping` --> Check Reachable?

- 2. `dig` --> DNS working check

- 3. `curl -I <URL>` --> HTTP responding check

- 4. `ss -tulnp` --> Service listening check

- 5. check logs
 
---

