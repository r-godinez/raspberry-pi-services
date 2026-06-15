# raspberry-pi-services

## Ansible

### Verify connection

ansible all \
-i inventory/hosts.yml \
-m ping

### Run Boostrap

ansible-playbook \
-i inventory/hosts.yml \
playbooks/bootstrap.yml \
-K

ansible-playbook playbooks/bootstrap.yml -K

### Install required collection locally

ansible-galaxy collection install community.general
