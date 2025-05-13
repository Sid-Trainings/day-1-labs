# 🌐 Network Engineer Guide

## 🎯 Role Objective
As a **Network Engineer**, your job is to create the backbone of your organization’s cloud infrastructure. You’ll design and implement secure, scalable networks using Virtual Networks (VNets), Subnets, and Network Security Groups (NSGs).

---

## ✅ Prerequisites
- You must be added to the Azure Resource Group with **Contributor** access.
- Assigned resource group and naming conventions from your Azure Admin.

---

## 🪜 Step-by-Step Lab Tasks

### 1️⃣ Create a Virtual Network (VNet)

1. Go to **Azure Portal** → **Search "Virtual Networks"**
2. Click **+ Create**
3. Fill in the following:
   - **Subscription:** Your free subscription
   - **Resource Group:** Select your team’s RG (e.g., `northwind-rg`)
   - **Name:** Use format `<company>-vnet` (e.g., `northwind-vnet`)
   - **Region:** Same as RG
4. Click **Next: IP Addresses**

---

### 2️⃣ Define Address Space & Subnets

1. In **IP Addresses** tab:
   - Set **Address Space** to `10.0.0.0/16`
2. Click **+ Add subnet**
   - **Subnet 1 Name:** `web-subnet`
   - **Range:** `10.0.1.0/24`
3. Add another subnet:
   - **Subnet 2 Name:** `internal-subnet`
   - **Range:** `10.0.2.0/24`
4. Click **Review + Create**

---

### 3️⃣ Create Network Security Groups (NSGs)

1. Go to **"Network Security Groups"** → **+ Create**
2. Fill in:
   - **Name:** `<company>-nsg-web` (e.g., `northwind-nsg-web`)
   - **Resource Group:** Your team’s RG
   - **Region:** Same as VNet
3. Click **Review + Create**

4. Repeat to create another NSG:
   - Name: `<company>-nsg-int`

---

### 4️⃣ Add Inbound Security Rules

#### 📂 NSG for Web Subnet (`-nsg-web`)
1. Open `-nsg-web` → Go to **Inbound Security Rules**
2. Click **+ Add**
   - **Source:** Any
   - **Protocol:** TCP
   - **Port:** 80, 443
   - **Action:** Allow
   - **Priority:** 100
   - **Name:** `allow-web`

#### 🔐 NSG for Internal Subnet (`-nsg-int`)
1. Open `-nsg-int` → **Inbound Security Rules**
2. Click **+ Add**
   - **Port:** 22 (for SSH) or 3389 (for RDP, if Windows)
   - **Source:** Your IP or VNet
   - **Priority:** 100
   - **Name:** `allow-admin`

📝 Add a **deny all rule** with higher priority if you want to simulate security-first approach.

---

### 5️⃣ Associate NSGs with Subnets

1. Go to **Virtual Network** → **Subnets**
2. Click on each subnet → Assign the appropriate NSG:
   - `web-subnet` → `-nsg-web`
   - `internal-subnet` → `-nsg-int`

---

### 6️⃣ Verify & Document

- Ensure VNet has both subnets created.
- Ensure NSGs are visible in the subnet configuration.
- Work with the SysAdmin team to attach VMs to these subnets.
- Validate that access rules are working (e.g., only HTTP on web VM).

---

## 🧾 Deliverables

- Screenshot of:
  - VNet overview with address space
  - Subnet list
  - NSG inbound rule summary
- A short note: Any issues faced and how you resolved them
- Optional: Diagram of network layout (use draw.io or paper)

---

## 🧪 Bonus Challenge (Optional)

Try deploying the VNet via Azure CLI:
```bash
az network vnet create \
  --name northwind-vnet \
  --resource-group northwind-rg \
  --address-prefix 10.0.0.0/16 \
  --subnet-name web-subnet \
  --subnet-prefix 10.0.1.0/24
```
Then add the internal subnet:
```commandline
az network vnet subnet create \
  --address-prefix 10.0.2.0/24 \
  --name internal-subnet \
  --resource-group northwind-rg \
  --vnet-name northwind-vnet
```
🔗 [← Back to Main Lab Guide](../README.md)