# 🗄 Storage Engineer Guide

## 🎯 Role Objective
As a **Storage Engineer**, you’re responsible for setting up and managing Azure Storage. You'll create a storage account, configure blob containers (both public and private), and set access levels properly.

---

## ✅ Prerequisites
- You must have **Contributor access** to the Resource Group from your Azure Admin.
- Use the company-wide **naming convention**.
- Coordinate with your team to ensure resource consistency.

---

## 🪜 Step-by-Step Lab Tasks

### 1️⃣ Create a Storage Account

1. Go to **Azure Portal** → Search **"Storage accounts"**
2. Click **+ Create**
3. Fill in the form:
   - **Subscription:** Your free subscription
   - **Resource Group:** Use your assigned one (e.g., `northwind-rg`)
   - **Storage Account Name:** `<company>storage` (e.g., `northwindstorage`)
     > Must be globally unique, lowercase, no special characters
   - **Region:** Same as other resources
   - **Performance:** Standard
   - **Redundancy:** Locally-redundant storage (LRS)
4. Click **Review + Create**

---

### 2️⃣ Create Blob Containers

1. After the Storage Account is created, open it
2. In the left menu, go to **Data storage → Containers**
3. Click **+ Container** to create two containers:

#### a. Public Container
- **Name:** `public`
- **Public Access Level:** Container (anonymous read access)

#### b. Private Container
- **Name:** `private`
- **Public Access Level:** Private (no anonymous access)

4. Click **Create** for each

---

### 3️⃣ Upload Sample Files

1. Enter each container (`public` and `private`)
2. Click **Upload**
3. Choose a file from your machine (e.g., an image or PDF)
4. Click **Upload**

✅ Try uploading the same file to both containers — this will help test access control with the SysAdmin or Security team.

---

### 4️⃣ Set Tags on the Storage Account

1. Go to the Storage Account → **Tags**
2. Add:
   - `team: storage`
   - `owner: yourname`
   - `env: test`
3. Click **Save**

---

### 5️⃣ (Optional) Enable Static Website Hosting

You can simulate hosting a basic website from the blob storage:

1. In the Storage Account → go to **Static Website**
2. Enable it
3. Upload an `index.html` file to `$web` container
4. Access the URL provided

> *Great for bonus points if you coordinate with SysAdmins or Admins!*

---

## 🧾 Deliverables

- Screenshot of:
  - Storage Account Overview
  - Blob container list showing public/private settings
  - One file uploaded in each container
  - Tags applied
- Short summary:
  - Who owns what?
  - Any access issues?
  - Coordination required with which team?

---

## 🧪 Bonus Challenge (Optional)

Try using Azure CLI to create a storage account:
```bash
az storage account create \
  --name northwindstorage \
  --resource-group northwind-rg \
  --location eastus \
  --sku Standard_LRS
```
To create a container:
```commandline
az storage container create \
  --name public \
  --account-name northwindstorage \
  --public-access container
```
### 📍 Final Tip:
Coordinate with the Security Officer to make sure access policies on private data are secure and tested.

🔗 [← Back to Main Lab Guide](../README.md)