# Day 19 – Shell Scripting Project: Log Rotation, Backup & Crontab

---

### Task 1: Log Rotation Script
Create `log_rotate.sh` that:
1. Takes a log directory as an argument (e.g., `/var/log/myapp`)
2. Compresses `.log` files older than 7 days using `gzip`
3. Deletes `.gz` files older than 30 days
4. Prints how many files were compressed and deleted
5. Exits with an error if the directory doesn't exist

<img width="1595" height="986" alt="image" src="https://github.com/user-attachments/assets/5a4e6a33-58bf-4c08-85dc-55b1491e3f7d" />

---

### Task 2: Server Backup Script
Create `backup.sh` that:
1. Takes a source directory and backup destination as arguments
2. Creates a timestamped `.tar.gz` archive (e.g., `backup-2026-02-08.tar.gz`)
3. Verifies the archive was created successfully
4. Prints archive name and size
5. Deletes backups older than 14 days from the destination
6. Handles errors — exit if source doesn't exist

<img width="1063" height="829" alt="image" src="https://github.com/user-attachments/assets/74863628-a2fd-43c7-a7f9-2f1de753f8c1" />
 
---

### Task 3: Crontab
1. Read: `crontab -l` — what's currently scheduled?
2. Understand cron syntax:
   ```
   * * * * *  command
   │ │ │ │ │
   │ │ │ │ └── Day of week (0-7)
   │ │ │ └──── Month (1-12)
   │ │ └────── Day of month (1-31)
   │ └──────── Hour (0-23)
   └────────── Minute (0-59)
   ```
3. Write cron entries (in your markdown, don't apply if unsure) for:
   - Run `log_rotate.sh` every day at 2 AM
   - Run `backup.sh` every Sunday at 3 AM
   - Run a health check script every 5 minutes


### scheduling log_rotate.sh every day at 2 AM

- `0 2 * * * /home/ubuntu/day19-Shell-scrpting/log_rotate.sh /var/log/myapp/`

### scheduling backup.sh every Sunday at 3 AM

- `0 3 * * 0 /home/ubuntu/day19-Shell-scrpting/backup.sh ./logs/`

### scheduling health check script every 5 mins

- `*/5 * * * * /home/ubuntu/shell-scripts/system_details.sh`
 

<img width="1410" height="895" alt="image" src="https://github.com/user-attachments/assets/72c9d288-6693-4c0e-9599-5b3c6fde7d99" />

---

### Task 4: Combine — Scheduled Maintenance Script
Create `maintenance.sh` that:
1. Calls your log rotation function
2. Calls your backup function
3. Logs all output to `/var/log/maintenance.log` with timestamps

<img width="1329" height="1007" alt="image" src="https://github.com/user-attachments/assets/08f1bb39-32e1-4e8b-a1a5-de70c535a606" />

4. Write the cron entry to run it daily at 1 AM

- `0 1 * * * /home/ubuntu/day19-Shell-scrpting/maintenance.sh`

<img width="1159" height="115" alt="image" src="https://github.com/user-attachments/assets/78497194-2f68-4d81-bc12-052278354f2c" />
  
---
