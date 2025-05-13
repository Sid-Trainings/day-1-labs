# Lab 3: Deploy an Azure Virtual Machine (IaaS)

## 🎯 Objective
Learn how to create and configure a Virtual Machine (VM) on Microsoft Azure using the Azure Portal.

---

## 🧰 Prerequisites
- Azure subscription
- Resource Group (e.g., `lab-resources`) already created

---

## 1️⃣ Navigate to Virtual Machines

1. Go to the Azure Portal: https://portal.azure.com
2. Use the search bar to find **Virtual Machines**
3. Click on **+ Create > Azure virtual machine**

![Step 1 - Navigate to VMs](images/lab3_step1_vm_nav.png)

---

## 2️⃣ Configure Basic Settings

1. Choose the following options:
   - **Subscription**: Your active subscription
   - **Resource Group**: `lab-resources`
   - **Virtual machine name**: `lab-vm`
   - **Region**: Select your closest region
   - **Image**: Ubuntu 22.04 LTS or Windows Server 2019
   - **Size**: Select B1s (Free Tier eligible)
2. Set up admin username and password or SSH key

![Step 2 - VM Basic Settings](images/lab3_step2_vm_basics.png)

---

## 3️⃣ Configure Networking

1. Leave default values for virtual network, subnet, and public IP
2. Allow selected inbound ports:
   - SSH (22) for Linux
   - RDP (3389) for Windows

![Step 3 - VM Networking](images/lab3_step3_vm_network.png)

---

## 4️⃣ Review and Create

1. Skip disks, management, monitoring, and advanced for now
2. Click **Review + Create**
3. Once validation passes, click **Create**

![Step 4 - Review and Create](images/lab3_step4_review.png)

---

## 5️⃣ Connect to Your VM

1. Once deployment is complete, go to the VM's overview page
2. Click **Connect** and choose either:
   - **SSH** (for Linux) → copy and run in terminal
   - **RDP** (for Windows) → download RDP file and connect

![Step 5 - VM Connection Options](images/lab3_step5_connect.png)

---

## ✅ Outcome
You have successfully deployed a Virtual Machine on Azure and connected to it.
