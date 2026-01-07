# 02-Linux

## 📋 Overview

Welcome to the **Linux** module! This section covers everything you need to become proficient with Linux systems—the backbone of DevOps infrastructure. Linux powers most servers, containers, and cloud instances, making it an essential skill for any DevOps engineer.

### 🎯 Module Objectives

By the end of this module, you will:

- ✅ Master Linux command-line interface (CLI)
- ✅ Understand Linux file system hierarchy and permissions
- ✅ Manage processes, services, and system resources
- ✅ Configure networking in Linux environments
- ✅ Troubleshoot and debug system issues
- ✅ Automate tasks using shell commands

## 📚 Learning Path

### Day-by-Day Breakdown

| Day | Topic | Focus Area | Status | Estimated Time |
|-----|-------|------------|--------|----------------|
| 1 | [Linux Basics](days/day-01-linux-basics.md) | CLI navigation, file operations | 🔴 | 4-6 hours |
| 2 | [Files & Permissions](days/day-02-files-permissions.md) | chmod, chown, ACLs | 🔴 | 4-6 hours |
| 3 | [Processes & Services](days/day-03-processes-services.md) | systemd, process management | 🔴 | 4-6 hours |
| 4 | [Networking](days/day-04-networking.md) | Network config, troubleshooting | 🔴 | 4-6 hours |
| 5 | [Logs & Debugging](days/day-05-logs-debugging.md) | System logs, debugging tools | 🔴 | 4-6 hours |
| 6 | [Revision](days/day-06-revision.md) | Practice & consolidation | 🔴 | 4-6 hours |

**Total Module Time**: 24-36 hours  
**Legend**: 🔴 Not Started | 🟡 In Progress | 🟢 Completed

## 🎓 Core Concepts

### Linux File System Hierarchy

```
/                    # Root directory
├── /bin             # Essential user binaries
├── /boot            # Boot loader files
├── /dev             # Device files
├── /etc             # System configuration files
├── /home            # User home directories
├── /lib             # System libraries
├── /media           # Removable media mount points
├── /mnt             # Temporary mount points
├── /opt             # Optional software
├── /proc            # Process information
├── /root            # Root user home directory
├── /sbin            # System binaries
├── /srv             # Service data
├── /tmp             # Temporary files
├── /usr             # User programs
└── /var             # Variable data (logs, cache)
```

### Permission Model

```
-rwxr-xr--
│││││││││└─ Other permissions (r--)
││││││└└└─ Group permissions (r-x)
│││└└└───── Owner permissions (rwx)
│└└─────── File type (- = file, d = directory, l = link)

Permission Values:
r (read)    = 4
w (write)   = 2
x (execute) = 1

Examples:
755 = rwxr-xr-x (Owner: full, Group: read+execute, Other: read+execute)
644 = rw-r--r-- (Owner: read+write, Group: read, Other: read)
600 = rw------- (Owner: read+write, Group: none, Other: none)
```

## 📖 Detailed Topics

### Day 1: Linux Basics
**What You'll Learn**:
- Linux distributions (Ubuntu, CentOS, Debian, RHEL)
- Command-line interface fundamentals
- File system navigation (pwd, cd, ls)
- File operations (touch, cat, cp, mv, rm)
- Directory operations (mkdir, rmdir)
- Text viewing (cat, less, more, head, tail)
- Finding files (find, locate)

**Essential Commands**:
```bash
# Navigation
pwd                    # Print working directory
ls -la                # List all files with details
cd /path/to/dir       # Change directory
cd ..                 # Go up one level
cd ~                  # Go to home directory

# File operations
touch file.txt        # Create empty file
cp source dest        # Copy file
mv old new            # Move/rename file
rm file.txt           # Remove file
cat file.txt          # Display file content

# Directory operations
mkdir mydir           # Create directory
mkdir -p dir1/dir2    # Create nested directories
rmdir mydir           # Remove empty directory
rm -rf mydir          # Remove directory recursively
```

### Day 2: Files & Permissions
**What You'll Learn**:
- Understanding file permissions (read, write, execute)
- Changing permissions (chmod)
- Changing ownership (chown, chgrp)
- Special permissions (setuid, setgid, sticky bit)
- Access Control Lists (ACLs)
- umask and default permissions

