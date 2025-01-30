
21. Automation and Configuration Management
Ansible
 ansible – Automation tool for configuration management
Page | 13
o ansible all -m ping – Ping all hosts defined in the
inventory
o ansible-playbook playbook.yml – Run an Ansible
playbook
o ansible -m command -a 'command' <host> – Run a
single command on a target host


o ansible-playbook --check playbook.yml – Dry-run
a playbook to see what would change
o ansible-playbook --limit <host> playbook.yml –
Run a playbook on a specific host or group
o ansible-playbook --extra-vars "key=value" –
Pass extra variables to a playbook