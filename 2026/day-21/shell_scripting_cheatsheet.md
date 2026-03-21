# Shell Scripting Cheat Sheet

---

## Quick Reference

| Topic | Key Syntax | Example |
|-------|-----------|---------|
| Variable | `VAR="value"` | `NAME="DevOps"` |
| Argument | `$1`, `$2` | `./script.sh arg1` |
| If | `if [ condition ]; then` | `if [ -f file ]; then` |
| For loop | `for i in list; do` | `for i in 1 2 3; do` |
| Function | `name() { ... }` | `greet() { echo "Hi"; }` |
| Grep | `grep pattern file` | `grep -i "error" log.txt` |
| Awk | `awk '{print $1}' file` | `awk -F: '{print $1}' /etc/passwd` |
| Sed | `sed 's/old/new/g' file` | `sed -i 's/foo/bar/g' config.txt` |


---

## 🐧 Bash Basics 

---

## Shebang (`#!/bin/bash`)

- Defines which interpreter should run the script.

```bash
#!/bin/bash
echo "Hello World."
```

- Ensures the script runs with Bash (not sh or another shell)

---

## Running a Script

### Make executable:

```bash
chmod +x script.sh
```

### Run script:

```bash
./script.sh
```

### Or run using bash:

```bash
bash script.sh
```

- `./script.sh` uses shebang
- `bash script.sh` ignores shebang and forces bash

---

## Comments

### Single-line comment:

```bash
# This is a comment
```

### Inline comment:

```bash
echo "Hello"  # prints Hello
```

### Multiline comment:

```bash
<< note
 Anything written here will get commented.
>>
```
- Bash ignores comments

---

## Variables

### Declare:

```bash
NAME="Sarthak"
```

### Use:

```bash
echo $NAME
```

### Quoting:

```bash
echo "$NAME"   # safe (recommended)
echo '$NAME'   # prints literally: $NAME
```
- Use double quotes to handle spaces safely

---

## Reading User Input (`read`)

```bash
read -p "Enter your name: " NAME
echo "Hello $NAME"
```

- Takes input from the user and stores it in a variable

---

## Command-Line Arguments

```bash
echo "Script name: $0"
echo "First argument: $1"
echo "Counts total arguments except 0'th argument: $#"
echo "Prints all arguments: $@"
```

### Example:

```bash
./script.sh file1.txt file2.txt
```

### Output:

```
Script name: ./script.sh
First argument: file1.txt
Total arguments: 2
All arguments: file1.txt file2.txt
```

---

## Exit Status (`$?`)

- `$?` - Checks the command success
```bash
ls file.txt
echo $?
```

- `0` → success
- non-zero → error

---

## Summary

- Shebang defines an interpreter
- Scripts run via `./` or `bash`
- Variables store data
- `read` takes user input
- `$1`, `$@`, `$#` handle arguments
- `$?` checks command success

---

# 🐧 Bash – Operators and Conditionals

## String Comparisons

```bash
[ "$a" = "$b" ]    # equal
[ "$a" != "$b" ]   # not equal
[ -z "$a" ]        # string is empty or not, also can be used to check if the argument is provided or not while running the script as [ -z "$1" ]
[ -n "$a" ]        # string is not empty
```

### Example:

```bash
name="Sarthak"

if [ "$name" = "Sarthak" ]; then
    echo "Match found."
fi
```

---

## Integer Comparisons

```bash
[ "$a" -eq "$b" ]  # equal
[ "$a" -ne "$b" ]  # not equal
[ "$a" -lt "$b" ]  # less than
[ "$a" -gt "$b" ]  # greater than
[ "$a" -le "$b" ]  # less than or equal
[ "$a" -ge "$b" ]  # greater than or equal
```

### Example:

```bash
num=10

if [ "$num" -gt 5 ]; then
    echo "Greater than 5"
fi
```

---

## File Test Operators

```bash
[ -f file.txt ]   # file exists and is a regular file
[ -d dir ]        # directory exists
[ -e path ]       # path exists
[ -r file ]       # readable
[ -w file ]       # writable
[ -x file ]       # executable
[ -s file ]       # not empty
```

### Example:

```bash
if [ -f "log.txt" ]; then
    echo "File exists."
fi
```

---

## if, elif, else Syntax

```bash
if [ condition ]; then
    # commands
elif [ condition ]; then
    # commands
else
    # commands
fi
```

### Example:

