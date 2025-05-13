# Lab 6: Enterprise Simulation on Azure

## 🌐 Overview
Welcome to the final lab of Day 1 — a real-world Azure simulation where you will operate as IT teams within a virtual organization. You’ll collaborate in groups, take on specific roles, and deploy an end-to-end enterprise environment on Azure.

- **Objective:** Simulate enterprise infrastructure management using Azure
- **Setup:** 4 virtual companies (10 students per company)
- **Time Allotment:** 90–120 minutes

---

## 🏢 Company Setup
Each company represents a free-tier Azure subscription and should:
- Have a unique name (e.g., Contoso, Fabrikam, Northwind, AdventureWorks)
- Assign **one Primary Azure Admin** to set up the organization
- Use consistent **naming conventions** (e.g., `nw-vm-web`, `contoso-rg1`)

---

## 👥 Roles & Responsibilities
Each company is structured into functional teams:

| Role | Count | Responsibilities | Readme Link |
|------|-------|------------------|-------------|
| Azure Admin | 1 | IAM roles, resource group setup | [Admin Guide](./roles/azure-admin.md) |
| Network Engineers | 2 | VNets, Subnets, NSGs | [Network Guide](./roles/network-engineer.md) |
| Storage Engineers | 2 | Storage accounts, blob containers | [Storage Guide](./roles/storage-engineer.md) |
| SysAdmins | 3 | VM deployment, tagging, config | [SysAdmin Guide](./roles/sysadmin.md) |
| Security Officers | 1 | RBAC, Policies, Defender | [Security Guide](./roles/security-officer.md) |
| Monitoring & Billing | 1 | Alerts, usage review | [Monitoring Guide](./roles/monitoring-billing.md) |

---

## 📋 Team Tasks (Company-Wide)
All teams will collaborate to:
1. Create a Resource Group using a consistent naming convention
2. Deploy Virtual Networks with subnets and NSGs
3. Set up Storage (private/public blob containers)
4. Deploy VMs for public and internal usage
5. Assign IAM roles per role responsibility
6. Apply basic security and cost monitoring settings

---

## 📄 Final Submission (Per Company)
Each team must submit:
- ✅ Screenshot of Resource Group and deployed services
- ✅ Architecture Diagram (via draw.io or hand-drawn photo)
- ✅ Troubleshooting notes or error handling
- ✅ Names & tasks of each team member

---

## ✅ Completion Criteria
To successfully complete the lab:
- All services must be configured and functional
- Proper role-based access must be applied
- Team members must document actions and share learnings

---

## 📂 Role-Based Lab Guides
Navigate to your role guide to get detailed steps:

- [`roles/azure-admin.md`](./roles/azure-admin.md)
- [`roles/network-engineer.md`](./roles/network-engineer.md)
- [`roles/storage-engineer.md`](./roles/storage-engineer.md)
- [`roles/sysadmin.md`](./roles/sysadmin.md)
- [`roles/security-officer.md`](./roles/security-officer.md)
- [`roles/monitoring-billing.md`](./roles/monitoring-billing.md)

---

### 💡 Pro Tip
Treat this like a real job — communicate clearly with your teammates, follow best practices, and document everything!

---
