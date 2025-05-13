# 🔐 Security Officer Guide

## 🎯 Role Objective
As a **Security Officer**, you're responsible for ensuring the cloud environment is secure. You'll configure RBAC (Role-Based Access Control), simulate security policies, and optionally enable tools like Microsoft Defender for Cloud.

---

## ✅ Prerequisites
- Assigned the **Security Admin** role by your Azure Admin
- Have access to the Resource Group and users’ details

---

## 🪜 Step-by-Step Lab Tasks

### 1️⃣ Review IAM Role Assignments

1. Go to **Resource Groups** → Select your team’s RG
2. Click **Access Control (IAM)** → **Role assignments**
3. Review:
   - Each member is assigned correct roles (Contributor, VM Contributor, etc.)
4. Document mismatches or simulate permission checks with the team

---

### 2️⃣ Apply Least Privilege Principle (RBAC Review)

If access seems too broad:
1. Inform Azure Admin
2. Suggest scope-based roles instead of full access:
   - **Reader** vs **Contributor**
   - **VM Contributor** for SysAdmins only

---

### 3️⃣ Simulate Conditional Access (Documented)

1. Go to **Azure Active Directory** → **Security → Conditional Access**
2. Explore but **do not configure (Free tier limitation)**
3. Document how you would:
   - Require MFA
   - Block access outside specific IPs
   - Enable device compliance

---

### 4️⃣ Enable Microsoft Defender for Cloud (if available)

1. Go to **Defender for Cloud**
2. Select your subscription
3. Enable **Defender plans** (where applicable)
4. Note security recommendations generated

---

### 5️⃣ Review NSG Rules

Work with Network Engineers:
1. Go to **Virtual Networks → Subnets**
2. Ensure:
   - `web-subnet` allows only HTTP/HTTPS
   - `internal-subnet` allows only SSH/RDP
3. Document any open ports that shouldn't be

---

### 6️⃣ Tag Resources with Security Responsibility

Go to each critical resource (VM, Storage, NSG):
1. Add a tag:
   - `security-owner: yourname`
   - `compliance: reviewed`
2. Save and verify tags appear in Resource Group view

---

## 🧾 Deliverables

- Screenshot of IAM role assignment list
- Security checklist filled (attached separately or typed)
- Tags added to at least 3 security-sensitive resources
- Notes on potential risks or misconfigurations found

---

## 🚀 Optional Advanced Configurations (Paid Features)

> These tasks require **Azure AD Premium P1/P2**. If you're willing to activate a trial or use credits, here’s how you can simulate enterprise-grade security.

---

### 🔐 A. Enable Multi-Factor Authentication (MFA)

1. Go to **Azure Portal** → **Azure Active Directory**
2. In the left menu, click **Users**
3. Click **Per-user MFA** (or use direct link: https://portal.azure.com/#blade/Microsoft_AAD_IAM/MfaSettingsMenu/overview)
4. Select a user → Click **Enable**
5. Ask the user to sign in again — they’ll be prompted to set up an authenticator app or SMS-based MFA

📝 *Simulate this by doing it on your own account.*

---

### 🌍 B. Region-Based Conditional Access

> Only works with Azure AD Premium P1 or above.

1. Go to **Azure Active Directory → Security → Conditional Access**
2. Click **+ New policy**
3. Name it: `Block Non-India Sign-ins`
4. **Assignments → Users or workload identities:**
   - Select a specific test user (or yourself)
5. **Cloud apps or actions:**
   - Choose **All cloud apps**
6. **Conditions → Locations:**
   - Include **All locations**
   - Exclude → **Countries/Regions → India**
7. **Access controls → Grant → Block access**
8. Click **Create**

✅ This simulates geofencing your Azure access — great for high-security teams or compliance.

---

### 💡 Tips:
- Combine **MFA + Conditional Access** for strong layered security.
- You can apply these only to specific test users to avoid locking yourself out.
- Use the **What If** tool in Conditional Access to preview the effect of policies.

---

📸 Bonus points if you:
- Capture screenshots of MFA enforcement
- Document or simulate Conditional Access scenarios
- Reflect on how these controls would apply to real organizations

---


🔗 [← Back to Main Lab Guide](../README.md)