```bash
num=5

if [ "$num" -gt 10 ]; then
    echo "Greater than 10"
elif [ "$num" -eq 5 ]; then
    echo "Equal to 5"
else
    echo "Less than 5"
fi
```

---

## Logical Operators

```bash
[ condition1 ] && [ condition2 ]   # AND
[ condition1 ] || [ condition2 ]   # OR
! [ condition ]                   # NOT
```

### Example:

```bash
age=20

if [ "$age" -gt 18 ] && [ "$age" -lt 30 ]; then
    echo "Eligible"
fi
```

---

## Case Statements

- Instead of writing multiple if-elif, you use case → cleaner + easier to read.

```bash
case "$var" in
    pattern1)
        commands ;;
    pattern2)
        commands ;;
    *)
        default ;;
esac
```

### Example:

```bash
choice="start"

case "$choice" in
    start)
        echo "Starting service" ;;
    stop)
        echo "Stopping service" ;;
    *)
        echo "Invalid option" ;;
esac
```
### Important Parts You Should Remember

1. `pattern)` → This is what you're matching against.
 ```bash
start)
stop)
```
2. `;;` → Means: stop checking further cases, Without it → script may behave unexpectedly.

3. `*` → Default case (like else), Runs when no pattern matches

```bash
*)
```
### Multiple Patterns in One Case

```bash
choice="restart"

case "$choice" in
    start|restart)
        echo "Starting service" ;;
    stop)
        echo "Stopping service" ;;
    *)
        echo "Invalid option" ;;
esac
```
```bash
Output:
Starting Service
```

### When to Use case vs if

| Use `case` |	Use `if` |
| -----------| -------- |
| Fixed options (start/stop/restart)	| Complex conditions |
| Pattern matching (*.txt) |	Numeric/logical checks |
| Cleaner CLI handling	| Comparisons |


---

## Summary

- Use `[ ]` for conditions
- Strings → `=`, `!=`, `-z`, `-n`
- Numbers → `-eq`, `-gt`, etc.
- Files → `-f`, `-d`, etc.
- Combine conditions using `&&`, `||`, `!`
- Use `case` for multiple conditions

---

# 🐧 Bash – Loops

---

## for Loop (List-Based)

- Run this loop for each item in a list

```bash
for item in a b c; do
    echo "$item"
done
```

### Example:

```bash
for name in Alice Bob Charlie; do
    echo "Hello $name"
done
```

---

## for Loop (C-Style)

- Run this loop like programming languages (C/Java) — using a counter

```bash
for ((i=1; i<=5; i++)); do
    echo "$i"
done
```

- “Double parentheses enable arithmetic evaluation and allow C-style syntax in Bash.”

### Example:

```bash
for ((i=1; i<=3; i++)); do
    echo "Iteration $i"
done
```

---

## while Loop

- runs while condition is TRUE

```bash
while [ condition ]; do
    # commands
done
```

### Example:

```bash
i=1

while [ $i -le 3 ]; do
    echo "Iteration $i"
    ((i++))
done
```
```bash
Output: 
Iteration 1
Iteration 2
Iteration 3
```
---

## until Loop

- runs until condition becomes TRUE (i.e., while it is FALSE)
- until = opposite of while

```bash
until [ condition ]; do
    # commands
done
```

### Example:

```bash
i=1

until [ $i -gt 3 ]; do
    echo "Iteration $i"
    ((i++))
done
```
```bash
Output: 
Iteration 1
Iteration 2
Iteration 3
```
- Runs until condition becomes true


- **Pro Tip**

- Use while → when condition is natural/positive

- Use until → when condition is negative or waiting for something

---

## Loop Control

### break (exit loop)

```bash
for i in 1 2 3 4; do
    if [ "$i" -eq 3 ]; then
        break
    fi
    echo "$i"
done
```

### continue (skip iteration)

- skip the rest of the current iteration and jump to the next loop cycle
- It does NOT stop the loop, just skips one round.

```bash
Loop starts
   ↓
Check condition
   ↓ 
True? → continue → skip everything below → next loop
   ↓   
False → run remaining code
```

```bash
for i in 1 2 3 4; do
    if [ "$i" -eq 3 ]; then
        continue
    fi
    echo "$i"
done
```
```bash
Output:
1
2
4
```
---

## Looping Over Files

```bash
for file in *.log; do
    echo "Processing $file"
done
```

- Useful for batch processing log files

---

## Looping Over Command Output

- Instead of loading everything at once, it processes one line at a time — efficient and clean.
- 
```bash
while read line; do
    echo "$line"
done < file.txt
```
- **How it works**
- read line → reads one line from file.txt
- Stores it in a variable line
- Loop runs for each line in the file

