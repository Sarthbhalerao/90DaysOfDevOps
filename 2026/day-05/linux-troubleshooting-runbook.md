# 🐧Day 05 – Linux Troubleshooting Drill: CPU, Memory, and Logs

## 🐧What is a Runbook?
A **runbook** is a short, repeatable checklist followed during an incident.  
It documents:
- The **exact commands** run
- **Observations** from each command
- **Next actions** if the issue worsens
- The goal is to keep it **concise, reusable, and pressure-friendly**.

---

## 🐧Target Service
- **Service:** ssh  
- **Why chosen:** Critical system access service

---

## 🐧STEP 1: Environment Basics Snapshot

- **uname -a** : Displays complete system info(kernel version, architecture, hostname, OS type)
- **lsb_release -a** : Shows Linux distribution details (Ubuntu version, release, codename).
- **cat /etc/os-release** : Prints detailed OS metadata (OS name, version, LTS info, codename, URLs).

  <img width="940" height="442" alt="image" src="https://github.com/user-attachments/assets/234fd387-6f46-411c-819f-d90f5e2115ad" />

 
## 🐧What I understood:
- **OS:** Ubuntu 24.04.3 LTS
- **Codename:** Noble
- **Kernel:** 6.14.0-1018-aws
- **Architecture:** x86_64
- **Environment:** AWS EC2 (Ubuntu user)
  
---
  
## 🐧Step 2. Filesystem Sanity Check

Ensure disk is writeable and behave normally.

- **mkdir /tmp/runbook-demo** : Creates a named runbook-demo under /tmp/
- **cp /etc/hosts /tmp/runbook-demo/hosts-copy && ls -l /tmp/runbook-demo** : Copies the /etc/hosts file into /tmp/runbook-demo as hosts-copy. If the copy succeeds, it lists the directory contents to confirm the file exists

<img width="940" height="210" alt="image" src="https://github.com/user-attachments/assets/7499fecb-d80b-472f-b529-136c2ceb6128" />

## 🐧What I understood:
- **Permissions:** -rw-r--r--

    - **rw- →** Owner can read & write
    
    - **r-- →** Group can read only
    
    - **r-- →** Others can read only
    
- **Ownership:** ubuntu

    - **user who owns the file:** ubuntu
    
    - **Group who owns the file:** ubuntu
    
- **No errors found**

---

## 🐧STEP 3. Identify the Service Process

- **ps aux | grep ssh**
  
  - **ps aux :** list all running process
  - **| :** sends output to another command
  - **grep ssh :** filters line contain ssh

<img width="940" height="256" alt="image" src="https://github.com/user-attachments/assets/a0fda070-b286-4051-ae52-82c35dc4d334" />

## 🐧What I understood:

<img width="940" height="61" alt="image" src="https://github.com/user-attachments/assets/29add75c-3a18-442e-ab55-f90b2fed669b" />
 
- The output confirms the SSH daemon is running, shows multiple active SSH login sessions for user ubuntu, but the **main SSH service** is running with **user root** and having **PID 1205** and displays the temporary privileged processes handling authentication.
---

## 🐧STEP 4. CPU & Memory Snapshot

- **Top :** shows live process

  <img width="940" height="1084" alt="image" src="https://github.com/user-attachments/assets/be1d5d61-b80a-4b20-89a5-3f2a2e3c5050" />

- **ps -o pid,pcpu,pmem,comm -p <PID> :** 

**What it shows:**

- **ps** → Displays process information (process state)
- **-o** → Specifies which output columns to display
- **pid** → Process ID
- **pcpu** → CPU usage percentage
- **pmem** → Memory usage percentage
- **comm** → Command name
- **-p <PID>** → Shows information only for the specified process ID(s)

<img width="940" height="56" alt="image" src="https://github.com/user-attachments/assets/74b85324-6e27-43d0-a4ea-8f1c4c1e8905" />

## 🐧What I understood:

  - **System load:** 0.00, 0.00, 0.00 → system idle, no CPU pressure
  - **CPU:** ~99.7% idle → no CPU bottleneck
  - **Processes:** 122 total (2 running, 120 sleeping, 0 zombie) → healthy state
  - **Memory:** ~419 MiB used, swap 0 → normal usage; cache is expected
  - **Top processes:** top (~0.7% CPU), containerd (~5% MEM) → no abnormal activity
    
**Conclusion:**
- System is healthy with no resource contention or runaway processes.
---

## 🐧STEP 5. Disk & IO Check

