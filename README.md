# 🖥️ Active Directory Home Lab Setup  

This guide walks you through setting up an **Active Directory (AD) Home Lab** using **Windows Server and Windows 10/11 clients** within a virtualized environment. This project demonstrates IT infrastructure skills, including **networking, domain management, and security policies**.  

---

## 📌 Prerequisites  
Before starting, ensure you have:  
✔ **Virtualization software** (VMware Workstation, VirtualBox, or Hyper-V)  
✔ **Windows Server ISO** and **Windows 10/11 ISO**  
✔ **At least 8GB RAM** (minimum) on your host machine  

---

## **Step 1: Set Up the Virtualization Environment**  

We will create virtual machines (VMs) for both **Windows Server** and **Windows Client**.  

### **1. Install Virtualization Software**  
1. Download and install **VMware Workstation**, **VirtualBox**, or enable **Hyper-V** on Windows.  
2. Open your chosen virtualization platform.  

### **2. Create a Windows Server VM**  
1. **Create a new virtual machine (VM)**.  
2. Assign at least **4GB RAM**, **2 CPU cores**, and a **50GB virtual disk**.  
3. Mount the **Windows Server ISO** to the VM.  
4. Power on the VM and start the Windows installation process.  

### **3. Create Windows 10/11 Client VMs**  
1. Repeat the above steps for Windows 10/11 VMs.  
2. Assign at least **2GB RAM** and **30GB virtual disk**.  
3. Mount the **Windows 10/11 ISO** and begin installation.  

---

## **Step 2: Installing Windows Server and Configuring Basic Settings**  

### **1. Install Windows Server**  
1. Boot the **Windows Server VM** and complete the installation.  
2. Choose **Windows Server with Desktop Experience**.  
3. Set a **strong administrator password** when prompted.  

### **2. Rename the Server**  
1. Open **Settings** → **System** → **About** → **Rename this PC**.  
2. Change the name to `DC01` (Domain Controller 01).  
3. Restart the VM.  

### **3. Assign a Static IP Address**  
1. Open **Network and Sharing Center** → **Change adapter settings**.  
2. Right-click **Ethernet** → **Properties** → Select **Internet Protocol Version 4 (TCP/IPv4)**.  
3. Set the following values:  
   - **IP Address:** `192.168.1.10`  
   - **Subnet Mask:** `255.255.255.0`  
   - **Default Gateway:** `192.168.1.1`  
   - **Preferred DNS Server:** `192.168.1.10`  
4. Click **OK** and close the settings.  

---

## **Step 3: Installing Active Directory Domain Services (AD DS)**  

### **1. Install the Active Directory Role**  
1. Open **Server Manager** → Click **Manage** → **Add Roles and Features**.  
2. Select **Active Directory Domain Services (AD DS)** and click **Next**.  
3. Click **Install** and wait for completion.  

### **2. Promote the Server to a Domain Controller**  
1. In **Server Manager**, click **Promote this server to a domain controller**.  
2. Choose **Add a new forest**, enter `MyLab.local`.  
3. Set a **Directory Services Restore Mode (DSRM) password**.  
4. Click **Install**, then restart the server.  

---

## **Step 4: Configuring Active Directory and DNS**  

### **1. Open Active Directory Users and Computers (ADUC)**  
1. Click **Start**, type `Active Directory Users and Computers`, and open the tool.  

### **2. Create Organizational Units (OUs)**  
1. In **ADUC**, right-click your domain (`MyLab.local`) → **New** → **Organizational Unit**.  
2. Name them:  
   - **Users** (for domain user accounts)  
   - **Computers** (for workstations)  

### **3. Create Test User Accounts**  
1. Right-click **Users OU** → **New** → **User**.  
2. Enter details (e.g., `John Doe, jdoe@MyLab.local`).  
3. Set an initial password and configure settings.  

---

## **Step 5: Connecting a Windows 10/11 Client to the Domain**  

### **1. Configure Client VM Network Settings**  
1. Open **Network and Sharing Center** → **Change adapter settings**.  
2. Right-click **Ethernet** → **Properties** → **Internet Pro


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
