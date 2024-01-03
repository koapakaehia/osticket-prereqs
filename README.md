<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used</h2>

- Windows 10 (21H2)
- Mac OS

<h2>List of Prerequisites</h2>

- Set up IIS on Windows, ensuring CGI and Common HTTP features are installed/enabled
- Install the Web Platform Installer
- Set up MySQL, including the configuration of a username and password
- Configure permissions and execute the osTicket installation
- Enable the necessary osTicket extensions: php_imap.dll, php_intl.dll, php_opcache.dll

<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>Start by creating a Resource Group (RG) for our Windows 10 Virtual Machine on Microsoft Azure</b>

- Name your new RG "RG-osTicket."
- Choose the region where the server will be located; in this case, select West US 3.
- Click on "Review + Create," ensure that validation passes, and then click "Create."
Step 4: Continue with the creation of your Windows 10 Virtual Machine.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>Search for "Virtual Machine (VM)" in the search bar and proceed to create a Windows 10 VM with 4 vCPUs within the resource group created in the previous step.</b>

- Name it VM1
- Region will be the same as your RG.
- Create your username and password, so we can RDP (Remote Desktop Protocol) into it later.
- Don't forget to scroll down and check liscencing box.
- Click Next: Disks and Next: Networking.
- Allow a new Virtual Network (Vnet) to be created when making your Virtual Machine.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>After the creation process is complete, we will utilize remote desktop to connect to our VM.</b>

- Retrieve the public IP address and paste it into Microsoft Remote Desktop (download it for Mac OS if needed).
- Connect to the VM using the previously set username and password.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>Continue with the certification and access https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6 to install the required prerequisites.</b>

- Retrieve the public IP address and paste it into Microsoft Remote Desktop (download it for Mac OS if needed).
- Connect to the VM using the previously set username and password.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>In your Windows VM, open the Run dialog, type "control," and navigate to Programs.</b>

- Access "Turn Windows features on or off."
- Install/Enable IIS (Internet Information Services) in Windows with CGI and Common HTTP Features.
- Include IIS Management Console in the installation.
<p>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>If you have followed the instructions accurately, open your web browser and enter 127.0.0.1; it should redirect you to the IIS "page."</b>
<p>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>With the installation files provided earlier, we can now proceed to install the prerequisites.</b>

- Download and install PHP Manager for IIS using the file named PHPManagerForIIS_V1.5.0.msi.
<p>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
- Download and install the Rewrite Module using the file named rewrite_amd64_en-US.msi.
<p>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
- Establish the directory C:\PHP.
<p>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
- Download PHP version 7.3.8 from the provided link (php-7.3.8-nts-Win32-VC15-x86.zip) and extract the contents into the C:\PHP directory.
<p>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
- Download and install VC_redist.x86.exe.
<p>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>Download and install MySQL version 5.5.62 using the file named mysql-5.5.62-win32.msi and follow the typical setup.</b>

- Launch the Configuration Wizard after installation.
- Choose the Standard Configuration option.
- Create a password as part of the configuration process.
<p>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
- Launch IIS with administrative privileges.
<p>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>Register PHP within IIS.</b>

- Restart IIS.
<p>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
- Download and install osTicket version 1.15.8 from the provided files.
<p>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
- To apply changes, restart Internet Information Services (IIS).
<p>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>Navigate to "Sites," then select "Default," and finally, access "osTicket."</b>

- On the right, click "Browse *:80" to access the designated site.
<p>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>Please take note that some extensions are not currently enabled."</b>

- Return to IIS, go to "Sites," then choose "Default," and access "osTicket." Double-click on PHP Manager.
- Click on "Enable or disable an extension."
<p>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>Enable the following extensions:</b>

- php_imap.dll
- php_intl.dll
- php_opcache.dll
<p>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
- Refresh the osTicket site in your browser and observe the changes.
<p>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>Before proceeding, rename the file ost-config.php.</b>

- Copy the contents from C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php.
- Paste the contents into C:\inetpub\wwwroot\osTicket\include\ost-config.php.
<p>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>Assign permissions to the ost-config.php file.</b>

- Disable inheritance and remove all existing permissions.
- Apply new permissions for Everyone with full access.
<p>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
- Grant full control and apply the permissions.
<p>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>Proceed with the osTicket setup.</b>

- Name: Helpdesk
- Default email (receives email from customers): [Enter Email]
- Enter Admin info:
- Name: [Admin Name]
- Email: [Admin Email]
- Create a username and password.
- Complete the next step before continuing.
<p>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>Download and install HeidiSQL.</b>

- Open Heidi SQL.
- Create a new session with the credentials root/Password1.
- Connect to the session.
- Create a database named "osTicket."
<p>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>Continue the osTicket setup in your browser and scroll down to the Database Settings section.</b>

- MySQL Database: osTicket
- MySQL Username: root
- MySQL Password: Password1
- Click "Install Now!"
<p>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>Perform the final cleanup steps.</b>

- Delete: C:\inetpub\wwwroot\osTicket\setup
- Set Permissions to "Read" only for: C:\inetpub\wwwroot\osTicket\include\ost-config.php.
<p>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>Great! You've completed the installation of osTicket on a Windows 10 Virtual Machine using Microsoft Azure.</b>

- Access your help desk login page: http://localhost/osTicket/scp/login.php
- For end-users, use the osTicket URL: http://localhost/osTicket/
<p>
</p>
<br />
