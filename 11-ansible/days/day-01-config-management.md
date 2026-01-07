# Day 01 - Configuration Management

## Topics Covered
- What is Configuration Management?
- Ansible overview
- Ansible architecture
- Inventory files
- Ad-hoc commands
- SSH setup

## Inventory Example
```ini
[webservers]
web1.example.com
web2.example.com

[databases]
db1.example.com

[all:vars]
ansible_user=ubuntu
ansible_ssh_private_key_file=~/.ssh/id_rsa
```

## Ad-hoc Commands
```bash
# Ping all hosts
ansible all -m ping

# Run command
ansible webservers -a "uptime"

# Install package
ansible webservers -m apt -a "name=nginx state=present" --become
```

## Notes