### Example:

```bash
grep "ERROR" logfile.log | while read line; do
    echo "Error: $line"
done
```
#### What’s happening here

- `grep "ERROR" logfile.log`
  - Finds all lines containing "ERROR"

- `|` (pipe)
  - Sends output line by line to the loop

- `while read line`
  - Reads each matching line

- Inside loop:
  - You process each line

---

## Summary

- `for` → iterate over list or range
- `while` → run while the condition is true
- `until` → run until the condition becomes true
- `break` → exit loop
- `continue` → skip iteration
- Loop files using `*.log`
- Process output using `while read`

---

# 🐧 Bash – Functions

---

## Defining a Function

```bash
function_name() {
    # commands
}
```

### Example:

```bash
greet() {
    echo "Hello World"
}
```

---

## Calling a Function

- Use the function name (no parentheses)

```bash
greet
```

---

## Passing Arguments to Functions

```bash
function_name() {
    echo "First arg: $1"
    echo "Second arg: $2"
}
```
- `$1`, `$2` work the same as script arguments
  
### Example:

```bash
greet() {
    echo "Hello $1"
}

greet Sarthak
```

---

## Return Values (`return` vs `echo`)

### Using `return` (numeric only):

- Used for exit status (0–255)

```bash
add() {
    return 5
}

add
echo $?
```
**What’s happening**

- `return 5` → sets the exit status of the function
- `$?` → gives you the last command’s exit status

```bash
Output:
5
```
### Important Rules

- Only numbers allowed: 0–255
- Used like:
    - 0 → success 
    - non-zero → failure 

---

### Using `echo` (for actual values):

```bash
add() {
    echo $(( $1 + $2 ))
}

result=$(add 2 3)
echo "$result"
```

**What’s happening**
- `echo` prints output
- `$(...)` captures that output into a variable
```
Output:
5
```
- Preferred for returning data

---

## Local Variables

```bash
my_func() {
    local var="Hello"
    echo "$var"
}
```

- `local` restricts variable to function scope

---

# Summary

- Define → `name() {}`
- Call → just `name`
- Arguments → `$1`, `$2`
- `return` → status code
- `echo` → actual output
- `local` → function-only variable

---

# 🐧 Bash – Text Processing Commands

---

## grep

- It is used to search patterns. It scans files or command output and shows matching lines.

### Search pattern →
```bash
grep "ERROR" file.log
```
- Shows all lines containing "ERROR"

### Case-insensitive →
```bash
grep -i "error" file.log
```
- **Matches:**
   - ERROR
   - error
   - Error
     
### Recursive →
```bash
grep -r "ERROR" logs/
```
- **Searches inside:**
  - all files
  - all subdirectories
- Very useful when scanning log folders

### Count matches →
```bash
grep -c "ERROR" file.log
```
```bash
Output:
2
```
- Tells how many lines matched
 
### Line numbers →
```bash
grep -n "ERROR" file.log
```
```bash
Output:
2:ERROR: DB failed
```
- **Format:** `line_number:content`

### Invert match →
```bash
grep -v "INFO" file.log
```
- Shows everything **except lines with INFO**
 
### Multiple Patterns (Regex OR) →`
```bash
grep -E "ERROR|FAILED" file.log
```
- **Matches:**
    - ERROR
    - FAILED

---

## awk

- It can be used to filter the data column-wise.
- By default:
    - It splits each line by space
    - Each part becomes a column:
         - `$1` : First column
         - `$2` : Second column
         - `$3` : Third column
### Print columns →
```bash
awk '{print $1, $3}' file.txt
```
- Pronts only first and third column

### Custom delimiter → 
```bash
awk -F',' '{print $1}' file.csv
```
- `-F','` → split values from file which is having comma seprated values example: .csv file

### Pattern match → `awk '/ERROR/ {print}' file.log`
```bash
awk '/ERROR/ {print}' file.log
# It is same as grep
grep "ERROR" file.log
# but more powerful
awk '/ERROR/ {print $2}' file.log
```
- Print only specific column from matching lines

### BEGIN/END →
```bash
awk 'BEGIN{print "Start"} {print} END{print "End"}' file.txt
```
- **Meaning**
    - `BEGIN` : Before processing file
    - `{print}` : For each line
    - `END` : After processing

```bash
Output:
Start
(line1)
(line2)
...
End
```
---

## sed

