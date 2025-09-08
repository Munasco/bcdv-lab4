# BCDV Lab4 - Ansible Inventory and VM Configuration

**Student Name:** Munachi Ernest-Eze  
**Course:** BCDV 4033  
**Assignment:** Lab 4 - Ansible Inventory and VM Configuration  
**Due Date:** June 14, 2025 11:59 PM  
**GitHub Repository:** https://github.com/Munasco/bcdv-lab4

This lab demonstrates how to create Ansible inventory files and connect to Azure VMs for automated configuration management.

## 📋 Assignment Overview

- **Lab Name:** BCDV Lab4
- **Focus:** Ansible inventory management and VM automation
- **Target VM:** Azure Ubuntu 20.04 LTS (created in previous Terraform lab)
- **Public IP:** 172.191.182.41
- **Private IP:** 10.0.2.4
- **User:** azureuser
- **Web Server:** http://172.191.182.41

## 🗂️ Project Structure

```
bcdv-lab4/
├── inventory.yml           # Ansible inventory file
├── ansible.cfg            # Ansible configuration
├── test-connection.yml     # Basic connection test playbook
├── setup-vm.yml           # VM configuration playbook
└── README.md              # This documentation
```

## ⚙️ Prerequisites

1. **Ansible installed:**
   ```bash
   pip install ansible
   ```

2. **SSH access to Azure VM:**
   - Private key: `~/.ssh/id_rsa`
   - Public IP: `172.191.182.41`
   - User: `azureuser`

3. **Azure VM running** (from previous Terraform lab)

## 📝 Inventory File (`inventory.yml`)

The inventory file defines our Azure VM connection details:

```yaml
azure_vms:
  hosts:
    demo-vm:
      ansible_host: 172.191.182.41
      ansible_user: azureuser
      ansible_ssh_private_key_file: ~/.ssh/id_rsa
      vm_name: demo-vm-vm
      vm_location: eastus
      vm_resource_group: rg-terraform-demo
```

## 🚀 Usage Instructions

### 1. Test Ansible Connection

Verify that Ansible can connect to your VM:

```bash
# Test basic connectivity
ansible azure_vms -m ping

# Check system information
ansible azure_vms -m setup
```

### 2. Run Connection Test Playbook

Execute the test playbook to gather system information:

```bash
ansible-playbook test-connection.yml
```

### 3. Configure VM with Essential Tools

Run the setup playbook to install software and configure nginx:

```bash
ansible-playbook setup-vm.yml
```

### 4. Verify Web Server

After running the setup playbook, visit:
```
http://172.191.182.41
```

## 📊 Expected Output

### Connection Test Results:
- ✅ Ping successful
- 📊 System facts gathered
- 💾 Disk usage reported
- ⏰ Uptime displayed

### VM Setup Results:
- 📦 Essential packages installed
- 🌐 Nginx web server running
- 📄 Custom webpage deployed
- 👤 User directories created

## 🔧 Ansible Commands Reference

```bash
# List all hosts in inventory
ansible-inventory --list

# Test connectivity to specific host
ansible demo-vm -m ping

# Run ad-hoc command on all VMs
ansible azure_vms -a "uptime"

# Check disk space
ansible azure_vms -a "df -h"

# Update packages (with sudo)
ansible azure_vms -b -m apt -a "update_cache=yes"

# Install specific package
ansible azure_vms -b -m apt -a "name=htop state=present"
```

## 🎯 Lab Objectives

1. ✅ Create Ansible inventory file
2. ✅ Configure Ansible connection settings
3. ✅ Test VM connectivity using Ansible
4. ✅ Gather system facts from remote VM
5. ✅ Execute playbooks for system configuration
6. ✅ Install and configure web server
7. ✅ Verify automated deployment

## 📚 Key Learning Points

- **Inventory Management:** How to organize and connect to multiple hosts
- **SSH Configuration:** Secure key-based authentication setup
- **Playbook Structure:** YAML syntax and task organization
- **System Administration:** Automated package installation and service management
- **Fact Gathering:** Collecting and using system information in playbooks

## 🔍 Troubleshooting

### Connection Issues:
```bash
# Test SSH connectivity manually
ssh -i ~/.ssh/id_rsa azureuser@172.191.182.41

# Verify SSH key permissions
chmod 600 ~/.ssh/id_rsa

# Check Ansible connectivity
ansible demo-vm -m ping -vvv
```

### Common Solutions:
- Ensure VM is running and accessible
- Verify SSH key path in inventory
- Check security group rules for SSH (port 22)
- Confirm user permissions on target system

## 🧹 Cleanup

To clean up resources after the lab:

```bash
# Stop services if needed
ansible azure_vms -b -m systemd -a "name=nginx state=stopped"

# Remove packages (optional)
ansible azure_vms -b -m apt -a "name=nginx state=absent"
```

## 📞 Support

For issues with this lab, check:
1. Azure VM is running and accessible via SSH
2. Ansible is properly installed
3. SSH keys are correctly configured
4. Network connectivity to Azure VM

## 📎 Assignment Submission

### What to Submit:

1. **GitHub Repository Link:**  
   https://github.com/Munasco/bcdv-lab4

2. **Screenshots:** (Located in `screenshots/` folder)
   - Ansible ping connection test
   - Test connection playbook results  
   - VM setup playbook execution
   - Final verification results
   - Working web server in browser
   - Azure portal showing running VM
   - Network security group rules
   - GitHub repository overview

3. **Live Demonstration URLs:**
   - **Web Server:** http://172.191.182.41
   - **SSH Access:** `ssh azureuser@172.191.182.41`

### 🎆 Lab Completion Status

✅ **COMPLETED SUCCESSFULLY**

- ✓ Ansible inventory file created and configured
- ✓ Successfully connected to Azure VM via Ansible
- ✓ Automated VM configuration using playbooks
- ✓ Installed essential software packages
- ✓ Deployed and configured Nginx web server
- ✓ Created custom web page showing VM information
- ✓ All verification tests passing
- ✓ Documentation complete with usage instructions

### 📨 Technical Implementation

**Infrastructure:**
- Azure VM: Ubuntu 20.04 LTS (Standard_B1s)
- Resource Group: rg-terraform-demo
- Location: East US
- Network: Secure with SSH (22) and HTTP (80) access

**Ansible Configuration:**
- Inventory file with connection details
- SSH key authentication (no passwords)
- Automated playbooks for system configuration
- Comprehensive verification and testing

**Software Deployed:**
- Web Server: Nginx with custom HTML page
- Development tools: git, curl, wget, vim, htop, tree
- Runtime: nodejs, npm, python3-pip

---

**Lab completed successfully! 🎉**

This lab demonstrates practical Ansible usage for infrastructure automation and configuration management, meeting all course objectives for BCDV 4033 Lab 4.
