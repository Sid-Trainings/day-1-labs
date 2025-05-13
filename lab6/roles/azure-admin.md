# 🛠 Azure Admin Guide

## 🎯 Role Objective
As the **Primary Azure Admin**, you're the backbone of your company's cloud setup. You will:
- Set up the organizational environment on Azure
- Manage user access through RBAC
- Oversee the creation of the Resource Group
- Support other team roles with access and visibility

---

## ✅ Prerequisites
- You must be the one who created the Free Azure Account for your company
- Familiarity with the Azure Portal
- A list of your team members and their roles

---

## 🪜 Step-by-Step Tasks

### 1️⃣ Create a Resource Group
> **Name convention:** `<company>-rg` (e.g., `contoso-rg`)

1. Go to the Azure Portal → "Resource Groups"
2. Click **+ Create**
3. Choose your subscription and region
4. Name your group following naming convention
5. Click **Review + Create**

---

### 2️⃣ Add Users and Assign Roles (Detailed Steps)

#### 👉 A. Add Team Members to Your Azure Directory (Optional if simulating roles)

If you're using real Microsoft accounts for your team, follow these steps:

1. Go to **Azure Portal** → **Azure Active Directory**
2. Click on **Users** → then click **+ New guest user**
3. Under **Invite user**, enter:
   - **Name**: Team Member’s Name (e.g., Riya Patel)
   - **Email**: Their Microsoft Account Email (e.g., example@hotmail.com)
   - Leave the rest as default
4. Click **Invite**
5. Once they accept the invite (check their email), they’ll appear in your user list

📝 *If you're not adding real users, simulate this by assigning team members roles on paper or in your documentation.*

---

#### 👉 B. Assign IAM Roles to Team Members

Once your users (or simulated roles) are ready, assign them the correct permissions on the **Resource Group**.

1. Go to **Resource Groups**
2. Click on your resource group (e.g., `contoso-rg`)
3. In the left menu, click **Access Control (IAM)**
4. Click **+ Add** → **Add role assignment**
5. Under **Role**, select one of the following:
   - **Contributor** (Network & Storage Engineers)
   - **Virtual Machine Contributor** (SysAdmins)
   - **Security Admin** (Security Officers)
   - **Monitoring Reader + Reader** (Monitoring & Billing)
6. Under **Assign access to**, choose:
   - **User, group, or service principal**
7. Click **Select members** → Choose the user(s)
8. Click **Review + assign**

Repeat for each user and each role.

---

#### 🧾 Role Mapping Example

| Team Member | Role | Assigned Azure Role |
|-------------|------|----------------------|
| Rahul Mehta | Network Engineer | Contributor |
| Tanya Shah | Storage Engineer | Contributor |
| Aarav Jain | SysAdmin | Virtual Machine Contributor |
| Diya Kapoor | Security Officer | Security Admin |
| Kunal Verma | Monitoring & Billing | Reader + Monitoring Reader |

---

🧠 **Pro Tip:** You can also use Azure CLI for advanced or bulk assignments. (Optional challenge at the bottom of this guide)

📸 **Don’t forget:** Take a screenshot of the **Access Control (IAM)** page showing assigned roles for final submission.



---

### 3️⃣ Define & Follow Naming Conventions

In real organizations, naming conventions are crucial for organizing and managing resources at scale. While Azure doesn’t enforce naming rules by default, you’re expected to follow these **manually** for this lab.

---

#### 📘 Recommended Naming Convention

| Resource Type | Naming Format | Example (Company = Northwind) |
|---------------|----------------|-------------------------------|
| Resource Group | `<company>-rg` | `northwind-rg` |
| Virtual Network | `<company>-vnet` | `northwind-vnet` |
| Subnet | `<role>-subnet` | `app-subnet`, `db-subnet` |
| VM | `<company>-vm-<type>` | `northwind-vm-web`, `northwind-vm-int` |
| Storage Account | `<company>storage` | `northwindstorage` |
| Blob Containers | `public`, `private` | `public`, `private` |
| NSG | `<company>-nsg-<zone>` | `northwind-nsg-web` |

🧠 *Note: Storage account names must be globally unique and lowercase with no special characters.*

