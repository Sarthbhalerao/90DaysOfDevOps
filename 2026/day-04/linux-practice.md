# 🐧Linux Practice: Processes and Services

Today’s goal is to practice Linux fundamentals with real commands.
- Practice Basic commands
- Check running processes
- Inspect one systemd service
- Capture a small troubleshooting flow
---

## 1.	Let’s check the environment first.
- **uname  -a** : Shows the complete system information
    
<img width="955" height="115" alt="image" src="https://github.com/user-attachments/assets/f09e1e06-70f0-421f-941b-cb13111beb9f" />

- Linux → Kernel name
- ip-172-31-42-78 → Hostname
- 6.14.0-1018-aws → Kernel version
- #18~24.04.1-Ubuntu SMP → Build info
- x86_64 → CPU architecture (64-bit)
- GNU/Linux → Operating system type

 ---
 
## 2.	Practice basic file and directory commands:

- **mkdir** : create a empty directory
- **rmdir** : remove an empty directory 
- **touch** : create a empty file
- **cp** : copy file
- **mv** : move/ rename file
- **rm** : remove file

<img width="856" height="561" alt="image" src="https://github.com/user-attachments/assets/03ae83ef-1a7f-434f-b3ae-8c3f55ed806a" />

---

## 3.	Process checks commands

- **ps aux** : Lists all running process on system
- **ps aux | head** : Lists first 10 running processes
<img width="946" height="174" alt="image" src="https://github.com/user-attachments/assets/6ed655c8-e9fe-48c2-82e9-6e7bc4e89548" />

- **top** Live process Monitor
- **htop** : Advance process view

<img width="895" height="507" alt="image" src="https://github.com/user-attachments/assets/8871d1a1-5156-4ea5-abd4-44fb933e4e40" />

<img width="903" height="510" alt="image" src="https://github.com/user-attachments/assets/012b9b95-b9b6-471f-8798-6992872c5d3a" />

- **kill PID** : Stop process
- **kill -9 PID** : Force stop process
- **free -h** : check free system RAM

<img width="964" height="146" alt="image" src="https://github.com/user-attachments/assets/9f31e425-22cf-47a2-abf0-36b410e337a7" />

---

## 4.	Service Management Commands:

- **systmctl status  <Service>** : check service status
- **systemctl start <Service>** :start service
- **systemctl stop <Service>** : stop servcie
- **systemctl restart <service>** : Restart service
- **ss tulnp | grep nginx** :  check the service is running on which port
	- **-t** → TCP sockets
	- **-u** → UDP sockets
	- **-l** → Listening sockets only
	- **-n** → Show port numbers (don’t resolve names)
	- **-p** → Show process using the socket (PID / program name)
- **journalctl -u <Service>** : check service logs.

-**Target Service**: nginx
-**Running on Port**: 80
-**Status**: running
-**Log status**: Logs looks normal no error found

<img width="920" height="349" alt="image" src="https://github.com/user-attachments/assets/8658b8c8-04b9-4400-9d53-26506ad83998" />

<img width="1090" height="739" alt="image" src="https://github.com/user-attachments/assets/26176f2f-28ff-49ac-943b-8e66de990591" />












