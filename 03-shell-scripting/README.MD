# 03-Shell Scripting

## 📋 Overview

Welcome to the **Shell Scripting** module! Shell scripting is the art of automation in Linux environments. As a DevOps engineer, you'll write scripts to automate repetitive tasks, deploy applications, manage infrastructure, and much more. This module will take you from basic scripts to advanced automation techniques.

### 🎯 Module Objectives

By the end of this module, you will:

- ✅ Master Bash scripting fundamentals
- ✅ Write robust, error-handling scripts
- ✅ Create reusable functions and modules
- ✅ Automate system administration tasks
- ✅ Build DevOps automation tools
- ✅ Implement best practices and security patterns

## 📚 Learning Path

### Day-by-Day Breakdown

| Day | Topic | Focus Area | Status | Estimated Time |
|-----|-------|------------|--------|----------------|
| 1 | [Shell Basics](days/day-01-shell-basics.md) | Syntax, variables, I/O | 🔴 | 6-8 hours |
| 2 | [Conditions & Loops](days/day-02-conditions-loops.md) | Control structures | 🔴 | 6-8 hours |
| 3 | [Functions](days/day-03-functions.md) | Modular programming | 🔴 | 6-8 hours |
| 4 | [Automation](days/day-04-automation.md) | Real-world automation | 🔴 | 6-8 hours |

**Total Module Time**: 24-32 hours  
**Legend**: 🔴 Not Started | 🟡 In Progress | 🟢 Completed

## 🎓 Core Concepts

### What is Shell Scripting?

**Shell Script**: A text file containing a series of commands that the shell can execute. Think of it as programming for system administration.

**Common Shells**:
- **Bash** (Bourne Again Shell) - Most popular, default on most Linux systems
- **Zsh** (Z Shell) - Feature-rich, default on macOS
- **Sh** (Bourne Shell) - Original Unix shell, POSIX compliant
- **Fish** (Friendly Interactive Shell) - User-friendly

### Basic Script Structure

```bash
#!/bin/bash
# This is the shebang - tells system which interpreter to use
# This is a comment

# Script metadata
# Author: Your Name
# Date: 2026-01-07
# Description: What this script does

# Script content goes here
echo "Hello, DevOps World!"
```

### Script Execution

```bash
# Method 1: Make executable and run
chmod +x script.sh
./script.sh

# Method 2: Run with bash
bash script.sh

# Method 3: Source the script (runs in current shell)
source script.sh
# or
. script.sh
```

## 📖 Detailed Topics

### Day 1: Shell Basics