**Essential Commands**:
```bash
# View permissions
ls -l file.txt
stat file.txt

# Change permissions
chmod 755 script.sh           # Numeric mode
chmod u+x script.sh           # Symbolic mode (user add execute)
chmod g-w file.txt            # Symbolic mode (group remove write)
chmod o=r file.txt            # Symbolic mode (other set to read only)

# Change ownership
chown user:group file.txt     # Change owner and group
chown user file.txt           # Change owner only
chgrp group file.txt          # Change group only
sudo chown -R user:group dir/ # Recursive ownership change

# Special permissions
chmod u+s file                # Set setuid
chmod g+s dir                 # Set setgid
chmod +t dir                  # Set sticky bit
```

### Day 3: Processes & Services
**What You'll Learn**:
- Process management and monitoring
- Background and foreground processes
- System services with systemd
- Process signals and killing processes
- System resource monitoring
- Cron jobs and scheduling

**Essential Commands**:
```bash
# Process viewing
ps aux                # List all processes
ps aux | grep nginx   # Find specific process
top                   # Interactive process viewer
htop                  # Enhanced top (if installed)

# Process management
kill PID              # Send SIGTERM to process
kill -9 PID           # Force kill (SIGKILL)
killall processname   # Kill by name
pkill pattern         # Kill by pattern

# Background/Foreground
command &             # Run in background
Ctrl+Z                # Suspend current process
bg                    # Resume in background
fg                    # Resume in foreground
jobs                  # List background jobs

# Systemd services
sudo systemctl start nginx      # Start service
sudo systemctl stop nginx       # Stop service
sudo systemctl restart nginx    # Restart service
sudo systemctl status nginx     # Check status
sudo systemctl enable nginx     # Enable at boot
sudo systemctl disable nginx    # Disable at boot

# Cron jobs
crontab -e            # Edit cron jobs
crontab -l            # List cron jobs
# Format: minute hour day month weekday command
# Example: 0 0 * * * /path/to/backup.sh  # Daily at midnight
```

### Day 4: Networking
**What You'll Learn**:
- Network configuration and interfaces
- IP addressing and routing
- Network troubleshooting tools
- Firewall basics (iptables, ufw)
- SSH configuration and usage
- Port management

**Essential Commands**:
```bash
# Network information
ip addr                    # Show IP addresses
ip link                    # Show network interfaces
ip route                   # Show routing table
ifconfig                   # Legacy network config (if available)

# Connectivity testing
ping google.com            # Test connectivity
ping -c 4 8.8.8.8         # Ping 4 times
traceroute google.com      # Trace route to host
mtr google.com             # Combined ping and traceroute

# Network services
netstat -tuln              # Show listening ports
ss -tuln                   # Modern replacement for netstat
lsof -i :80                # Show what's using port 80

# DNS
nslookup google.com        # DNS lookup
dig google.com             # Detailed DNS query
host google.com            # Simple DNS lookup

# Transfer and download
curl https://example.com   # Make HTTP request
wget https://example.com/file.tar.gz  # Download file
scp file.txt user@host:/path          # Secure copy to remote

# SSH
ssh user@hostname          # Connect to remote host
ssh -i key.pem user@host   # Connect with key
ssh -p 2222 user@host      # Connect on custom port

# Firewall (Ubuntu)
sudo ufw status            # Check firewall status
sudo ufw enable            # Enable firewall
sudo ufw allow 22          # Allow SSH
sudo ufw allow 80/tcp      # Allow HTTP
sudo ufw deny 23           # Deny Telnet
```

### Day 5: Logs & Debugging
**What You'll Learn**:
- System log locations and formats
- journalctl for systemd logs
- Log analysis and parsing
- Debugging techniques
- Performance monitoring

**Essential Commands**:
```bash
# System logs
sudo tail -f /var/log/syslog          # Follow system log
sudo tail -f /var/log/auth.log        # Follow auth log
sudo less /var/log/apache2/error.log  # View Apache errors

# Journalctl (systemd)
journalctl                     # View all logs
journalctl -u nginx            # Logs for specific service
journalctl -f                  # Follow logs (like tail -f)
journalctl --since "1 hour ago"  # Recent logs
journalctl -p err              # Only error messages
journalctl -b                  # Logs since last boot

# Log analysis
grep "error" /var/log/syslog   # Search for errors
grep -i "failed" /var/log/auth.log | wc -l  # Count failed attempts
awk '{print $5}' file.log      # Extract 5th column
sed 's/error/ERROR/g' file.log # Replace text

# System monitoring
dmesg                          # Kernel messages
vmstat 1                       # Virtual memory stats
iostat                         # I/O statistics
sar                            # System activity report
df -h                          # Disk usage (human readable)
du -sh /path                   # Directory size
free -h                        # Memory usage
```

