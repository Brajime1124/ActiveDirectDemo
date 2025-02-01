<h1>Active Directory Home Lab</h1>

<h2>Prerequisites</h2>
<ul>
    <li>A computer with enough resources (at least 16GB RAM, SSD recommended)</li>
    <li><strong>Virtualization software</strong> (VMware Workstation, VirtualBox, or Hyper-V)</li>
    <li><strong>Windows Server ISO</strong> (2019 or 2022) – available from Microsoft’s evaluation site</li>
    <li><strong>Windows 10/11 ISO</strong> (for client machines)</li>
</ul>

<h2>Step 1: Set Up the Virtualization Environment</h2>
<ol>
    <li>Install your preferred virtualization software.</li>
    <li>Create a new <strong>Virtual Machine (VM)</strong> for Windows Server:
        <ul>
            <li>Allocate at least <strong>4GB RAM, 2 CPU cores</strong></li>
            <li>Set the virtual disk to <strong>50GB</strong> or more</li>
            <li>Mount the <strong>Windows Server ISO</strong> and begin installation</li>
        </ul>
    </li>
    <li>Create additional VMs for Windows 10/11 clients following similar steps.</li>
</ol>

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
