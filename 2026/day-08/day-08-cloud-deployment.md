# 🐧Day 08 – Cloud Server Setup: Docker, Nginx & Web Deployment
---
### Today's goal is to deploy a real web server on the cloud and learn practical server management.

- You will:

    - Launch a cloud instance (AWS EC2 or Utho)
    - Connect via SSH
    - Install Nginx
    - Configure security groups for web access (port 80 by default for nginx)
    - Extract and save logs to a file
    - Verify your webpage is accessible from the internet
This is real DevOps work - exactly what you'll do in production.

---

## 🐧Part 1: Launch Cloud Instance & SSH Access
- **Step 1: Create & launch a Cloud Instance**

 <img width="1895" height="406" alt="image" src="https://github.com/user-attachments/assets/92d7ed6f-8f92-4fd7-bc0d-28d2d2ae2303" />

- **Step 2: SSH into the Server**
- On your local machine, go to the path where your key is present (.pem) , here i am using git bash for windows.
- Do **chmod 400** to key.pem file, so that only the file owner can read the private key, preventing unauthorized access and satisfying SSH security requirements.
    - 4 (read)   → owner
    - 0 (none)   → group
    - 0 (none)   → others
      
<img width="1335" height="536" alt="image" src="https://github.com/user-attachments/assets/c808b23f-120c-4205-a809-f18ef39fa081" />

---

# 🐧Part 2: Install Docker & Nginx

- **`sudo apt update`** : to check the latest available package versions before installing or upgrading software.

<img width="1230" height="464" alt="image" src="https://github.com/user-attachments/assets/349da211-2528-4d85-9fe7-9e97e5c8f084" />

- **`sudo apt install nginx`** : To install nginx, in my case nginx is already installed 

<img width="1337" height="124" alt="image" src="https://github.com/user-attachments/assets/7f8b175a-37fe-424b-b4ed-d7bff507b4e3" />

- **`systemctl status nginx`** : to check if the nginx is running from console.

<img width="1179" height="314" alt="image" src="https://github.com/user-attachments/assets/d3660b9c-65a9-40e9-8f3e-81ffcce088bc" />

---

# 🐧PART 3: Web Access & Security Group

- **Test Web access**
- Open http://<PUBLIC-IP> on your local machine, in my case it is **http://ec2-13-234-136-69.ap-south-1.compute.amazonaws.com/**
- Fiest time it won't load, so you need to recheck security group (port 80 open)
- Add the port 80 if not added
  
<img width="1918" height="573" alt="image" src="https://github.com/user-attachments/assets/40fbebea-6a29-468a-adcd-3d9d414a67ff" />

- Try again

<img width="1468" height="498" alt="image" src="https://github.com/user-attachments/assets/590c2c11-c65a-48db-a5b6-297650caac1b" />

---

# 🐧Part 4: Extract Nginx Logs

## Step 1: View Nginx Logs
- To check **ngin=x** logs run `sudo ls /var/log/nginx`
- `cat error.log` : check the error logs
  
<img width="1013" height="118" alt="image" src="https://github.com/user-attachments/assets/045b66e6-429f-4146-b666-c5cc363a49a7" />

## Step 2: Save Logs to File

- `sudo tail -50 /var/log/nginx/access.log > nginx-logs.txt`
- `cat nginx-logs.txt`

<img width="1895" height="289" alt="image" src="https://github.com/user-attachments/assets/a8d7f02e-cc1b-44a5-8098-a71fee5b331b" />

## Step 3: Download Log File to Your Local Machine

#### On your local machine (new terminal window)
### For AWS:
- **`scp -i your-key.pem ubuntu@<your-instance-ip>:~/nginx-logs.txt .`**

#### For Utho:
- **`scp root@<your-instance-ip>:~/nginx-logs.txt .`**
  
<img width="1440" height="205" alt="image" src="https://github.com/user-attachments/assets/b9575a3d-df88-4d5d-ad9f-5d6cca37e9de" />

---

## 🐧Challenges Faced
- Port 80 not accessible initially
- opened a security group and added a port 80 for nginx

---

## 🐧What I Learned
- How to launch and access a cloud VM
- How to install and verify a web server
- How logs help verify real traffic
- Importance of security groups/firewall rules

---

## 🐧Why This Matters for DevOps
This task reflects real-world DevOps work such as deploying services on cloud servers, managing access securely, and validating deployments using logs.

---






