### Day 6: Revision & Practice
- Review all commands and concepts
- Complete hands-on labs
- Work on mini-project
- Troubleshoot common issues
- Practice scenarios

## 🛠️ Hands-On Practice

### Practice Labs ([hands-on/labs.sh](hands-on/labs.sh))

1. **Lab 1: File Management**
   - Create directory structure
   - Create and manipulate files
   - Practice permissions

2. **Lab 2: User Management**
   - Create users and groups
   - Set up home directories
   - Configure sudo access

3. **Lab 3: Service Management**
   - Install and configure services
   - Manage service lifecycle
   - Debug service issues

4. **Lab 4: Network Configuration**
   - Configure network interfaces
   - Setup firewall rules
   - Troubleshoot connectivity

5. **Lab 5: Log Analysis**
   - Parse and analyze logs
   - Create log monitoring script
   - Set up log rotation

### Commands Reference
See [hands-on/commands.md](hands-on/commands.md) for comprehensive command reference.

## 🚀 Projects

### Mini Project: [Linux System Monitoring Tool](projects/linux-mini-project/)

**Objective**: Build a comprehensive system monitoring script

**Features**:
- CPU, Memory, and Disk usage monitoring
- Service health checks
- Log file analysis
- Automated alerts
- Report generation

**Technologies**:
- Bash scripting
- cron for scheduling
- System commands (top, df, free, ps)
- Log parsing (grep, awk, sed)

**Deliverables**:
- [ ] Monitoring script
- [ ] Alert mechanism
- [ ] HTML/text report generator
- [ ] Cron job setup
- [ ] Documentation

## 📊 Assessment Checklist

After completing this module, you should be able to:

### Basic Skills
- [ ] Navigate Linux file system confidently
- [ ] Create, edit, and delete files and directories
- [ ] Use text editors (nano, vim)
- [ ] Search for files and text patterns
- [ ] Redirect and pipe command output

### Permissions & Ownership
- [ ] Understand and modify file permissions
- [ ] Change file ownership
- [ ] Explain special permissions (setuid, setgid, sticky bit)
- [ ] Use umask effectively

### Process Management
- [ ] View and monitor processes
- [ ] Kill processes safely
- [ ] Run processes in background
- [ ] Manage system services
- [ ] Schedule tasks with cron

### Networking
- [ ] Configure network interfaces
- [ ] Troubleshoot connectivity issues
- [ ] Use SSH for remote access
- [ ] Configure basic firewall rules
- [ ] Understand common ports and protocols

### Troubleshooting
- [ ] Read and analyze system logs
- [ ] Debug service issues
- [ ] Monitor system resources
- [ ] Identify performance bottlenecks

## 💡 Best Practices

### Command Line Productivity
```bash
# Use tab completion
cd /var/log/<TAB>

# Command history
history               # View command history
!number               # Run command by history number
!string               # Run last command starting with string
Ctrl+R                # Reverse search history

# Aliases (add to ~/.bashrc)
alias ll='ls -la'
alias update='sudo apt update && sudo apt upgrade'
alias ports='netstat -tuln'

# Useful shortcuts
Ctrl+A                # Move to beginning of line
Ctrl+E                # Move to end of line
Ctrl+U                # Clear line before cursor
Ctrl+K                # Clear line after cursor
Ctrl+L                # Clear screen (like 'clear')
```

### Safety Tips
```bash
# Always double-check before running:
sudo rm -rf /path     # Recursive delete - be careful!
chmod -R 777 /path    # Makes everything writable - dangerous!

# Use these safer alternatives:
rm -i file            # Interactive delete (prompts)
cp -i source dest     # Interactive copy (prompts on overwrite)
mv -i source dest     # Interactive move

# Test commands first
find / -name "test" -print    # Test with -print
find / -name "test" -delete   # Then use -delete
```

## 📚 Learning Resources

