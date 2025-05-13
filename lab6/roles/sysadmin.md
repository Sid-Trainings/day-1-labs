# 🖥 SysAdmin Guide

## 🎯 Role Objective
As a **SysAdmin**, your responsibility is to deploy and configure virtual machines that simulate production and internal environments. You’ll create:
- A **web-facing VM** for public access
- An **internal VM** for internal team access
- A **generalized template (image)** from one VM
- Additional VM(s) using that image

## ✅ Prerequisites
- **Contributor or VM Contributor** role assigned
- Network and Storage teams should already have:
  - Created the VNet and subnets (`web-subnet`, `internal-subnet`)
  - Set up blob containers (optional for testing)

## 🪜 Step-by-Step Tasks

### 1️⃣ Create Your First Virtual Machine (Web Server)

1. Go to **Azure Portal** → Search **Virtual Machines**
2. Click **+ Create**
3. Fill in:
   - **Subscription:** Your free-tier
   - **Resource Group:** e.g., `northwind-rg`
   - **VM Name:** `<company>-vm-web` (e.g., `northwind-vm-web`)
   - **Region:** Same as rest of team
   - **Image:** Ubuntu 20.04 LTS (or Windows if preferred)
   - **Size:** Standard B1s
   - **Auth Type:** Password (shareable for team if needed)
   - **Username/Password:** Note these down
   - **Inbound Ports:** HTTP, HTTPS (and SSH)

4. Click **Next → Disks**: Keep defaults
5. Click **Next → Networking**:
   - **Virtual Network:** Select your team’s VNet
   - **Subnet:** Select `web-subnet`
   - **Public IP:** Yes (Static)
   - **NSG:** Use existing (`-nsg-web`)

6. Click **Review + Create** → Then **Create**

### 2️⃣ Install Basic Web Server (Ubuntu)

Once deployed:
1. SSH into the VM using the portal or terminal:
```bash
ssh username@<public-ip>
```
2. Run:
```bash
sudo apt update
sudo apt install apache2 -y
```
3. Verify:
   - Go to browser → `http://<public-ip>` → Should show Apache welcome page

### 3️⃣ Create an Internal-Only VM

Repeat steps from above but with these changes:

- **VM Name:** `<company>-vm-int`
- **Subnet:** `internal-subnet`
- **NSG:** Use `-nsg-int`
- **Public IP:** Set to **None** (for simulation of internal-only)

*Access to this VM should be via Private IP or simulated (just note this setup).*

### 4️⃣ Tag Both VMs

Add these tags:
- `owner: yourname`
- `team: sysadmin`
- `env: test` or `web` / `internal`

### 5️⃣ [Advanced] Create a VM Template Image

Let’s simulate what’s done in production — use your web VM to create a **custom image**.

#### a. Deprovision the VM
SSH into the VM:
```bash
sudo waagent -deprovision+user
```
Type `y` if prompted, then:

#### b. Deallocate the VM
1. In Azure Portal → VM → Click **Stop (Deallocate)**

#### c. Capture the Image
1. In Azure Portal → VM → Click **Capture**
2. Fill in:
   - **Name:** `webvm-image`
   - **Resource Group:** Same
   - Select: **Automatically delete after capture**
3. Click **Create**

✅ This will create a **generalized image** in your resource group.

### 6️⃣ Deploy a VM from Custom Image

1. Go to **Virtual Machines** → **+ Create**
2. Under **Image**, select **"My Items" → Your image**
3. Fill in:
   - **Name:** `<company>-vm-web2`
   - Other settings: Same as before
   - **Subnet:** Optional — can be same or different

This simulates a scaled deployment — great in real production scenarios.

## 🧾 Deliverables

- Screenshots of:
  - All deployed VMs and their configurations
  - Tags added
  - Apache homepage (or other installed app)
  - Image captured from base VM
- Note any issues (e.g., NSG blocks, SSH issues, image failure)

## 🧪 Bonus CLI (Optional)

Create a VM from CLI:
```bash
az vm create \
  --resource-group northwind-rg \
  --name northwind-vm-web \
  --image UbuntuLTS \
  --admin-username azureuser \
  --admin-password P@ssword1234 \
  --vnet-name northwind-vnet \
  --subnet web-subnet \
  --nsg northwind-nsg-web \
  --public-ip-address ""
```

📍 Final Tip:
Work with the **Network Team** for subnet/NIC issues and the **Storage Team** for backup or blob mounting simulations.

🔗 [← Back to Main Lab Guide](../README.md)