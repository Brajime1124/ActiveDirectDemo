<h1>Active Directory Home Lab</h1>

<h2>Prerequisites</h2>
<ul>
    <li>A computer with enough resources (at least 16GB RAM, SSD recommended)</li>
    <li><strong>Virtualization software</strong> (VMware Workstation, VirtualBox, or Hyper-V)</li>
    <li><strong>Windows Server ISO</strong> (2019 or 2022) – available from Microsoft’s evaluation site</li>
    <li><strong>Windows 10/11 ISO</strong> (for client machines)</li>
</ul>

<h2>Step 1: Set Up the Virtualization Environment</h2>

Before we can build an Active Directory (AD) home lab, we need a controlled environment where we can install and configure the necessary systems. To achieve this, we’ll set up a **virtualized network** using a hypervisor of your choice, such as **VMware Workstation, VirtualBox, or Hyper-V**.

### 1. Install a Virtualization Platform
Choose a hypervisor that suits your system’s capabilities and install it. Popular options include:

- **VMware Workstation Pro/Player** – Offers a user-friendly interface and solid performance.
- **VirtualBox** – A free and open-source alternative with broad compatibility.
- **Hyper-V** (Windows only) – Built-in for Windows Pro/Enterprise users.

### 2. Create a Virtual Machine (VM) for Windows Server
Once your hypervisor is installed, create a new VM that will act as your domain controller. Configure it as follows:

- **Memory**: Allocate **at least 4GB RAM** (8GB recommended for better performance).
- **CPU**: Assign **2 CPU cores** to ensure smooth operation.
- **Storage**: Set the virtual disk to **50GB or more**, depending on available space.
- **Network Adapter**: Choose **NAT or Bridged mode**, depending on whether you want the VMs to communicate with your host system.
- **Installation Media**: Mount the **Windows Server ISO** file to begin the installation process.

### 3. Create Additional VMs for Client Machines
To simulate a real-world Active Directory environment, we need client machines to join the domain. Follow similar steps to create one or more **Windows 10 or Windows 11 VMs**, ensuring they have:

- **2GB RAM (minimum)**
- **1 CPU core**
- **30GB of disk space**
- **Network settings that allow communication with the domain controller**

By the end of this step, you should have a **Windows Server VM** ready for installation and **one or more client VMs** prepared to join the domain. Next, we’ll configure the server and set up Active Directory.

<h2>Step 2: Install Windows Server and Configure Basic Settings</h2>
<ol>
    <li>Boot the server VM and install <strong>Windows Server</strong>.</li>
    <li>Set a <strong>strong administrator password</strong>.</li>
    <li>Assign a <strong>static IP address</strong>:
        <ul>
            <li>Open <strong>Network and Sharing Center</strong> → Change adapter settings.</li>
            <li>Configure the Ethernet adapter with a manual IP (e.g., <code>192.168.1.10</code> for the server).</li>
        </ul>
    </li>
    <li>Rename the server to something meaningful (e.g., <code>DC01</code>).</li>
</ol>

<h2>Step 3: Install Active Directory Domain Services (AD DS)</h2>
<ol>
    <li>Open <strong>Server Manager</strong> and select <strong>Add Roles and Features</strong>.</li>
    <li>Choose <strong>Active Directory Domain Services (AD DS)</strong> and install it.</li>
    <li>After installation, <strong>Promote the server to a domain controller</strong>:
        <ul>
            <li>Select <strong>Add a new forest</strong> (e.g., <code>MyLab.local</code>).</li>
            <li>Set a <strong>Directory Services Restore Mode (DSRM) password</strong>.</li>
            <li>Complete the wizard and restart the server.</li>
        </ul>
    </li>
</ol>

<h2>Step 4: Configure Active Directory and DNS</h2>
<p>Once the server is rebooted:</p>
<ul>
    <li>Open <strong>Active Directory Users and Computers (ADUC)</strong>.</li>
    <li>Create <strong>Organizational Units (OUs)</strong> to structure users and computers.</li>
    <li>Create test <strong>user accounts</strong>.</li>
</ul>

<h2>Step 5: Connect a Windows 10/11 Client to the Domain</h2>
<ol>
    <li>Boot the Windows client VM and set a static IP.</li>
    <li>Set the <strong>Preferred DNS</strong> to the server’s IP (e.g., <code>192.168.1.10</code>).</li>
    <li>Open <strong>System Properties</strong> → Change Settings → Change.</li>
    <li>Enter the domain name (<code>MyLab.local</code>) and provide admin credentials.</li>
    <li>Restart the client and log in with a domain user account.</li>
</ol>

<h2>Step 6: Implement Group Policies (GPOs)</h2>
<p>Use <strong>Group Policy Management</strong> to enforce policies:</p>
<ul>
    <li>Enforce password complexity</li>
    <li>Disable USB storage</li>
    <li>Deploy a desktop wallpaper</li>
</ul>

<h2>Step 7: Testing and Managing AD</h2>
<ul>
    <li>Use <strong>Active Directory Users and Computers (ADUC)</strong> to manage users and groups.</li>
    <li>Use <strong>Event Viewer</strong> to monitor domain activity.</li>
    <li>Test logging in from different client machines.</li>
</ul>

<h2>Conclusion</h2>
<p>Setting up an Active Directory home lab is essential for IT professionals looking to gain real-world experience. This lab allows you to explore user management, GPOs, and networking in a controlled environment.</p>
<p>With this foundation, you can expand into more advanced topics like PowerShell automation, hybrid cloud integration, or security hardening.</p>


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
