# BCDV Lab4 - Ansible Inventory and VM Configuration

Ansible inventory and playbooks to configure Azure VM.

- VM: 172.191.182.41 (Ubuntu 20.04)
- Web: http://172.191.182.41
- SSH: azureuser@172.191.182.41

Files:
- `inventory.yml` - VM connection details
- `test-connection.yml` - Basic connectivity test
- `setup-vm.yml` - Install packages and nginx
- `verify-lab.yml` - Run all tests

Usage:
```bash
ansible azure_vms -m ping
ansible-playbook test-connection.yml
ansible-playbook setup-vm.yml
ansible-playbook verify-lab.yml
```