- `sed` is a stream editor. It reads input (file or command output), modifies text, and prints the result.
- **syntax**: `sed 'operation' file`
  
### Replace → `sed 's/foo/bar/' file.txt`
- **Example: Simply replace text**
```bash
syntax:
sed 's/old/new/' file
```
- `s` → substitute
- `old` → text to find
- `new` → replace with

```bash
echo "hello world" | sed 's/world/devops/'
```
```bash
Output:
hello devops
```
- **Example: Replace Only First Match Per Line**
```bash
echo "one one" | sed 's/one/two/'
```
```bash
Output:
two one
```

### Global replace → `sed 's/foo/bar/g' file.txt`
- **Example: Replace All Matches (g flag)**
```bash
echo "one one" | sed 's/one/two/g'
```
```
Output:
two two
```
### Delete line → `sed '3d' file.txt`
- **Example: Delete Lines**
```bash
syntax:
sed '/pattern/d' file
```
```bash
sed '/ERROR/d' logfile.log
```
- Removes all lines containing "ERROR"


### In-place edit → `sed -i 's/foo/bar/g' file.txt`
- **Example: Editing Files (In-place)**
```bash
syntax:
sed -i 's/old/new/g' file.txt
```
- Modifies the file directly
```bash
sed -i 's/localhost/127.0.0.1/g' config.txt
```
### Some more examples:

- **Example: Print Specific Lines**
```bash
sed -n '2p' file.txt
```
- Prints only line 2
- **Range:**
```bash
sed -n '1,3p' file.txt
```
- Prints lines 1 to 3

- **Example: Use with Pipes**
```bash
grep "ERROR" logfile.log | sed 's/ERROR/ALERT/'
```
- Replace ERROR → ALERT in output

---

## cut
- `cut` is like the simplest version of awk when you just want to grab specific columns quickly
- `cut` = extract specific parts of text (columns/fields)
- **syntax**
   ```bash
   cut -d'<delimiter>' -f<fields> file
   ```
   - `-d	delimiter` (how columns are separated)
   - `-f` field number(s)
  
### Extract single column →
```bash
cut -d',' -f1 file.csv
```
- Extracts first column

### Extracts multiple fields →
```bash
cut -d',' -f1,3 file.csv
```
- Extracts column 1 and 3

### Extract Range of Fields
```bash
cut -d' ' -f4- sample_log.log
```
- **Means:**
   - Start from 4th column
   - Go till end

### Use with Pipes
```bash
echo "user:admin:1234" | cut -d':' -f1
```
```bash
Output:
user
```
---

## sort
- arranges lines in order
  
### Alphabetical → 
```bash
sort file.txt
```
- Sorts line A-Z

### Numerical (-n) →
```bash
sort -n file.txt
```
- Sorts numbers properly (not like text)
- Example
```bash
10
2
1
# Without -n:
1
10
2
# With -n:
1
2
10
```
### Reverse (-r) →
```bash
sort -r file.txt
```
- Z → A (or largest → smallest)

### Unique (-u) →
```bash
sort -u file.txt
```
- Sorts + removes duplicates

---

## uniq
- `uniq` = remove or count duplicate lines
- uniq only works on adjacent (consecutive) duplicates, So usually you must use sort before uniq

