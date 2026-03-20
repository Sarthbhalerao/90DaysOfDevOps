# Day 20 – Bash Scripting Challenge: Log Analyzer and Report Generator

## Task

You are a system administrator responsible for managing a network of servers. Every day, a log file is generated on each server containing important system events and error messages. Your job is to analyze these log files, identify specific events, and generate a summary report.

Write a Bash script (`log_analyzer.sh`) that automates the process of analyzing log files and generating a daily summary report.

---


<img width="1484" height="2087" alt="image" src="https://github.com/user-attachments/assets/ade9c5b6-bc1a-408d-9a8e-298fd6de8ddf" />


<img width="1362" height="979" alt="image" src="https://github.com/user-attachments/assets/af63b1b7-3c6a-49a2-aaad-60d413e3f067" />

---

## Commands Used

## Input & Validation
- `$1` → first command-line argument (log file input)  
- `[ -f file ]` → checks if a file exists  
- `exit 1` → exits the script with an error status  

---

## Log Analysis
- `grep "ERROR" logfile` → searches for lines containing "ERROR"  
- `grep -E "ERROR|Failed" logfile` → searches for multiple patterns (ERROR or Failed)  
- `grep -c "ERROR" logfile` → counts occurrences of "ERROR"  
- `grep -n "CRITICAL" logfile` → prints matching lines with line numbers  

---

## Text Processing
- `awk '{print}'` → processes and formats text line by line  
- `awk -F: '{print $1}'` → splits text using delimiter (:)  
- `awk '{$1=$2=$3=""; print}'` → removes first 3 fields (timestamp cleanup)  

---

## Sorting & Counting
- `sort` → sorts lines alphabetically  
- `uniq -c` → counts duplicate lines  
- `sort -rn` → sorts numerically in descending order  
- `head -5` → shows top 5 results  

---

## Pipelines
- `| `→ passes output of one command as input to another  

- Example:
- `grep "ERROR" logfile | sort | uniq -c`

---

## File & Directory Operations
- `mkdir -p archive` → creates directory if it doesn’t exist  
- `mv file archive/` → moves file to another directory  
- `touch file` → creates an empty file  

---

## Report Generation
- `date +%Y-%m-%d`→ gets current date in YYYY-MM-DD format  
- `echo "text" > file` → writes text to file (overwrite)  
- `echo "text" >> file` → appends text to file  

---

## File Inspection
- `cat file` → displays full file content  
- `wc -l` → counts total number of lines in a file  

---

## Execution
- `chmod +x log_analyzer.sh`→ makes script executable  
- `./log_analyzer.sh sample_log.log` → runs script with input file  

---

## Combined Example

- `grep "ERROR" sample_log.log | awk '{$1=$2=$3=""; print}' | sort | uniq -c | sort -rn | head -5  `
→ extracts top 5 most frequent error messages
---

## What I Learned

- log analysis using bash
- text processing pipelines
- generating reports automatically
