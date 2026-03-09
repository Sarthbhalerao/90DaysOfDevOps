### Task 1: Basic Functions
1. Create `functions.sh` with:
   - A function `greet` that takes a name as argument and prints `Hello, <name>!`
   - A function `add` that takes two numbers and prints their sum
   - Call both functions from the script

<img width="1329" height="625" alt="image" src="https://github.com/user-attachments/assets/aac23d5a-2c97-4cb8-b0ec-8ba10459dcda" />

---

### Task 2: Functions with Return Values
1. Create `disk_check.sh` with:
   - A function `check_disk` that checks disk usage of `/` using `df -h`
   - A function `check_memory` that checks free memory using `free -h`
   - A main section that calls both and prints the results

<img width="1702" height="1015" alt="image" src="https://github.com/user-attachments/assets/5dcf3bdc-60c6-4ec1-9898-2aed79bf4ff8" />

---

### Task 3: Strict Mode — `set -euo pipefail`
1. Create `strict_demo.sh` with `set -euo pipefail` at the top
2. Try using an **undefined variable** — what happens with `set -u`?

<img width="1759" height="572" alt="image" src="https://github.com/user-attachments/assets/3b6ae4a0-e0a7-44cf-b3d2-91ed5df5d784" />

3. Try a command that **fails** — what happens with `set -e`?

<img width="1342" height="293" alt="image" src="https://github.com/user-attachments/assets/991c1836-85ef-4633-ad02-e330ab11c493" />

4. Try a **piped command** where one part fails — what happens with `set -o pipefail`?

<img width="1356" height="291" alt="image" src="https://github.com/user-attachments/assets/f470ac7d-0dfc-472a-8e5d-f663eea19746" />


- `set -e` → exits the script immediately if any command fails.
- `set -u` → exits the script when an undefined variable is used.
- `set -o pipefail` → ensures a pipeline fails if any command in the pipeline fails, not just the last one. 

---

### Task 4: Local Variables
1. Create `local_demo.sh` with:
   - A function that uses `local` keyword for variables
   - Show that `local` variables don't leak outside the function
   - Compare with a function that uses regular variables

<img width="1426" height="1120" alt="image" src="https://github.com/user-attachments/assets/69784f1b-ec22-4654-b36a-609fed67d6bc" />

---

### Task 5: Build a Script — System Info Reporter
Create `system_info.sh` that uses functions for everything:
1. A function to print **hostname and OS info**
2. A function to print **uptime**
3. A function to print **disk usage** (top 5 by size)
4. A function to print **memory usage**
5. A function to print **top 5 CPU-consuming processes**
6. A `main` function that calls all of the above with section headers
7. Use `set -euo pipefail` at the top

Output should look clean and readable.

<img width="1539" height="1823" alt="image" src="https://github.com/user-attachments/assets/4b23ac51-8b53-4a6c-ac9e-1284244f77f9" />

<img width="1491" height="1351" alt="image" src="https://github.com/user-attachments/assets/cee5d42f-ba47-42aa-a420-8384080bc786" />
