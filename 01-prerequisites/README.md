# 01-Prerequisites

## 📋 Overview

Welcome to the **Prerequisites** module! This section covers fundamental knowledge areas that are essential before diving deep into DevOps tools and practices. These foundational skills will be used throughout your entire DevOps journey.

### 🎯 Module Objectives

By the end of this module, you will have:

- ✅ Understanding of cloud computing fundamentals
- ✅ Proficiency in Git and version control workflows
- ✅ Solid foundation in Linux/Unix systems
- ✅ Networking basics for DevOps engineers
- ✅ Scripting fundamentals (Bash, Python basics)

## 📚 Learning Content

### Topics Overview

| # | Topic | Difficulty | Estimated Time | Status |
|---|-------|------------|----------------|--------|
| 1 | [Cloud Fundamentals](cloud-fundamentals.md) | Beginner | 4-6 hours | 🔴 |
| 2 | [Git & Version Control](git-version-control.md) | Beginner | 6-8 hours | 🔴 |
| 3 | [Linux Basics](linux-basics.md) | Beginner | 8-10 hours | 🔴 |
| 4 | [Networking Basics](networking-basics.md) | Beginner | 6-8 hours | 🔴 |
| 5 | [Scripting Basics](scripting-basics.md) | Beginner | 6-8 hours | 🔴 |

**Legend**: 🔴 Not Started | 🟡 In Progress | 🟢 Completed

## 🎓 Topic Breakdown

### 1. Cloud Fundamentals ([cloud-fundamentals.md](cloud-fundamentals.md))

**Why It Matters**: Modern DevOps is heavily cloud-centric. Understanding cloud concepts is crucial.

**What You'll Learn**:
- ☁️ Cloud computing models (IaaS, PaaS, SaaS)
- 🌐 Cloud deployment models (Public, Private, Hybrid)
- 🏢 Major cloud providers overview (AWS, Azure, GCP)
- 💰 Cloud economics and pricing models
- 🔒 Cloud security fundamentals
- 📊 Cloud service categories

**Key Concepts**:
```
IaaS (Infrastructure as a Service)
  └─ Virtual Machines, Storage, Networks
  
PaaS (Platform as a Service)
  └─ Development platforms, Databases
  
SaaS (Software as a Service)
  └─ Ready-to-use applications
```

### 2. Git & Version Control ([git-version-control.md](git-version-control.md))

**Why It Matters**: Git is the backbone of collaboration in DevOps. Every code change, configuration, and infrastructure definition uses version control.

**What You'll Learn**:
- 📝 Git basics and terminology
- 🔄 Git workflow (clone, add, commit, push, pull)
- 🌿 Branching and merging strategies
- 🔀 Pull requests and code reviews
- 🏷️ Tags and releases
- 🐙 GitHub/GitLab workflows
- 🔍 Git best practices

**Essential Commands**:
```bash
# Basic workflow
git init
git clone <repo-url>
git status
git add .
git commit -m "message"
git push origin main

# Branching
git branch feature-name
git checkout -b feature-name
git merge feature-name

# Collaboration
git pull
git fetch
git rebase
```

### 3. Linux Basics ([linux-basics.md](linux-basics.md))

**Why It Matters**: Most DevOps tools and servers run on Linux. You need to be comfortable with the command line.

**What You'll Learn**:
- 🐧 Linux distributions overview
- 📂 File system hierarchy
- 💻 Essential commands and navigation
- 📝 File manipulation and permissions
- 👤 User and group management
- 📦 Package management (apt, yum)
- 🔍 Finding and searching files
- 🖥️ Process management basics

**Must-Know Commands**:
```bash
# Navigation
ls, cd, pwd, mkdir, rmdir

# File operations
touch, cat, cp, mv, rm, nano, vim

# Permissions
chmod, chown, chgrp

# System info
uname, whoami, df, du, free, top

# Package management
apt-get, apt, yum, dnf
```

### 4. Networking Basics ([networking-basics.md](networking-basics.md))

**Why It Matters**: DevOps involves connecting systems, services, and users. Understanding networking is essential.

**What You'll Learn**:
- 🌐 OSI and TCP/IP models
- 📡 IP addressing and subnetting
- 🔌 Ports and protocols (HTTP, HTTPS, SSH, FTP)
- 🌍 DNS basics
- 🔒 Firewalls and security groups
- 🛣️ Routing fundamentals
- 🔍 Network troubleshooting commands

**Key Networking Commands**:
```bash
# Connectivity
ping, traceroute, curl, wget

# Network info
ifconfig, ip addr, netstat, ss

# DNS
nslookup, dig, host

# Port scanning
telnet, nc, nmap
```

### 5. Scripting Basics ([scripting-basics.md](scripting-basics.md))

**Why It Matters**: Automation is at the heart of DevOps. Scripting enables you to automate repetitive tasks.

**What You'll Learn**:
- 📜 Shell scripting fundamentals (Bash)
- 🔢 Variables and data types
- 🔄 Loops and conditionals
- 📥 Input/Output operations
- 🛠️ Functions and modularity
- 🐍 Python basics for DevOps
- ⚙️ Automation use cases

**Bash Script Example**:
```bash
#!/bin/bash
# Simple backup script

SOURCE="/home/user/data"
BACKUP="/backup"
DATE=$(date +%Y%m%d)

tar -czf $BACKUP/backup-$DATE.tar.gz $SOURCE
echo "Backup completed: backup-$DATE.tar.gz"
```

