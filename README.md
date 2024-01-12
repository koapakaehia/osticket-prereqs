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
<img src="https://i.imgur.com/QAw8InZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
<img src="https://i.imgur.com/ADelcgy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<b>2. Create Windows 10 VM:</b>

- Name: VM1
- Username: labuser (customizable)
- Password: osTicketPassword1! (customizable)
- Allow VM to create a new Virtual Network (Vnet).

<p>
<img src="https://i.imgur.com/lG0Q9S0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
- Log in to the Virtual Machine using Remote Desktop for macOS.
</p>
<br />

<p>
<img src="https://i.imgur.com/58id1JR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>PART 2: INSTALLATION</b>

1. Prepare Installation Files:
  - Download osTicket installation files from [Google Drive](https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6).
</p>
<br />

<p>
<img src="https://i.imgur.com/0ruwH46.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
2. IIS and Additional Components:

  a. Install/Enable IIS in Windows:
  - Open the control panel:
    - Search the Run dialog.
    - Type control and press Enter.
</p>
<br />

<p>
<img src="https://i.imgur.com/yrR8bol.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  - Navigate to "Programs" -> "Programs and Features":
    - Click on "Turn Windows features on or off" on the left side.
  - World Wide Web Services -> Application Development Features:
    - [X] CGI
    - [X] Common HTTP Features
  - Internet Information Services -> Web Management Tools -> IIS Management Console:
    - [X] IIS Management Console
</p>
<br />

<p>
<img src="https://i.imgur.com/nwd3MO4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
b. - If done correctly, open up your web browser and type 127.0.0.1 and it should redirect you IIS "page."
</p>
<br />

<p>
<img src="https://i.imgur.com/r00IkuZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
b. Download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi).
</p>
<br />

<p>
<img src="https://i.imgur.com/35dGFfL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
c. Download and install the Rewrite Module (rewrite_amd64_en-US.msi).
</p>
<br />

<p>
<img src="https://i.imgur.com/kpYSWsQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

d. Create the directory C:\PHP.
  - In your Files
  - Go to "This PC"
  - "C Drive"
  - Create New folder "PHP"
</p>
<br />

<p>
<img src="https://i.imgur.com/sXE98PZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
e. Download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip), unzip into C:\PHP.
  - Download the file and right click once finished.
    - Select "Extract All"
  - Browse and extract to your newly created folder "C:\PHP."
  - If prompted, choose "Keep" for the file.
  - If difficulties persist, try downloading via Google Chrome.
</p>
<br />

<p>
<img src="https://i.imgur.com/EHn1UF0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
f. Download and install VC_redist.x86.exe.
</p>
<br />

<p>
<img src="https://i.imgur.com/urg4bSZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/SjJqnGO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
<img src="https://i.imgur.com/KTNm3yq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>4. Configure IIS and PHP:</b>

a. Open IIS as an Admin.
  - In windows search IIS.
  - Right, click and select Run as administrator.
</p>
<br />

<p>
<img src="https://i.imgur.com/2F2Cqlt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/pvkZ7V4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

b. Register PHP within IIS.
- In PHP Manager
  - Select Register New  PHP Version  
  - Click on the 3 dots to browse
  - Go to This Pc > C Drive > PHP > and select php-cgi

c. Reload IIS (Stop and Start the server).
</p>
<br />

<p>
<img src="https://i.imgur.com/5wzYb2C.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/q7kSXdB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>5. Install osTicket v1.15.8:</b>

a. Download osTicket from the Installation Files Folder.

b. Extract and copy the "upload" folder to C:\inetpub\wwwroot.

c. Rename "upload" to "osTicket" within C:\inetpub\wwwroot.
</p>
<br />

<p>
<img src="https://i.imgur.com/uXfY2vy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
d. Restart IIS (Stop and Start the server).
<p>
<img src="https://i.imgur.com/TCOCvbf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/JdSOfyN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

e. In IIS. Go to sites -> Default -> osTicket.
  - On the right, click "Browse *:80."
  - The osTicket installer should now be accessible.
</p>
<br />

<p>
<img src="https://i.imgur.com/ouLqy5q.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/JZnx7rM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>6. Enable PHP Extensions:</b>

a. In IIS, go to sites -> Default -> osTicket.

b. Double-click PHP Manager.
<p>
<img src="https://i.imgur.com/JZnx7rM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/iBumfAm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

c. Click "Enable or disable an extension":
  - Enable: php_imap.dll
  - Enable: php_intl.dll
  - Enable: php_opcache.dll.
<p>
<img src="https://i.imgur.com/1oWeJG3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
d. Refresh the osTicket site in your browser and observe changes.
</p>
<br />

<p>
<img src="https://i.imgur.com/FniQptc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>7. Configure osTicket:</b>

a. Rename: ost-config.php
  - From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
  - To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
<p>
<img src="https://i.imgur.com/WgueIIX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

b. Assign Permissions to ost-config.php:
  - Right-click ost-config.php -> properties.
  - Select Security -> Advanced.
<p>
<img src="https://i.imgur.com/f1TzJeV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  - Disable inheritance -> Remove All.
<p>
<img src="https://i.imgur.com/YqArCHa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 
  - Select Security -> Advanced.
  - Permissions -> Enable Inheritance.
  - For Name type "Everyone" -> Check Namnes -> OK
  - Check all basics permisions (not Special Permissions) -> OK.
  - Verify Permissions for Everyone -> OK.
</p>
<br />

<p>
<img src="https://i.imgur.com/pG3PrQi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/asHyxrj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>8. Setting up osTicket:</b>

a. Continue setting up osTicket in the browser by clicking "Continue."
  - Name Helpdesk
  - Default email (receives email from customers)
  - Enter Admin info
  - Create username and password
  - Do next step before continuing
</p>
<br />

<p>
<img src="https://i.imgur.com/XRBu44i.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>9. Database Setup:</b>

a. Download and install HeidiSQL.
  - Check Launch HeidiSQL -> Finish.  
<p>
<img src="https://i.imgur.com/YogFn08.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/2K2yVnT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

b. Open Heidi SQL, create a new session (root/Password1), and connect.

c. Create a database called "osTicket."
<p>
<img src="https://i.imgur.com/tJsnoGP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

d. Continue setting up osTicket in the browser:
  - MySQL Database: osTicket
  - MySQL Username: root
  - MySQL Password: Password1
  - Click "Install Now!"
</p>
<br />

<p>
<img src="https://i.imgur.com/z4x0jbY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>10. Verify Installation:</b>

- Congratulations! Check for errors by browsing to the help desk login page: http://localhost/osTicket/scp/login.php.
</p>
<br />

<p>
<img src="https://i.imgur.com/UQFbcdB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b>Clean Up</b>

- Delete: C:\inetpub\wwwroot\osTicket\setup.
<p>
<img src="https://i.imgur.com/L5KhfM5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

- Set Permissions to "Read" only for C:\inetpub\wwwroot\osTicket\include\ost-config.php.

<b>That concludes the installation of osTicket on a Windows 10 Virtual Machine using Microsoft Azure.</b>
  - Help Desk Login Page: http://localhost/osTicket/scp/login.php
  - End Users osTicket URL: http://localhost/osTicket/
</p>
<br />