### Remove duplicates →
- Example (Wrong case)
```bash
file.txt` contains
apple
banana
apple
```
```bash
uniq file.txt
```
```bash
Output
apple
banana
apple
```
- Not removed because duplicates are not together
- Example (Correct way)
```bash
sort file.txt | uniq
```
```bash
Output:
apple
banana
```

### Count duplicates → 
- Example
```bash
file.txt contains
apple
banana
apple
apple
```
```bash
sort file.txt | uniq -c
```
```bash
Output:
3 apple
1 banana
```

---

## tr
- Replace or remove characters in a stream
- `tr` works on standard input (stdin)
  - So you usually use it with:  `pipes |` or `input redirection <`

### Replace chars →
```bash
tr 'a-z' 'A-Z' < file.txt
```
- Converts lowercase → uppercase

### Delete chars (-d) →
```bash
tr -d 'a' < file.txt
```
- Removes all `a` characters

---

## wc
- `wc` = word count, but it actually counts lines `-l` , words `-w`, characters `-c`
### Line count (-l) →
```bash
wc -l file.txt
```
- Counts number of lines

### Word count (-w) → 
```bash
wc -w file.txt
```
- Count number of words

### Char count (-c) →
```bash
wc -c file.txt
```
- counts characters 

### Default behavior
```bash
wc file.txt
```
- Output format: ` lines words characters filename`

---

## head / tail

### First N lines →
```bash
head -5 file.txt
```
- Shows first 5 Lines of the file

### Last N lines → 
```bash
tail -5 file.txt
```
- Shows last 5 lines of the file

### Follow file (-f) →
```bash
tail -f file.log
```
- Keeps watching the file and shows new lines as they are added

---

# Summary

- `grep` → search logs
- `awk` → extract/process data
- `sed` → modify text
- `cut` → pick columns
- `sort`, `uniq` → group/count
- `tr` → transform text
- `wc` → count data
- `head/tail` → preview logs

---

# 🐧 Bash – Useful Patterns & One-Liners

---

## Delete files older than N days

```bash
find /path/to/dir -type f -mtime +7 -delete
```
- Deletes files older than 7 days

---

## Count lines in all `.log` files

```bash
wc -l *.log
```
- Shows line count for each log file
- Total:

```bash
wc -l *.log | tail -1
```

---

## Replace string across multiple files

```bash
sed -i 's/old_text/new_text/g' *.txt
```
- Replaces text in all `.txt` files

---

## Check if a service is running

```bash
ps aux | grep -i nginx | grep -v grep
```
- Shows process if running
- Better (systemd):

```bash
systemctl is-active nginx
```

---

## Monitor disk usage with alert

```bash
df -h | awk '$5 > 80 {print "High usage on", $1}'
```
- Alerts if usage > 80%

---

## Tail log and filter errors (real-time)

```bash
tail -f app.log | grep --line-buffered "ERROR"
```
- Live error monitoring

---

## Find large files (>100MB)

```bash
find . -type f -size +100M
```
- Helps identify disk hogs

---

## Count occurrences of a pattern

```bash
grep -o "ERROR" app.log | wc -l
```
- Counts total matches (not lines)

---

## Parse CSV (print column)

```bash
awk -F',' '{print $1}' file.csv
```
- Extracts first column

---

## Parse JSON (using jq)

```bash
jq '.name' file.json
```
- Extracts `name` field

- Example:

```bash
echo '{"name":"Sarthak"}' | jq '.name'
```

---

## Check open ports

```bash
ss -tuln
```
- Lists listening ports

---

## Find failed SSH login attempts

```bash
grep "Failed password" /var/log/auth.log
```
- Security monitoring

---

# Summary

- `find` → file cleanup
- `wc`, `grep` → counting
- `sed` → bulk replace
- `ps`, `systemctl` → service check
- `df`, `awk` → monitoring
- `tail -f` → real-time logs
- `jq` → JSON parsing

---

# 🐧 Bash – Error Handling & Debugging

---

## Exit Codes
- Every command in Linux returns a status code after execution.

### `$?` → last command status
```bash
ls file.txt
echo $?
```
- `$?` = exit code of the last executed command

### `0` → success
```bash
ls /etc/passwd
echo $?
```
```bash
Output:
0
```
- `0` means success

### non-zero → error
```bash
ls nofile.txt
echo $?
```
```
Output:
2
```
- Non-zero means error

### Custom exit:

```bash
exit 0   # success
exit 1   # failure
```

---

## set -e (Exit on Error)

```bash
set -e
```
- Script stops immediately if any command fails

### Example:

```bash
set -e
cp file.txt /invalid/path   # script exits here
echo "This won't run"
```

---

## set -u (Unset Variables as Error)

```bash
set -u
```
- Using undefined variable will cause error

### Example:

```bash
set -u
echo "$NAME"   # error if NAME not set
```

---

## set -o pipefail

```bash
set -o pipefail
```
- Detects failure in pipelines

### Example:

```bash
set -o pipefail
grep "ERROR" file.log | sort
```
- If `grep` fails, script detects it (not just last command)

---

## set -x (Debug Mode)

```bash
set -x
```
- Prints each command before execution

### Example:

```bash
set -x
echo "Hello"
ls file.txt
```
- Output shows commands + results

---

## trap (Cleanup on Exit)

```bash
trap 'commands' EXIT
```
- Runs commands when script exits

### Example:

```bash
cleanup() {
    echo "Cleaning up..."
}

trap cleanup EXIT

echo "Running script..."
```
- `cleanup` runs automatically when script ends

---

# Summary

- `$?` → check status
- `exit` → stop script
- `set -e` → fail fast
- `set -u` → catch undefined vars
- `set -o pipefail` → detect pipeline errors
- `set -x` → debug mode
- `trap` → run cleanup on exit

---

