## 🛠️ Tools & Software

### Required Installations

1. **Git**
   - Download: [git-scm.com](https://git-scm.com/)
   - Verify: `git --version`

2. **Linux Environment**
   - Option 1: WSL (Windows Subsystem for Linux)
   - Option 2: Virtual Machine (VirtualBox/VMware)
   - Option 3: Cloud VM (AWS EC2, Azure VM)

3. **Text Editor**
   - VS Code (recommended)
   - Vim or Nano (terminal-based)

4. **Terminal Emulator**
   - Windows: PowerShell, Windows Terminal, Git Bash
   - Mac: iTerm2
   - Linux: Built-in terminal

### Online Practice Environments

- [Katacoda](https://www.katacoda.com/) - Interactive Linux and DevOps scenarios
- [Play with Docker](https://labs.play-with-docker.com/)
- [AWS Free Tier](https://aws.amazon.com/free/)
- [GitHub](https://github.com/) - Free repositories

## 📊 Assessment Checklist

After completing this module, you should be able to:

### Cloud Fundamentals
- [ ] Explain IaaS, PaaS, and SaaS with examples
- [ ] Identify use cases for different cloud models
- [ ] Understand cloud pricing and cost optimization

### Git & Version Control
- [ ] Initialize and clone repositories
- [ ] Create, switch, and merge branches
- [ ] Resolve merge conflicts
- [ ] Create pull requests and conduct code reviews
- [ ] Use `.gitignore` effectively

### Linux Basics
- [ ] Navigate the file system confidently
- [ ] Manage files and permissions
- [ ] Install and manage software packages
- [ ] Understand and manage processes
- [ ] Edit files using command-line editors

### Networking Basics
- [ ] Explain TCP/IP model
- [ ] Understand IP addresses and subnets
- [ ] Troubleshoot network connectivity
- [ ] Explain common ports (22, 80, 443, 3306)
- [ ] Use basic networking commands

### Scripting Basics
- [ ] Write basic Bash scripts
- [ ] Use variables and conditionals
- [ ] Create loops for automation
- [ ] Handle script arguments
- [ ] Understand Python basics

## 🎯 Hands-On Exercises

### Exercise 1: Git Workflow
```bash
# Create a new repository
# Make changes, commit, and push
# Create a branch, make changes, and merge
```

### Exercise 2: Linux Administration
```bash
# Create users and groups
# Set up file permissions
# Install and configure software
```

### Exercise 3: Network Troubleshooting
```bash
# Diagnose connectivity issues
# Test DNS resolution
# Check open ports
```

### Exercise 4: Automation Script
```bash
# Create a backup script
# Schedule it with cron
# Add error handling
```

## 📝 Learning Resources

### Official Documentation
- [Git Documentation](https://git-scm.com/doc)
- [Linux Documentation Project](https://tldp.org/)
- [AWS Documentation](https://docs.aws.amazon.com/)

### Interactive Learning
- [Learn Git Branching](https://learngitbranching.js.org/)
- [Linux Journey](https://linuxjourney.com/)
- [OverTheWire: Bandit](https://overthewire.org/wargames/bandit/) - Linux practice

### Books
- "Pro Git" by Scott Chacon (Free online)
- "The Linux Command Line" by William Shotts
- "Linux Basics for Hackers" by OccupyTheWeb

### Video Courses
- Linux Academy / A Cloud Guru
- Udemy: Git Complete
- YouTube: NetworkChuck, TechWorld with Nana

## 🔄 Next Steps

After mastering these prerequisites:

1. ✅ Complete all topic files
2. ✅ Practice hands-on exercises
3. ✅ Document your learnings in [learnings.md](learnings.md)
4. ✅ Take notes (handwritten-notes/)
5. ✅ Move to **02-Linux** for deep dive

## 📌 Important Notes

> **💡 Pro Tip**: Don't skip the prerequisites! These fundamentals will save you hours of frustration later.

> **⚠️ Common Mistake**: Trying to memorize everything. Focus on understanding concepts and knowing where to look things up.

> **🎯 Goal**: You don't need to master everything—just be comfortable enough to learn more as you go.

## 🤔 Self-Assessment Questions

1. Can you explain the difference between public and private cloud?
2. What is a Git branch and why would you use one?
3. How do you change file permissions in Linux?
4. What is the difference between TCP and UDP?
5. When would you use a shell script vs a Python script?

## 📈 Progress Tracking

Use [learnings.md](learnings.md) to track:
- ✍️ Daily progress and notes
- ❓ Questions and answers
- 💡 Key insights and aha moments
- 🐛 Challenges and how you solved them
- 🔗 Useful resources you found

---

## 📂 Module Structure

```
01-prerequisites/
├── README.md                  # This file
├── cloud-fundamentals.md      # Cloud basics
├── git-version-control.md     # Git and version control
├── linux-basics.md            # Linux fundamentals
├── networking-basics.md       # Networking concepts
├── scripting-basics.md        # Bash and Python basics
├── learnings.md               # Your personal notes
└── handwritten-notes/         # Handwritten notes (PDFs)
```

---

<div align="center">

### 🎓 Build a Strong Foundation!

**"Give me six hours to chop down a tree and I will spend the first four sharpening the axe."** - Abraham Lincoln

Start with: [Cloud Fundamentals](cloud-fundamentals.md)

</div>

---

**Last Updated**: January 2026  
**Module Status**: 🔴 Not Started