### Official Documentation
- [Ubuntu Documentation](https://help.ubuntu.com/)
- [Red Hat Documentation](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/)
- [Linux Foundation](https://www.linuxfoundation.org/)

### Interactive Learning
- [Linux Journey](https://linuxjourney.com/) - Beginner-friendly
- [OverTheWire: Bandit](https://overthewire.org/wargames/bandit/) - Command line practice
- [Katacoda](https://www.katacoda.com/) - Interactive scenarios

### Books
- "The Linux Command Line" by William Shotts (Free PDF)
- "Linux Bible" by Christopher Negus
- "How Linux Works" by Brian Ward
- "UNIX and Linux System Administration Handbook" by Evi Nemeth

### Video Courses
- Linux Academy / A Cloud Guru
- Udemy: Linux Mastery
- YouTube: Learn Linux TV, NetworkChuck

### Cheat Sheets
- [Linux Command Line Cheat Sheet](https://cheatography.com/davechild/cheat-sheets/linux-command-line/)
- [Vi/Vim Cheat Sheet](https://vim.rtorr.com/)

## 🔄 Next Steps

After completing this module:

1. ✅ Complete all 6 days of learning
2. ✅ Finish the mini-project
3. ✅ Document learnings in [learnings.md](learnings.md)
4. ✅ Practice commands daily
5. ✅ Move to **03-Shell Scripting** module

## 📌 Important Notes

> **💡 Pro Tip**: The best way to learn Linux is to use it daily. Set up a Linux VM or use WSL on Windows.

> **⚠️ Warning**: Be careful with commands that modify the system, especially when using `sudo`. Always double-check before running destructive commands.

> **🎯 Focus**: Don't try to memorize every command. Learn the common ones and know how to find information using `man` pages and `--help`.

### Using Man Pages
```bash
man command           # View manual for command
man -k keyword        # Search man pages
command --help        # Quick help
info command          # Detailed info pages
```

## 🤔 Common Issues & Solutions

### Permission Denied
```bash
# Problem: Permission denied when running script
./script.sh
-bash: ./script.sh: Permission denied

# Solution: Add execute permission
chmod +x script.sh
./script.sh
```

### Command Not Found
```bash
# Problem: Command not found
ifconfig
bash: ifconfig: command not found

# Solution: Install package or use alternative
sudo apt install net-tools  # For ifconfig
ip addr                     # Modern alternative
```

### Disk Space Full
```bash
# Problem: No space left on device

# Solution: Find large files
du -sh /* | sort -rh | head -10
find / -type f -size +100M

# Clean up
sudo apt clean              # Clean package cache
sudo journalctl --vacuum-time=3d  # Clean old logs
```

## 📈 Progress Tracking

| Day | Topic | Status | Completion Date | Notes |
|-----|-------|--------|----------------|-------|
| 1 | Linux Basics | 🔴 | - | |
| 2 | Files & Permissions | 🔴 | - | |
| 3 | Processes & Services | 🔴 | - | |
| 4 | Networking | 🔴 | - | |
| 5 | Logs & Debugging | 🔴 | - | |
| 6 | Revision | 🔴 | - | |

**Module Completion**: 0%

---

## 📂 Module Structure

```
02-linux/
├── README.md                           # This file
├── days/                               # Day-wise learning
│   ├── day-01-linux-basics.md
│   ├── day-02-files-permissions.md
│   ├── day-03-processes-services.md
│   ├── day-04-networking.md
│   ├── day-05-logs-debugging.md
│   └── day-06-revision.md
├── hands-on/                           # Practice materials
│   ├── commands.md                     # Command reference
│   └── labs.sh                         # Lab scripts
├── projects/                           # Projects
│   └── linux-mini-project/
│       └── README.md
├── handwritten-notes/                  # Handwritten notes (PDFs)
└── learnings.md                        # Personal insights
```

---

<div align="center">

### 🐧 Master Linux, Master DevOps!

**"Linux is only free if your time has no value." - Jamie Zawinski**  
*(Just kidding, it's worth every minute!)*

[Start Day 1 →](days/day-01-linux-basics.md)

</div>

---

**Last Updated**: January 2026  
**Difficulty**: Beginner to Intermediate  
**Prerequisites**: Basic computer literacy  
**Estimated Time**: 24-36 hours