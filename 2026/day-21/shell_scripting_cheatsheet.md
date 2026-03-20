# Shell Scripting Cheat Sheet

---

## Quick Reference

| Topic | Syntax | Example |
|------|--------|--------|
| Variable | VAR="value" | NAME="Sarthak" |
| Argument | $1, $2 | ./script.sh file |
| If | if [ condition ]; then | if [ -f file ]; then |
| Loop | for i in list; do | for i in 1 2 3; do |
| Function | name() { } | greet() { echo hi; } |
| Grep | grep pattern file | grep "error" log.txt |



---

## 🐧 Bash Basics 

## Shebang (`#!/bin/bash`)

- Defines which interpreter should run the script.

```bash
#!/bin/bash
echo "Hello World"
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
- Comments are ignored by Bash

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

- Takes input from user and stores in variable

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

- `$?` - Checks chekcs command success
```bash
ls file.txt
echo $?
```

- `0` → success
- non-zero → error

---

# Summary

* Shebang defines interpreter
* Scripts run via `./` or `bash`
* Variables store data
* `read` takes user input
* `$1`, `$@`, `$#` handle arguments
* `$?` checks command success

---

# 🐧 Bash – Operators and Conditionals

## 🔹 String Comparisons

```bash
[ "$a" = "$b" ]    # equal
[ "$a" != "$b" ]   # not equal
[ -z "$a" ]        # string is empty
[ -n "$a" ]        # string is not empty
```

### Example:

```bash
name="Sarthak"

if [ "$name" = "Sarthak" ]; then
    echo "Match found"
fi
```

---

## 🔹 Integer Comparisons

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

## 🔹 File Test Operators

```bash
[ -f file.txt ]   # file exists and is regular file
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
    echo "File exists"
fi
```

---

## 🔹 if, elif, else Syntax

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

## 🔹 Logical Operators

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

## 🔹 Case Statements

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

---

# 🚀 Summary

* Use `[ ]` for conditions
* Strings → `=`, `!=`, `-z`, `-n`
* Numbers → `-eq`, `-gt`, etc.
* Files → `-f`, `-d`, etc.
* Combine conditions using `&&`, `||`, `!`
* Use `case` for multiple conditions

---
