# raspberry-pi-services

Pi = Network Service Appliance

Not a compute node.

Meaning:

DNS (Pi-hole)
DHCP (later optional)
Recursive DNS (Unbound later)
Always-on infra dependency

## Features

Networking
Static IP enforced via Ansible
Single authoritative config source (netplan role)
Netplan applied safely via handler
System
Fully patched via unattended upgrades
Standard tooling installed
Timezone enforced
Access Layer
Tailscale SSH working
Ansible control plane working
Idempotent configuration verified (ping succeeds post-change)

Declarative network configuration + remote execution safety loop

## Architecture

Client Devices
    ↓
Pi-hole (192.168.0.3)
    ↓
Unbound (optional local recursion)
    ↓
Upstream DNS (1.1.1.1 / 8.8.8.8)

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