**What You'll Learn**:
- Script structure and shebang
- Variables (local, global, environment)
- Command substitution
- Input/Output
- Special variables ($0, $1, $@, $#, $?, $$)
- String operations
- Arrays

**Variables**:
```bash
#!/bin/bash

# Variable assignment (no spaces around =)
NAME="DevOps"
COUNT=10

# Using variables
echo "Hello, $NAME!"
echo "Count: ${COUNT}"

# Read-only variables
readonly VERSION="1.0"

# Environment variables
export PATH="$PATH:/new/path"
echo $HOME
echo $USER
echo $PWD

# Command substitution
CURRENT_DATE=$(date +%Y-%m-%d)
FILES=$(ls -1 | wc -l)
echo "Date: $CURRENT_DATE"
echo "Files: $FILES"

# User input
read -p "Enter your name: " username
echo "Hello, $username!"

# Read with timeout
read -t 5 -p "Quick! Enter something: " response
```

**Special Variables**:
```bash
#!/bin/bash

# $0 - Script name
echo "Script name: $0"

# $1, $2, ... - Positional parameters
echo "First argument: $1"
echo "Second argument: $2"

# $@ - All arguments as separate strings
echo "All arguments: $@"

# $# - Number of arguments
echo "Number of arguments: $#"

# $? - Exit status of last command
ls /nonexistent 2>/dev/null
echo "Exit status: $?"  # Will be non-zero

# $$ - Current process ID
echo "PID: $$"

# $! - PID of last background process
sleep 10 &
echo "Background PID: $!"
```

**Arrays**:
```bash
#!/bin/bash

# Declare array
declare -a fruits=("apple" "banana" "orange")

# Or simply
servers=("web1" "web2" "db1")

# Access elements
echo "First fruit: ${fruits[0]}"
echo "All fruits: ${fruits[@]}"
echo "Number of fruits: ${#fruits[@]}"

# Loop through array
for fruit in "${fruits[@]}"; do
    echo "Fruit: $fruit"
done

# Add to array
fruits+=("grape")

# Associative arrays (Bash 4+)
declare -A config
config[host]="localhost"
config[port]=3306
config[user]="admin"

echo "Host: ${config[host]}"
```

### Day 2: Conditions & Loops

**What You'll Learn**:
- if/elif/else statements
- case statements
- Test operators (file, string, numeric)
- for loops
- while loops
- until loops
- Loop control (break, continue)

**If Statements**:
```bash
#!/bin/bash

# Basic if statement
if [ "$USER" = "root" ]; then
    echo "Running as root"
fi

# If-else
if [ $# -eq 0 ]; then
    echo "No arguments provided"
else
    echo "Arguments: $@"
fi

# If-elif-else
SCORE=85

if [ $SCORE -ge 90 ]; then
    echo "Grade: A"
elif [ $SCORE -ge 80 ]; then
    echo "Grade: B"
elif [ $SCORE -ge 70 ]; then
    echo "Grade: C"
else
    echo "Grade: F"
fi

# Modern syntax [[ ]] (recommended)
if [[ $USER == "root" ]]; then
    echo "Root user detected"
fi

# Logical operators
if [[ $USER == "admin" ]] && [[ -f /tmp/flag ]]; then
    echo "Admin with flag file"
fi

if [[ $COUNT -gt 10 ]] || [[ $FORCE == "yes" ]]; then
    echo "Proceeding..."
fi
```

**Test Operators**:
```bash
#!/bin/bash

# File tests
[[ -f file.txt ]]      # File exists and is regular file
[[ -d /path ]]         # Directory exists
[[ -e file ]]          # File exists (any type)
[[ -r file ]]          # File is readable
[[ -w file ]]          # File is writable
[[ -x file ]]          # File is executable
[[ -s file ]]          # File exists and not empty
[[ file1 -nt file2 ]]  # file1 newer than file2
[[ file1 -ot file2 ]]  # file1 older than file2

# String tests
[[ -z $string ]]       # String is empty
[[ -n $string ]]       # String is not empty
[[ $str1 == $str2 ]]   # Strings are equal
[[ $str1 != $str2 ]]   # Strings are not equal
[[ $str1 < $str2 ]]    # Lexicographic comparison

# Numeric tests
[[ $a -eq $b ]]        # Equal
[[ $a -ne $b ]]        # Not equal
[[ $a -lt $b ]]        # Less than
[[ $a -le $b ]]        # Less than or equal
[[ $a -gt $b ]]        # Greater than
[[ $a -ge $b ]]        # Greater than or equal

# Example usage
if [[ -f /etc/nginx/nginx.conf ]]; then
    echo "Nginx config found"
    if [[ -r /etc/nginx/nginx.conf ]]; then
        echo "Config is readable"
    fi
fi
```

**Case Statements**:
```bash
#!/bin/bash

read -p "Enter command (start|stop|restart|status): " CMD

case $CMD in
    start)
        echo "Starting service..."
        ;;
    stop)
        echo "Stopping service..."
        ;;
    restart)
        echo "Restarting service..."
        ;;
    status)
        echo "Checking status..."
        ;;
    *)
        echo "Invalid command: $CMD"
        echo "Usage: $0 {start|stop|restart|status}"
        exit 1
        ;;
esac
```

**Loops**:
```bash
#!/bin/bash

# For loop - range
for i in {1..5}; do
    echo "Number: $i"
done

# For loop - array
SERVERS=("web1" "web2" "db1")
for server in "${SERVERS[@]}"; do
    echo "Checking $server..."
    ping -c 1 $server > /dev/null 2>&1
    if [ $? -eq 0 ]; then
        echo "  ✓ $server is up"
    else
        echo "  ✗ $server is down"
    fi
done

# For loop - C-style
for ((i=0; i<10; i++)); do
    echo "Iteration $i"
done

# For loop - files
for file in *.txt; do
    echo "Processing $file"
done

# While loop
COUNT=0
while [ $COUNT -lt 5 ]; do
    echo "Count: $COUNT"
    ((COUNT++))
done

# While reading file
while IFS= read -r line; do
    echo "Line: $line"
done < input.txt

# Until loop
COUNTER=0
until [ $COUNTER -ge 5 ]; do
    echo "Counter: $COUNTER"
    ((COUNTER++))
done

# Break and continue
for i in {1..10}; do
    if [ $i -eq 5 ]; then
        continue  # Skip 5
    fi
    if [ $i -eq 8 ]; then
        break     # Stop at 8
    fi
    echo "Number: $i"
done
```

### Day 3: Functions

**What You'll Learn**:
- Function declaration and calling
- Function parameters
- Return values and exit codes
- Local vs global variables
- Function libraries
- Recursive functions

**Basic Functions**:
```bash
#!/bin/bash

# Simple function
greet() {
    echo "Hello, World!"
}

# Call function
greet

# Function with parameters
greet_user() {
    local name=$1  # local variable
    local age=$2
    echo "Hello, $name! You are $age years old."
}

greet_user "Alice" 30

# Function with return value
add_numbers() {
    local sum=$(($1 + $2))
    echo $sum  # Echo acts as return value
}

result=$(add_numbers 5 10)
echo "Sum: $result"

# Function with exit code
check_file() {
    if [[ -f $1 ]]; then
        return 0  # Success
    else
        return 1  # Failure
    fi
}

if check_file "/etc/passwd"; then
    echo "File exists"
else
    echo "File not found"
fi
```

**Advanced Functions**:
```bash
#!/bin/bash

# Function with validation
backup_file() {
    local source=$1
    local dest=$2
    
    # Validate parameters
    if [[ $# -ne 2 ]]; then
        echo "Error: Usage: backup_file <source> <dest>"
        return 1
    fi
    
    if [[ ! -f $source ]]; then
        echo "Error: Source file does not exist: $source"
        return 1
    fi
    
    # Perform backup
    cp "$source" "$dest"
    if [[ $? -eq 0 ]]; then
        echo "Backup successful: $source -> $dest"
        return 0
    else
        echo "Backup failed"
        return 1
    fi
}

# Function library pattern
source "./lib/common.sh"  # Include external functions

# Recursive function (factorial)
factorial() {
    local n=$1
    if [[ $n -le 1 ]]; then
        echo 1
    else
        local prev=$(factorial $((n-1)))
        echo $((n * prev))
    fi
}

result=$(factorial 5)
echo "5! = $result"
```

### Day 4: Automation

**What You'll Learn**:
- Real-world automation scenarios
- Error handling and logging
- Cron job scheduling
- Email notifications
- API interactions
- Deployment automation

**Error Handling**:
```bash
#!/bin/bash

# Exit on error
set -e  # Exit if any command fails
set -u  # Exit if undefined variable used
set -o pipefail  # Exit if any command in pipeline fails

# Combined
set -euo pipefail

# Error trap
error_handler() {
    echo "Error occurred in script at line: $1"
    exit 1
}

trap 'error_handler $LINENO' ERR

# Cleanup on exit
cleanup() {
    echo "Cleaning up..."
    rm -f /tmp/tempfile_$$
}

trap cleanup EXIT

# Try-catch pattern
if ! command_that_might_fail; then
    echo "Command failed, handling error..."
    # Recovery code here
fi
```

**Logging**:
```bash
#!/bin/bash

LOGFILE="/var/log/myscript.log"

# Logging function
log() {
    local level=$1
    shift
    local message=$@
    local timestamp=$(date '+%Y-%m-%d %H:%M:%S')
    echo "[$timestamp] [$level] $message" | tee -a "$LOGFILE"
}

log "INFO" "Script started"
log "ERROR" "Something went wrong"
log "SUCCESS" "Task completed"

# Redirect all output to log
exec 1> >(tee -a "$LOGFILE")
exec 2>&1
```

**Automation Examples**:
```bash
#!/bin/bash
# System Backup Script

BACKUP_DIR="/backup"
DATE=$(date +%Y%m%d_%H%M%S)
LOGFILE="/var/log/backup_$DATE.log"

# Logging function
log() {
    echo "[$(date '+%Y-%m-%d %H:%M:%S')] $1" | tee -a "$LOGFILE"
}

# Create backup
log "INFO: Starting backup"

if tar -czf "$BACKUP_DIR/backup_$DATE.tar.gz" /home /etc 2>>"$LOGFILE"; then
    log "SUCCESS: Backup completed"
    
    # Remove old backups (keep last 7 days)
    find "$BACKUP_DIR" -name "backup_*.tar.gz" -mtime +7 -delete
    log "INFO: Old backups cleaned"
    
    # Send notification
    echo "Backup completed successfully" | mail -s "Backup Status" admin@example.com
else
    log "ERROR: Backup failed"
    echo "Backup failed! Check logs: $LOGFILE" | mail -s "Backup FAILED" admin@example.com
    exit 1
fi
```

**Cron Job Setup**:
```bash
# Edit crontab
crontab -e

# Schedule examples:

# Every day at 2 AM
0 2 * * * /path/to/backup.sh

# Every Monday at 3 AM
0 3 * * 1 /path/to/weekly_task.sh

# Every 15 minutes
*/15 * * * * /path/to/monitor.sh

# First day of every month at midnight
0 0 1 * * /path/to/monthly_report.sh

# Cron format:
# ┌───────────── minute (0 - 59)
# │ ┌───────────── hour (0 - 23)
# │ │ ┌───────────── day of month (1 - 31)
# │ │ │ ┌───────────── month (1 - 12)
# │ │ │ │ ┌───────────── day of week (0 - 6) (Sunday=0)
# │ │ │ │ │
# * * * * * command to execute
```

## 🚀 Projects

### [Automation Scripts Collection](projects/automation-scripts/)

**Project Ideas**:

1. **System Monitoring Dashboard**
   - CPU, Memory, Disk usage
   - Service status checks
   - Alert on thresholds
   - HTML report generation

2. **Automated Backup Solution**
   - Database backups
   - File system backups
   - Cloud upload (S3, etc.)
   - Retention policy
   - Email notifications

3. **Deployment Automation**
   - Git pull/clone
   - Build application
   - Run tests
   - Deploy to server
   - Rollback on failure

4. **Log Analyzer**
   - Parse log files
   - Extract errors/warnings
   - Generate statistics
   - Create reports

5. **Server Health Check**
   - Multi-server monitoring
   - SSH connectivity check
   - Service availability
   - Port scanning
   - Status dashboard

## 📊 Best Practices

### Script Organization
```bash
#!/bin/bash
################################################################################
# Script Name: backup.sh
# Description: Automated backup script with rotation
# Author: Your Name
# Date: 2026-01-07
# Version: 1.0
################################################################################

# Exit on error
set -euo pipefail

# Configuration
readonly SCRIPT_DIR="$(cd "$(dirname "${BASH_SOURCE[0]}")" && pwd)"
readonly BACKUP_DIR="/backup"
readonly LOG_FILE="/var/log/backup.log"

# Functions
log() { echo "[$(date +'%Y-%m-%d %H:%M:%S')] $*" | tee -a "$LOG_FILE"; }
error() { log "ERROR: $*"; exit 1; }

# Main script
main() {
    log "Starting backup process"
    # Script logic here
}

# Execute
main "$@"
```

### Security Best Practices
```bash
# Use full paths
/usr/bin/rm instead of rm

# Validate user input
if [[ ! "$input" =~ ^[a-zA-Z0-9_]+$ ]]; then
    echo "Invalid input"
    exit 1
fi

# Avoid eval
# Bad:
eval "$user_input"
# Good:
# Validate and sanitize input first

# Use quotes around variables
rm "$file"  # Good
rm $file    # Bad - breaks with spaces

# Store sensitive data securely
# Don't hardcode passwords
# Use environment variables or secret managers
DB_PASS="${DB_PASS:-$(cat /secure/db_password)}"
```

### Error Handling
```bash
#!/bin/bash

# Check if command exists
command -v docker >/dev/null 2>&1 || {
    echo "Docker is required but not installed. Exiting."
    exit 1
}

# Check if running as root
if [[ $EUID -ne 0 ]]; then
   echo "This script must be run as root"
   exit 1
fi

# Validate number of arguments
if [[ $# -lt 2 ]]; then
    echo "Usage: $0 <source> <destination>"
    exit 1
fi

# Check if file exists before processing
if [[ ! -f "$config_file" ]]; then
    echo "Config file not found: $config_file"
    exit 1
fi
```

## 📚 Learning Resources

### Official Documentation
- [Bash Manual](https://www.gnu.org/software/bash/manual/)
- [Advanced Bash-Scripting Guide](https://tldp.org/LDP/abs/html/)
- [ShellCheck](https://www.shellcheck.net/) - Script analyzer

### Practice Platforms
- [HackerRank Shell](https://www.hackerrank.com/domains/shell)
- [Exercism Bash Track](https://exercism.org/tracks/bash)

### Tools
- **ShellCheck**: Static analysis for shell scripts
- **Bashate**: Style checker
- **shfmt**: Shell script formatter

### Books
- "Learning the bash Shell" by Cameron Newham
- "Bash Cookbook" by Carl Albing
- "Wicked Cool Shell Scripts" by Dave Taylor

### Video Courses
- Udemy: Bash Scripting and Shell Programming
- Linux Academy: Shell Scripting Fundamentals
- YouTube: Learn Linux TV

## 📊 Assessment Checklist

After completing this module, you should be able to:

### Basic Skills
- [ ] Write executable shell scripts
- [ ] Use variables and command substitution
- [ ] Handle user input
- [ ] Work with arrays

### Control Structures
- [ ] Implement if/elif/else logic
- [ ] Use case statements
- [ ] Write for, while, until loops
- [ ] Apply test operators correctly

### Functions
- [ ] Create and call functions
- [ ] Pass parameters to functions
- [ ] Return values from functions
- [ ] Use local and global variables

### Automation
- [ ] Implement error handling
- [ ] Add logging to scripts
- [ ] Schedule tasks with cron
- [ ] Create production-ready scripts

### Best Practices
- [ ] Follow naming conventions
- [ ] Add proper comments and documentation
- [ ] Handle errors gracefully
- [ ] Validate user input
- [ ] Write secure scripts

## 🔄 Next Steps

After completing this module:

1. ✅ Complete all 4 days of learning
2. ✅ Build automation scripts project
3. ✅ Document learnings in [learnings.md](learnings.md)
4. ✅ Contribute scripts to personal GitHub
5. ✅ Move to **04-Networking** module

## 📌 Important Notes

> **💡 Pro Tip**: Start with simple scripts and gradually add complexity. Test each component before moving on.

> **⚠️ Warning**: Always test scripts in a safe environment before running in production. One wrong command can cause serious damage.

> **🎯 Goal**: Automate anything you do more than twice. If you're repeating manual steps, script it!

### Quick Reference Card
```bash
# Variables
VAR="value"
$VAR or ${VAR}

# Conditions
if [[ condition ]]; then ... fi

# Loops
for i in {1..10}; do ... done
while [[ condition ]]; do ... done

# Functions
function_name() { ... }

# Useful operators
-f  file exists
-d  directory exists
-z  string is empty
-eq numeric equal
==  string equal
```

## 📈 Progress Tracking

| Day | Topic | Status | Completion Date | Scripts Written |
|-----|-------|--------|-----------------|------------------|
| 1 | Shell Basics | 🔴 | - | 0 |
| 2 | Conditions & Loops | 🔴 | - | 0 |
| 3 | Functions | 🔴 | - | 0 |
| 4 | Automation | 🔴 | - | 0 |

**Module Completion**: 0%  
**Scripts Written**: 0/10 target

---

## 📂 Module Structure

```
03-shell-scripting/
├── README.md                           # This file
├── days/                               # Day-wise learning
│   ├── day-01-shell-basics.md
│   ├── day-02-conditions-loops.md
│   ├── day-03-functions.md
│   └── day-04-automation.md
├── projects/                           # Projects
│   └── automation-scripts/
│       └── README.md
├── handwritten-notes/                  # Handwritten notes (PDFs)
└── learnings.md                        # Personal insights
```

---

<div align="center">

### 🔧 Automate Everything!

**"A good programmer is someone who always looks both ways before crossing a one-way street."** - Doug Linder

[Start Day 1 →](days/day-01-shell-basics.md)

</div>

---

**Last Updated**: January 2026  
**Difficulty**: Beginner to Intermediate  
**Prerequisites**: Linux basics, command line comfort  
**Estimated Time**: 24-32 hours