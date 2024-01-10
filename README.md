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
<img src="https://i.imgur.com/DfaC9eK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>PART 1: CREATE VIRTUAL MACHINE IN AZURE</b>

<b>1. Create a Resource Group:</b>
- Name: Rg-osTicket
- Choose the same region for all resources.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<b>2. Create Windows 10 VM:</b>

- Name: Vm-osticket
- Username: labuser (customizable)
- Password: osTicketPassword1! (customizable)
- Allow VM to create a new Virtual Network (Vnet).
- Log in to the Virtual Machine using Remote Desktop for macOS.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>PART 2: INSTALLATION</b>

1. Prepare Installation Files:
  - Download osTicket installation files from [Google Drive](https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6).
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
2. IIS and Additional Components:

  a. Install/Enable IIS in Windows:
  - World Wide Web Services -> Application Development Features:
    - [X] CGI
    - [X] Common HTTP Features
  - Internet Information Services -> Web Management Tools -> IIS Management Console:
    - [X] IIS Management Console
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
b. Download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi).
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
c. Download and install the Rewrite Module (rewrite_amd64_en-US.msi).
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
d. Create the directory C:\PHP.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
e. Download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip), unzip into C:\PHP.
  
  - If prompted, choose "Keep" for the file.
  - If difficulties persist, try downloading via Google Chrome.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
f. Download and install VC_redist.x86.exe.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>3. MySQL Installation:</b>

- Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi):
  - Typical Setup.
  - Launch Configuration Wizard after install.
  - Standard Configuration.
  - Set the password to "Password1."
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>4. Configure IIS and PHP:</b>

a. Open IIS as an Admin.

b. Register PHP within IIS.

c. Reload IIS (Stop and Start the server).
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>5. Install osTicket v1.15.8:</b>

a. Download osTicket from the Installation Files Folder.

b. Extract and copy the "upload" folder to C:\inetpub\wwwroot.

c. Rename "upload" to "osTicket" within C:\inetpub\wwwroot.

d. Reload IIS (Stop and Start the server).

e. Go to sites -> Default -> osTicket.
  - On the right, click "Browse *:80."
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>6. Enable PHP Extensions:</b>

a. In IIS, go to sites -> Default -> osTicket.

b. Double-click PHP Manager.

c. Click "Enable or disable an extension":
  - Enable: php_imap.dll
  - Enable: php_intl.dll
  - Enable: php_opcache.dll.

d. Refresh the osTicket site in your browser and observe changes.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>7. Configure osTicket:</b>

a. Rename: ost-config.php
  - From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
  - To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
b. Assign Permissions to ost-config.php:
  - Disable inheritance -> Remove All.
  - New Permissions -> Everyone -> All.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>8. Setting up osTicket:</b>

a. Continue setting up osTicket in the browser by clicking "Continue."

b. Name the Helpdesk and set a default email (to receive customer emails).
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>9. Database Setup:</b>

a. Download and install HeidiSQL.

b. Open Heidi SQL, create a new session (root/Password1), and connect.

c. Create a database called "osTicket."

d. Continue setting up osTicket in the browser:
  - MySQL Database: osTicket
  - MySQL Username: root
  - MySQL Password: Password1
  - Click "Install Now!"
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>10. Verify Installation:</b>

- Congratulations! Check for errors by browsing to the help desk login page: http://localhost/osTicket/scp/login.php.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>Clean Up</b>

- Delete: C:\inetpub\wwwroot\osTicket\setup.
- Set Permissions to "Read" only for C:\inetpub\wwwroot\osTicket\include\ost-config.php.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>Notes:</b>

- Help Desk Login Page: http://localhost/osTicket/scp/login.php
- End Users osTicket URL: http://localhost/osTicket/
</p>
<br />