- **Df -h :** Shows total, used, and available disk space in human-readable format

 <img width="940" height="351" alt="image" src="https://github.com/user-attachments/assets/25f7940a-a510-4434-ae0b-ac1a29c2ed39" />
 
- **du -sh /var/log :** Check directory size
    -	**-s** = summary only
    -	**-h** = human-readable

<img width="940" height="118" alt="image" src="https://github.com/user-attachments/assets/12f9722b-7d33-45f8-a5e6-7eec43b40425" />

- **iostat :** shows disk I/O performance 

<img width="936" height="315" alt="image" src="https://github.com/user-attachments/assets/b940ad0f-a338-4e9f-8e8e-9415e9ae87b0" />

- **vmstat :** shows memory, CPU, and I/O pressure

<img width="940" height="108" alt="image" src="https://github.com/user-attachments/assets/72538c4e-cb91-41b7-a8d7-30f32579dca6" />
 
- **dstat :** shows a combined real-time system view of CPU, DISK, net, and memory

<img width="940" height="841" alt="image" src="https://github.com/user-attachments/assets/f3323960-378d-4958-ab8a-3ea2ca52efa6" />
 
## 🐧What I understood:

- **Disk space:** Root filesystem is only 14% used; all partitions have ample free space. No disk capacity risk.
- **Logs:** /var/log is ~60 MB, which is small and well within normal limits.
- **Disk I/O:** iostat shows very low I/O activity and negligible iowait; storage is not a bottleneck.
- **Memory:** vmstat shows no swap usage, sufficient free memory, and healthy buffer/cache usage.
- **CPU:** System is mostly idle (~100% idle) with no CPU or I/O pressure.
- **The system is healthy and stable with no CPU, memory, disk, or I/O contention observed. No immediate remediation required.**

---
## 🐧STEP 6. Network Sanity

- **ss -tulpn | grep ssh :** checks whether the SSH service is listening on a network port.

  - **ss →** shows network connections and listening ports
  - **-t →** TCP sockets
  - **-u →** UDP sockets
  - **-l →** Listening ports only
  - **-p →** Show process using the port
  - **-n →** Show numeric ports
  - **| grep ssh →** Filters output to show only SSH-related entries
  
- **curl -I localhost :** checks whether a web service is responding on the local machine.

- **ping localhost :** checks basic network connectivity to the local machine.

<img width="940" height="352" alt="image" src="https://github.com/user-attachments/assets/92e95ca0-f83a-4298-bd2b-11e4d1c59410" />

## 🐧What I understood:

- **SSH service:** sshd is running and listening on port 22 for both IPv4 (0.0.0.0:22) and IPv6 ([::]:22), managed by systemd. No port or binding issues.
- **HTTP service:** curl -I localhost returns HTTP/1.1 200 OK, confirming a local nginx (v1.24.0) web server is running and responding on port 80.
- **Network stack:** ping localhost succeeds with low latency, confirming the loopback interface and local networking are healthy.

**Core services (SSH and HTTP) are operational, ports are listening correctly, and local network connectivity is functioning as expected. No service or network issues detected.**

---

## 🐧STEP 7. Log Investigation

- **journalctl -u ssh -n 50 :** shows the last 50 log entries for the SSH service.

- **Journalctl :** is a tool to query systemd logs

<img width="940" height="559" alt="image" src="https://github.com/user-attachments/assets/7c2c5bdc-a4a1-4589-90c3-fe460e66a21c" />

- **tail -n 50 /var/log/auth.log :** provides a quick snapshot of the latest authentication activity, essential for SSH and access troubleshooting.

<img width="940" height="481" alt="image" src="https://github.com/user-attachments/assets/887949f0-d14a-4779-9ba7-0e41d7efaba9" />

- **grep ssh /var/log/auth.log | tail -n 20 :** shows focused view of the latest SSH authentication activity.

<img width="940" height="216" alt="image" src="https://github.com/user-attachments/assets/435c22b2-428e-4bc9-85a2-8f4e2f1f1c73" />

## 🐧What I understood:

- **SSH service is functioning correctly with secure, key-based access for the ubuntu user. There are routine background login attempts from external Ips.**

---
## 🐧If this worsens, what will be our next plan?

- **Restart ssh using systemctl restart ssh and monitor logs.**
- **Enable debug logging temporarily.**
- **Capture strace on the PID to analyze blocking calls.**
- **When troubleshooting, always think in this order:**
- **Context → Resources → Reachability → Evidence → Next Actions**

