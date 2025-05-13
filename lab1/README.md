
# Lab 1: Create a Virtual Machine using VirtualBox (Detailed)

## 🎯 Objective
Set up a virtual machine using Oracle VirtualBox and install Ubuntu. This lab covers downloading software, configuration, and installation steps.

---

## 🧰 Prerequisites
- A Windows/macOS/Linux laptop with at least 8GB RAM and 20GB free space

---

## 1️⃣ Download and Install VirtualBox

1. Visit [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)
2. Choose the installer for your operating system (Windows/Mac/Linux)
3. Run the installer and complete the setup

![Step 1 - VirtualBox Download](images/step1_virtualbox_download.png)
![Step 2 - VirtualBox Install](images/step2_virtualbox_install.png)

---

## 2️⃣ Download Ubuntu ISO

1. Go to [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)
2. Choose the latest LTS version (e.g., Ubuntu 22.04 LTS)
3. Save the ISO file to your computer

![Step 3 - Ubuntu ISO Download](images/step3_ubuntu_iso.png)

---

## 3️⃣ Create a New VM in VirtualBox

1. Open VirtualBox and click **New**
2. Enter name: `Ubuntu-VM`
3. Set Type: Linux | Version: Ubuntu (64-bit)
4. Allocate Memory: **2048 MB**
5. Create a Virtual Hard Disk → VDI → Dynamically Allocated → 20 GB

![Step 4 - VM Settings](images/step4_vm_settings.png)

---

## 4️⃣ Mount Ubuntu ISO and Start Installation

1. Go to Settings → Storage → Empty → Choose disk → Select the downloaded ISO
2. Start the VM → Ubuntu Installer launches
3. Follow on-screen instructions to install Ubuntu
4. Set up username, timezone, disk settings (defaults)

![Step 5 - ISO Mount](images/step5_mount_iso.png)
![Step 6 - Ubuntu Installer](images/step6_ubuntu_install.png)

---

## 5️⃣ Post-Installation Tasks

1. Log in to Ubuntu
2. Open Terminal and update:
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```
3. Take a snapshot in VirtualBox

![Step 7 - Ubuntu Desktop](images/step7_ubuntu_desktop.png)

---

## ✅ Outcome
You now have a working Ubuntu VM inside VirtualBox.
