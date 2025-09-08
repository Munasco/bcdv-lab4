# Screenshots for BCDV Lab4 Submission

Please add the following screenshots to this directory:

## Required Screenshots:

### 1. Ansible Inventory Connection Test
- **Filename:** `01-ansible-ping-success.png`
- **Content:** Terminal showing successful `ansible azure_vms -m ping` command
- **Shows:** Connection established to Azure VM

### 2. Test Connection Playbook Results
- **Filename:** `02-test-connection-playbook.png`
- **Content:** Terminal output from `ansible-playbook test-connection.yml`
- **Shows:** System information, disk usage, uptime

### 3. VM Setup Playbook Execution
- **Filename:** `03-setup-vm-playbook.png`
- **Content:** Terminal output from `ansible-playbook setup-vm.yml`
- **Shows:** Package installation and nginx configuration

### 4. Final Verification Playbook
- **Filename:** `04-verification-results.png`
- **Content:** Terminal output from `ansible-playbook verify-lab.yml`
- **Shows:** All tests passing with green checkmarks

### 5. Web Server Running
- **Filename:** `05-website-browser.png`
- **Content:** Browser showing http://172.191.182.41
- **Shows:** Custom webpage with VM information deployed by Ansible

### 6. Azure Portal - VM Running
- **Filename:** `06-azure-vm-portal.png`
- **Content:** Azure portal showing the running VM in resource group
- **Shows:** VM status, public IP, resource group details

### 7. Azure Portal - Network Security Group
- **Filename:** `07-azure-nsg-rules.png`
- **Content:** Azure portal showing NSG with SSH (22) and HTTP (80) rules
- **Shows:** Security rules allowing both SSH and web traffic

### 8. GitHub Repository
- **Filename:** `08-github-repository.png`
- **Content:** Browser showing GitHub repo https://github.com/Munasco/bcdv-lab4
- **Shows:** All files committed and repository structure

## Optional Additional Screenshots:

### 9. SSH Connection to VM
- **Filename:** `09-ssh-connection.png`
- **Content:** Terminal showing SSH connection to azureuser@172.191.182.41
- **Shows:** Direct SSH access to the VM

### 10. Ansible Inventory File
- **Filename:** `10-inventory-file.png`
- **Content:** Code editor showing inventory.yml contents
- **Shows:** Ansible inventory configuration

---

**Total Required: 8 screenshots**  
**Total Optional: 2 screenshots**

All screenshots should clearly show the success of each component of the lab.
