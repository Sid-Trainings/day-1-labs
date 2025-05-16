
# Lab 1: Create a Virtual Machine using VirtualBox (Detailed)

## 🎯 Objective
Set up a virtual machine using Oracle VirtualBox and install Ubuntu. This lab covers downloading software, configuration, and installation steps.

---

## 🧰 Prerequisites
- A Windows/macOS/Linux laptop with at least 8GB RAM and 20GB free space

---

## 1️⃣ Download and Install VMWare Workstation

1. Go to the [Slack Channel](https://join.slack.com/t/iacsd-devopsworkshop/shared_invite/zt-35ykagbls-glqUZ7LtTdIvs8F9lveGjg)
2. Go to Resources
3. Download [VMware Workstation Pro](https://iacsd-devopsworkshop.slack.com/files/U08SEH6UMEX/F08T2HY0ZNV/vmware-workstation-full-17.6.3-24583834.exe)
4. Install the `exe` file

---

## 2️⃣ Download ISO's to your machine

1. Download CentOS ISO from here -> [Download CentOS](https://drive.google.com/file/d/1p4hVBFFjUI8KfuaxKa6rIhiw0Z4G3aD7/view?usp=sharing)

---

## 3️⃣ Create a New VM in VMWare Workstation

1. Open VMware Workstation and click **Create a New Virtual Machine**
2. Click **Next**
3. Select `Installer Disc image file (iso)`
4. Browse to your downloaded CentOS image
5. Click **Next**
6. In the next screen, give your details `Full Name`, `Username`, `Password`, `Confirm Password` and click **Next**
7. In the next scree, choose the location where your VM will be deployed (Can leave default if there is enough space) and click **Next**
8. In the disk size window, click **Store virtual machine as a single disk** and then click **Next**
9. In the hardware scree, click on **Customize Hardware** button
10. In the sub window, go to **Network Adapter** --> In the Network Connection sub window select **Bridged**
11. Click on**Close**
12. Finally click on **Finish**

---

## 4️⃣ Installation will begin

1. Follow on-screen instructions to install Centos
2. Set up Disk
3. Installation Type should **Minimal**
4. Set up username, timezone, disk settings (defaults)

---

## 5️⃣ Post-Installation Tasks

1. Log in to CentOS Server
2. Open Terminal and update:
   ```bash
   sudo yum update -y
   ```
3. Take a snapshot in VMWare Workstation
  - Shutdown the Virtual Machine, using toolbar
  - Wait for it to shutdown
  - On the right side panel, right click on your server name and select **Snapshot --> Take Snapshot**
  - On the Snapshot window, click on **Take Snapshot**

---

## ✅ Outcome
You now have a working CentOS VM inside VirtualBox.
