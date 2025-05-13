# 📊 Monitoring & Billing Guide

## 🎯 Role Objective
As the **Monitoring & Billing Analyst**, you’ll track performance, configure alerts, and estimate resource usage. This is a vital role to simulate FinOps and proactive health monitoring in the cloud.

---

## ✅ Prerequisites
- Assigned **Reader** + **Monitoring Reader** role
- Ensure tagging is completed (especially `env`, `owner`, `team`)

---

## 🪜 Step-by-Step Lab Tasks

### 1️⃣ Enable Monitoring Insights

1. Go to **Resource Group** → Click any **VM**
2. In the left pane, click **Monitoring → Insights**
3. Click **Enable**
4. Do the same for Storage if possible

---

### 2️⃣ Set Up a Basic Alert

1. Go to **Monitor** → **Alerts**
2. Click **+ New alert rule**
3. Scope: Select one VM
4. Condition:
   - Metric: **CPU percentage**
   - Operator: **Greater than**
   - Threshold: `70`
5. Action group: **Create simulated action** (or skip actual config)
6. Click **Review + Create**

---

### 3️⃣ Review Cost Estimations

1. Go to **Cost Management + Billing**
2. Select **Cost Analysis**
3. Filter by your Resource Group
4. Capture screenshot showing cost (even ₹0) and resource usage

---

### 4️⃣ Validate Resource Tagging

Go to **Resource Group**:
1. Confirm each resource has tags:
   - `owner`, `team`, `env`
2. Log resources missing any tag

---

## 🧾 Deliverables

- Screenshot of Alert Rule
- Screenshot of Cost Analysis view (Resource Group-level)
- Summary of any missing tags and resource usage trends

---

📍 Optional Bonus:
Install **Log Analytics Agent** or explore **Azure Advisor** recommendations for optimization ideas.

---

🔗 [← Back to Main Lab Guide](../README.md)