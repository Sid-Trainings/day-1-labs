# Lab 5: Azure CLI + VM Deployment Scripts

## 🎯 Objective
Learn basic Azure CLI commands and automate VM deployment using Bash and PowerShell scripts.

---

## 🧰 Prerequisites
- Azure CLI installed  
  [Installation Guide](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli)
- Logged in to Azure using:
  ```bash
  az login

- Existing Resource Group (e.g., lab-resources)

## 1️⃣ Basic Azure CLI Commands
```
# Check CLI version
az version

# List available resource groups
az group list --output table

# View available VM sizes in a region
az vm list-sizes --location eastus --output table

# List all VMs in your subscription
az vm list -d --output table
```

## 2️⃣ Create a Single VM via Azure CLI
```
az vm create \
  --name myvm01 \
  --resource-group lab-resources \
  --image UbuntuLTS \
  --admin-username azureuser \
  --generate-ssh-keys \
  --location eastus \
  --size Standard_B1s
```
## 3️⃣ Bash/PowerShell Script: Deploy Multiple VMs
In this section you will aim to deploy multiple VMs using predefined inputs but via command line to save time

### Bash Script
```
#!/bin/bash

# Usage: ./create-vms.sh <region> <count>
REGION=$1
COUNT=$2
RESOURCE_GROUP="lab-resources"

for i in $(seq 1 $COUNT); do
  VM_NAME="vm${i}"
  echo "Creating $VM_NAME in $REGION..."
  az vm create \
    --name $VM_NAME \
    --resource-group $RESOURCE_GROUP \
    --image UbuntuLTS \
    --admin-username azureuser \
    --generate-ssh-keys \
    --location $REGION \
    --size Standard_B1s \
    --no-wait
done
```
**Save as:** ```create-vms.sh```

**Run:** 
```
chmod +x create-vms.sh
./create-vms.sh eastus 3
```

### Powershell Script
```
# Usage: .\create-vms.ps1 -Region "eastus" -Count 3

param (
  [string]$Region = "eastus",
  [int]$Count = 3
)

$ResourceGroup = "lab-resources"

for ($i = 1; $i -le $Count; $i++) {
  $VMName = "vm$i"
  Write-Output "Creating $VMName in $Region..."
  az vm create `
    --name $VMName `
    --resource-group $ResourceGroup `
    --image UbuntuLTS `
    --admin-username azureuser `
    --generate-ssh-keys `
    --location $Region `
    --size Standard_B1s `
    --no-wait
}

```
**Save as:** ```create-vms.ps1```

**Run:**  ```.\create-vms.ps1 -Region "eastus" -Count 3```
