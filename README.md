<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial covers the setup process process for the open-source help desk ticketing system, osTicket this guide will cover all the requirements and detailed steps for installation .<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Azure Virtual Machine 
- osTicket Installation files
- Heidi SQL

<h2>Installation Steps</h2>

<p>
  First Lets start by creating the virtual machine in Azure.
<img width="746" alt="Image" src="https://github.com/user-attachments/assets/52d05515-90fc-40df-beb5-bf793a873be7" />
</p>
<p>
To begin this process, we first create a resource group called osTicket in Microsoft Azure.  Then, inside this resource group, establish a virtual machine.  We will make sure the virtual machine (VM) has at least two virtual CPUs and runs a Windows 10 Pro image.  OsTicket will be installed and utilized in this virtual machine.
<br />

<p>
<img width="200" alt="Image" src="https://github.com/user-attachments/assets/7e9bacd5-1801-4a3b-bc88-488696cc4967" />
</p>
<p>
Next, use Remote Desktop Protocol (RDP) to access the virtual machine.  To create the RDP connection, copy the Public IPv4 address for the virtual machine that appears in the Azure site. Enter the lab user credentials that were set up during the virtual machine's setup.
</p>
<br />

<p>

<img width="345" alt="Image" src="https://github.com/user-attachments/assets/623cad41-fc23-474d-aa42-a80448953c45" />
</p>
<p>
  After connecting to the virtual machine, click the Control Panel and select Turn Windows Features On or Off to activate IIS.  Locate Internet Information Services (IIS) by scrolling down, then click the checkbox to activate the service.
</p>
<br />

<p>
<img width="345" alt="Image" src="https://github.com/user-attachments/assets/556096ea-6273-4065-8850-e335ce6e9293" />
</p>
<p>
  Open the tab for Internet information services.  Expand the World Wide Web Services tab after scrolling to it.  Locate and expand the application development features tab.  Scroll down to the CGI tab, then select the checkbox to activate the service.  
</p>
<br />


<p>
<img src="https://i.imgur.com/jdy6kVT.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD Next, use the provided download link to obtain all the necessary files to install and launch osTicket.  
From the osTicket Installation folder, locate and install PHP Manager to proceed with the setup.
</p>
<br />

<p>
<img src="https://i.imgur.com/BraQ2Sp.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Within the same folder, install the Rewrite Module to continue configuring the environment.
</p>
<br />

<p>
<img src="https://i.imgur.com/3G7QEou.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/BJ7pQXn.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create the directory C:\PHP. Unzip the file PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and extract all its contents into the C:\PHP directory.
</p>
<br />

<p>
<img src="https://i.imgur.com/vnapOUJ.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Install VC_redist.x86.exe from the osTicket Installation folder to ensure the necessary Visual C++ Redistributable components are in place.
</p>
<br />

<p>
<img src="https://i.imgur.com/6Ni4PkJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Install MySQL 5.5.62 (mysql-5.5.62-win32.msi) from the osTicket Installation folder to set up the MySQL database server.
</p>
<br />

<p>
<img src="https://i.imgur.com/HFBKqHa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open IIS Manager as an administrator. Register PHP within IIS by configuring the necessary settings. Afterward, restart the server by selecting Restart in the IIS Manager.
</p>
<br />

<p>
<img src="https://i.imgur.com/dUEDOI2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From the osTicket-Installation-Files folder, unzip osTicket-v1.15.8.zip and copy the upload folder to C:\inetpub\wwwroot. Then, within C:\inetpub\wwwroot, rename the upload folder to osTicket.
</p>
<br />

<p>
<img src="https://i.imgur.com/ofoOo0Z.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Return to IIS Manager and restart the server. Enable the necessary PHP extensions by navigating to Sites -> Default -> osTicket, then double-click PHP Manager. Select "Disable or enable an extension" and enable php_intl.dll, php_opcache.dll, and php_imap.dll. Afterward, refresh the osTicket web server and verify that the Intl Extension is now enabled.
</p>
<br />

<p>
<img src="https://i.imgur.com/JEdBG6b.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Navigate to C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php and rename the file to ost-config.php in the same directory (C:\inetpub\wwwroot\osTicket\include).
</p>
<br />

<p>
<img src="https://i.imgur.com/vFIs9DL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Assign the appropriate permissions to ost-config.php by right-clicking the file and selecting Properties. In the Security tab, disable inheritance, remove all existing permissions, and grant Everyone full access.
</p>
<br />

<p>
<img src="https://i.imgur.com/HZnNtf2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Finally, proceed with the osTicket setup in your browser by clicking Continue. Assign a name to your helpdesk as desired, and select a default email address to receive customer-submitted ticket notifications. Congrats! 
</p>
<br />
