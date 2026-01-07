# Ansible Automation Project

## Overview
Automate infrastructure configuration with Ansible.

## Project Structure
```
ansible/
├── inventory/
│   ├── production
│   └── staging
├── group_vars/
│   ├── all.yml
│   └── webservers.yml
├── host_vars/
├── roles/
│   ├── common/
│   ├── webserver/
│   ├── database/
│   └── monitoring/
├── playbooks/
│   ├── site.yml
│   ├── webserver.yml
│   └── database.yml
└── ansible.cfg
```

## Use Cases
1. Server provisioning
2. Application deployment
3. Configuration updates
4. Security hardening
5. Monitoring setup

## Usage
```bash
# Run full setup
ansible-playbook -i inventory/production playbooks/site.yml

# Run specific role
ansible-playbook -i inventory/production playbooks/webserver.yml

# Target specific hosts
ansible-playbook -i inventory/production playbooks/site.yml --limit web1
```

## Notes
