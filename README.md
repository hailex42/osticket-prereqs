<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Create Windows Virtual Machine
- Download [osTicket](https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD) installation files and unzip to Windows-vm


<h2>Installation Steps</h2>

![image](https://github.com/user-attachments/assets/c36e4f58-13ae-4e69-bbec-f4f44cde0f4b)

<p>
Install / Enable IIS in Windows WITH CGI
World Wide Web Services -> Application Development Features -> [X] CGI

From the “osTicket-Installation-Files” folder, install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)

From the “osTicket-Installation-Files” folder install the Rewrite Module (rewrite_amd64_en-US.msi)
</p>

![image](https://github.com/user-attachments/assets/7ebcd31f-992e-4e1a-a51d-d9061494b3bb)

<p>
Create the directory C:\PHP

From the “osTicket-Installation-Files” folder, unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder

From the “osTicket-Installation-Files” folder, install VC_redist.x86.exe.

From the “osTicket-Installation-Files” folder, install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
Typical Setup ->
Launch Configuration Wizard (after install) ->
Standard Configuration ->
Username: root
Password: root

</p>
<br />

![image](https://github.com/user-attachments/assets/9aee5774-75e1-4d04-9da3-fbb3a3742c5a)

<p>Open IIS as an Admin

Register PHP from within IIS (PHP Manager -> C:\PHP\php-cgi.exe)

Reload IIS (Open IIS, Stop and Start the server)
</p>

![image](https://github.com/user-attachments/assets/89447d07-bb76-4b2b-8013-1ea58509396b)
<p>
Install osTicket v1.15.8
From the “osTicket-Installation-Files” folder, 
Unzip “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”
Within “c:\inetpub\wwwroot”, Rename “upload” to “osTicket” </p>

![image](https://github.com/user-attachments/assets/96463a88-9809-4fcf-8687-bbaeec5f359e)
<p>
Reload IIS (Open IIS, Stop and Start the server)
Go to sites -> Default -> osTicket
On the right, click “Browse *:80”
</p>

![image](https://github.com/user-attachments/assets/1a214cb3-2a69-467f-9489-784eb5d60d7b)
<p>Note that some extensions are not enabled
Go back to IIS, sites -> Default -> osTicket
Double-click PHP Manager
Click “Enable or disable an extension”
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll
Refresh the osTicket site in your browser, observe the changes
</p>

![image](https://github.com/user-attachments/assets/5bf60b41-ddd4-46f6-8bc6-d48754a1f762)
<p> 
Rename: ost-config.php
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
</p>

![image](https://github.com/user-attachments/assets/f41ba263-6632-4acd-b5e4-6da30918ff0a)
<p>
Assign Permissions: ost-config.php
Disable inheritance -> Remove All
New Permissions -> Everyone -> All
</p>
![image](https://github.com/user-attachments/assets/1aad6aa9-fea9-43bc-a0d6-9c321b55e346)

<p>
From the “osTicket-Installation-Files” folder, install HeidiSQL.
Open Heidi SQL
Create a new session, root/root
Connect to the session
Create a database called “osTicket”

</p>


![image](https://github.com/user-attachments/assets/2ecf9dd8-f90a-4721-90a0-002131c8a491)

<p>Continue Setting up osTicket in the browser (click Continue)
Name Helpdesk
Default email (receives email from customers)
</p>
