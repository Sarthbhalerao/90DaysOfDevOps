# Day 06 – Read and Write Text Files

## Objective
The objective of Day 06 is to practice basic Linux file operations using fundamental commands.  
This task focuses on creating files, writing and appending text, and reading file contents in different ways.

---

# Commands used:

- **mkdir -p** : Creates a parent directory if doesn't exists.
- **touch <filename>** : cretes empty file.
- **echo "message to write to file" > <file_name>** : Write text to a file, but **>** overwrites the content.
- **echo "message to write to file" >> <file_name>** : Write text to a file, but **>>** appends to the next line.
- **cat <file_name>** : read the conetnt of the file.
- **ls -lh <file_name>** : Displays file permissions, size, and last modified time in a human-readable format.
- **head -n 2 <file_name>**: Displays the first 2 lines of the file.
- **tail -n 2 <file_name>** : Displays the last 2 lines of the file.
- **echo "message to write to file" | tee -a <file_name>** : **echo** generates text , **| (pipe)** sends output to another command, **tee** writes input to file **AND stdout** , and **-a** ppend (does NOT overwrite)
---

# Key Learnings

- Learned the difference between overwrite (>) and append (>>).
- Understood how tee -a helps write and view output simultaneously.
- Practiced reading files using cat, head, and tail.
- Gained confidence in handling text files, which is essential for logs, configs, and scripts in DevOps

----
# Practice Snapshots:

<img width="1831" height="1705" alt="image" src="https://github.com/user-attachments/assets/66c63f07-2ff7-482f-9d27-84a950c00e60" />

<img width="1904" height="795" alt="image" src="https://github.com/user-attachments/assets/9a9ad23f-9aa0-405d-b043-40e923bbf52b" />
