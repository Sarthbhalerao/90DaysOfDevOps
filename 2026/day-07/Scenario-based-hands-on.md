## Hands-on task:
---

# Find the largest log file in /var/log
- `du -sh /var/log/* 2>/dev/null | sort -h | tail -5`

  lets break this command what it does,
  - `du` : checks disk usage
  - `du -s` : shows the total size of each directory not each sub file.
  - `du -h` : shows output in human readble form, i.e. kb, mb, gb
  - `/var/logs/*` : target all files from directory `/var/logs/`, this directory contains system , application & service logs
  - `2>/dev/null/` : redirects error message to trash bin. **2** is a standard error (stderr), and **/dev/null/** is a trash bin. this can be used to hide permission denied, inaccessible log files error.
  - `| (pipe)` : sends output of previous command to the next command after pipe
  - `sort -h` : sort output in human readable form like KB < MB < GB
  - `tail -5` : shows last 5 lines of sorted output.

<img width="1007" height="134" alt="image" src="https://github.com/user-attachments/assets/f0799e7e-7d3b-4572-bb4b-5c23459aecf9" />
  
 ---

# Look at a config file in /etc
- `cat /etc/hostname` : reads the file called **hostname** from **/etc/**
<img width="1472" height="58" alt="image" src="https://github.com/user-attachments/assets/a41d082a-64a2-4658-8035-7f259fa18076" />

---

# Check your home directory
- `ls -la ~` : Is used to list the content of your home directory 

<img width="1595" height="363" alt="image" src="https://github.com/user-attachments/assets/8ffd4020-28f6-4293-af71-a73a3ced13ab" />

---

# Scenario-Based Practice

----

# Scenario 1: Service Not Starting

- A web application service called 'myapp' failed to start after a server reboot. We are taking **nginx** service here
- What commands would you run to diagnose the issue?
- Write at least 4 commands in order.

## My Approach:

- **Step 1: systemctl status myapp**
- **Why:** To check if the service is running, stopped, or failed

<img width="1368" height="339" alt="image" src="https://github.com/user-attachments/assets/73a91b18-682c-480d-8282-4da5dc2de808" />

- **Step 2: journalctl -u myapp -n 50**
- **Why:** To inspect recent logs and identify the failure reason

<img width="1330" height="238" alt="image" src="https://github.com/user-attachments/assets/ec65a981-e712-4b6a-b6e5-4219d73e3cf9" />

- **Step 3: systemctl is-enabled myapp** 
- **Why:** To verify whether the service is configured to start on boot

<img width="876" height="74" alt="image" src="https://github.com/user-attachments/assets/969987d1-5d85-4cf3-b18f-e748ba9ef208" />

- **Step 4: systemctl list-units --type=service**  
- **Why:** To confirm which the service exists on the system

<img width="1583" height="925" alt="image" src="https://github.com/user-attachments/assets/136e2922-bf3d-46fb-9211-e782feed519d" />

- **systemctl list-units --type=service | grep myapp**  
- **Why:** To confirm whether our service exists on the system
  
<img width="1209" height="94" alt="image" src="https://github.com/user-attachments/assets/bc8720e6-3e01-4981-89d6-c3a9b97d2ace" />

---

# Scenario 2: High CPU Usage
- Your manager reports that the application server is slow.
- You SSH into the server. What commands would you run to identify which process is using high CPU?

## My Approach

- **Step 1: top**
- **Why:** To view live CPU and memory usage of processes

<img width="1603" height="2152" alt="image" src="https://github.com/user-attachments/assets/f7e553a2-ddd8-40cb-992e-164a58307c5e" />

- **Step 2: ps aux --sort=-%cpu | head -10**  
- **Why:** To list top CPU-consuming processes in a static view

<img width="1461" height="244" alt="image" src="https://github.com/user-attachments/assets/69739160-5ac2-48e3-9b48-0f59171fcd1e" />

- **Step 3: Note the PID of the top process**  
- **Why:** PID is required for further investigation or action

---

# Scenario 3: Finding Service Logs

- **Step 1: systemctl status docker**  
- **Why:** To confirm service status and identify log source

<img width="1911" height="395" alt="image" src="https://github.com/user-attachments/assets/59f1b49b-c36b-40a0-9e33-019561fe19d5" />

- **Step 2: journalctl -u docker -n 50**  
- **Why:** To view recent logs for the docker service

<img width="1907" height="362" alt="image" src="https://github.com/user-attachments/assets/7595260c-10e2-49d8-a561-c89d146bf655" />

- **Step 3: journalctl -u docker -f**  
- **Why:** To monitor logs in real time

<img width="1919" height="282" alt="image" src="https://github.com/user-attachments/assets/3033524a-6129-4b45-a505-d6597ab623c4" />

---

# Scenario 4: File Permissions Issue