---

#### 🧪 How to Ensure Naming is Followed

1. **Shared Naming Sheet (Google Sheet / Excel)**
   - Maintain a shared document per company to list:
     - Team members
     - Resource names
     - Roles responsible
   - Review before deployment

2. **Resource Group Review**
   - As Azure Admin, regularly check the **Resource Group** to confirm naming
   - Provide feedback if a team violates the pattern

3. **Tag Resources (for clarity)**
   - Go to any resource → Click **Tags**
   - Add tags like:
     - `team: network`
     - `owner: rahul.mehta`
     - `env: test`
   - Helps with accountability and review

---

#### 🔐 Optional (Advanced / Theory Only): Azure Policy

> *For learning only — not applicable in Free Tier*

In real enterprises, Azure Policy is used to enforce naming conventions.

Example policy snippet:
```json
{
  "if": {
    "not": {
      "field": "name",
      "like": "nw-*"
    }
  },
  "then": {
    "effect": "deny"
  }
}
```

---

### 4️⃣ Monitor Resource Creation
- Work with your team to make sure each resource is created in the correct Resource Group.
- Validate that all users can access their respective resources (simulate or test access).

---

### 5️⃣ Configure and Enforce Resource Tagging

#### 🧭 What are Tags?
Tags are key-value pairs that help categorize resources in Azure. For example:
- `team: network`
- `owner: tanya.shah`
- `env: test`

They’re **not just labels** — in real organizations, they’re used for:
- **Cost tracking** across departments
- **Automation** scripts
- **Organizational visibility**
- **Security audits**

---

#### 👩‍💼 Azure Admin’s Role in Tagging

You’re responsible for:
- **Defining** the tagging structure for your company
- **Sharing** it with the entire team
- **Reviewing** all resources in your Resource Group for proper tags
- **Helping** team members tag resources correctly

---

#### 📘 Tag Format to Follow (Company-Wide)

| Tag Key | Description | Example |
|---------|-------------|---------|
| `team` | Team or role that owns the resource | `network`, `storage`, `sysadmin` |
| `owner` | Person responsible | `aarav.jain` |
| `env` | Environment type | `test`, `prod`, `dev` |

---

#### 🪜 How to Add Tags (Azure Portal)

1. Go to the **Resource Group** or specific **resource** (VM, VNet, etc.)
2. Click on **Tags** in the left-hand menu
3. Add the key-value pairs:
   - `team: sysadmin`
   - `owner: tanya.shah`
   - `env: test`
4. Click **Save**

✅ Tip: Tags can be added during resource creation too — ask your team to fill them out there when possible.

---

#### ✅ Tag Review Checklist (for Azure Admin)

Before submission, ensure:
- All deployed resources have **at least 3 tags**
- **Team roles** and **owners** are correctly reflected
- **Environment tags** match the purpose (e.g., `test` not `prod`)
- No typos or inconsistent naming (`Team` ≠ `team`)

📸 **Take a screenshot of the tag pane for 2–3 key resources** for submission.

---

#### 🚀 Bonus: Tagging via Azure CLI

Here’s a quick command to tag a VM (optional for advanced users):
```bash
az resource tag \
  --tags team=sysadmin owner=aarav.jain env=test \
  --resource-id /subscriptions/<sub-id>/resourceGroups/northwind-rg/providers/Microsoft.Compute/virtualMachines/northwind-vm-web
```
---

### 📸 Final Deliverables
Include in your team’s submission:

- Screenshot of Resource Group with all resources

- Screenshot of IAM role assignments (or a table documenting them)

- Summary note: Challenges faced and how you resolved them

### 🧠 Tips for Admins
- Stay in sync with all roles

- Use the Azure CLI for quick tasks if comfortable

- Be the escalation point in case others hit permissions issues

### 🧪 Bonus (Optional Challenge)
Try assigning RBAC roles using Azure CLI:
```commandline
az role assignment create \
  --assignee <user-email-or-object-id> \
  --role "Contributor" \
  --scope "/subscriptions/<sub-id>/resourceGroups/<group-name>"

```
🔗 [← Back to Main Lab Guide](../README.md)