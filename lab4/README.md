# Lab 4: Create and Use Azure Blob Storage

## 🎯 Objective
Learn how to create an Azure Storage Account and use Blob Storage to store and access files.

---

## 🧰 Prerequisites
- Azure subscription
- Resource Group (e.g., `lab-resources`)

---

## 1️⃣ Navigate to Storage Accounts

1. Log into [https://portal.azure.com](https://portal.azure.com)
2. Search for **Storage Accounts**
3. Click **+ Create** to start a new storage account


---

## 2️⃣ Configure Storage Account

1. Choose:
   - **Subscription**: Your active subscription
   - **Resource Group**: `lab-resources`
   - **Storage Account Name**: Must be globally unique (e.g., `labstorage2025`)
   - **Region**: Your preferred region
2. Leave the defaults for performance (Standard) and redundancy (LRS)



---

## 3️⃣ Review + Create

1. Skip tabs like Networking, Data Protection, and Advanced
2. Click **Review + Create**
3. Click **Create** once validation passes



---

## 4️⃣ Create a Blob Container

1. After deployment, go to the Storage Account
2. Under **Data Storage**, click **Containers**
3. Click **+ Container**
   - Name: `lab-container`
   - Public access level: **Private (no anonymous access)**
4. Click **Create**



---

## 5️⃣ Upload Files to Blob Storage

1. Click on the container you created (`lab-container`)
2. Click **Upload**
3. Select any file (e.g., a text file or image)
4. Upload and note the file’s path


---

## 6️⃣ (Optional) View Blob Properties and URL

1. Click on the uploaded blob
2. View its metadata, content type, and URL
3. You can copy the URL (if public access was enabled)


---

## ✅ Outcome
You’ve successfully created a storage account, a private container, and uploaded a file to Azure Blob Storage.
