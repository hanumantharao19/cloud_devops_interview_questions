
## Automation and Configuration Management Ansible
- ansible –> Automation tool for configuration management
- ansible all -m ping    #Ping all hosts defined in the inventory
- ansible-playbook playbook.yml # Run an Ansible playbook
- ansible -m command -a 'command' <host> # Run a single command on a target host
-  ansible-playbook --check playbook.yml # Dry-run a playbook to see what would change
- ansible-playbook --limit <host> playbook.yml # Run a playbook on a specific host or group
- ansible-playbook --extra-vars "key=value" # Pass extra variables to a playbook