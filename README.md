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
<img width="385" alt="Image" src="https://github.com/user-attachments/assets/f192d391-393b-4e78-b353-435ee2f7d065" />
</p>
<p>
  Next, we will use This Link - https://drive.usercontent.google.com/download?id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD&export=download&authuser=0
to obtain all the necessary files to install and launch osTicket.  
To continue with the setup, find and install PHP Manager in the osTicket Installation folder.
</p>
<br />

<p>
<img width="382" alt="Image" src="https://github.com/user-attachments/assets/a6cce174-506f-41ee-a830-005850c25d5c" />
</p>
<p>
Next locate and install the IIS URL Rewrite Module by navigating to the same folder to proceed with the configuration.
</p>
<br />

<p>
<img width="457" alt="Image" src="https://github.com/user-attachments/assets/3b1754c4-4ef7-42da-962a-5c56b5936b6c" />
<img width="464" alt="Image" src="https://github.com/user-attachments/assets/c0f853c8-0b21-4410-944d-c338b5392c60" />
</p>
<p>
Create a new folder on the C drive, name the new folder "PHP"; the directory should be C:\PHP.  After that, extract all of the contents from the PHP 7.3.8 file (php-7.3.8-nts-Win32-VC15-x86.zip) and place it in the C:\PHP directory.
</p>
<br />

<p>
<img width="362" alt="Image" src="https://github.com/user-attachments/assets/93dc21a1-eeb4-4afe-a7fd-52dcfed89c2f" />
</p>
<p>
To make sure the required Visual C++ Redistributable components are present, we must then install VC_redist.x86.exe from the osTicket Installation folder.
</p>
<br />

<p>
<img width="383" alt="Image" src="https://github.com/user-attachments/assets/783f5224-c571-440b-81aa-e9aff07fa15c" />
  
<img width="371" alt="Image" src="https://github.com/user-attachments/assets/d60b626f-9dc5-4fac-98ee-06c978dad18f" />

<img width="371" alt="Image" src="https://github.com/user-attachments/assets/efd83c7e-d16b-44ca-9501-3d2a5c9b542b" />
</p>
<p>
The MySQL 5.5.62 will then be installed from the osTicket Installation folder. The MySQL instance configuration wizard will start running after it has finished installing, and we will proceed with the standard installation options.  Following that, we will generate a new root password by clicking the "modify security setting options" box. 
</p>
<br />

<p>
<img width="415" alt="Image" src="https://github.com/user-attachments/assets/4f47735f-a21d-41c7-9740-9d863d6c96a3" />

![Image](https://github.com/user-attachments/assets/a4647320-5f7f-4b11-9cf7-b07a8cb2709c)
  
</p>
<p>
Next, as an administrator, launch IIS Manager.  We will configure the required parameters and register PHP under IIS. To acomplish this we will select the path to the php excecutable file as "C:\PHP\php-cgi.exe". After that, choose Restart in the IIS Manager to restart the server.
</p>
<br />

<p>
<img width="593" alt="Image" src="https://github.com/user-attachments/assets/3cf862cd-fe9e-4c7d-8a21-ff5131d738bc" />
</p>
<p>
Unzip osTicket-v1.15.8.zip from the osTicket-Installation-Files folder, then move the upload folder to C:\inetpub\wwwroot.  Next, rename the upload folder to osTicket inside C:\inetpub\wwwroot.
</p>
<br />

<p>
<img width="473" alt="Image" src="https://github.com/user-attachments/assets/bce13b79-ddd4-4f56-b512-ee0bb449a3ea" />
</p>
<p>
Return to IIS Manager and restart the server. Enable the necessary PHP extensions by navigating to Sites -> Default -> osTicket, then double-click PHP Manager. Select "Disable or enable an extension" and enable php_intl.dll, php_opcache.dll, and php_imap.dll. Afterward, refresh the osTicket web server and verify that the Intl Extension is now enabled.
</p>
<br />

<p>
<img width="593" alt="Image" src="https://github.com/user-attachments/assets/09303baf-31b0-4253-9860-8ea88013616a" />
</p>
<p>
Navigate to C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php and rename the file to ost-config.php in the same directory (C:\inetpub\wwwroot\osTicket\include).
</p>
<br />

<p>
<img src="https://github-production-user-asset-6210df.s3.amazonaws.com/195221381/421403298-8393fd78-795a-446a-84f2-9016d32e68c7.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250312%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250312T135522Z&X-Amz-Expires=300&X-Amz-Signature=33134198c84ab018740b0a70631b16bc4b79f1024498bcf09085bd463afdc678&X-Amz-SignedHeaders=host"/>
</p>
<p>
Assign the appropriate permissions to ost-config.php by right-clicking the file and selecting Properties. In the Security tab, disable inheritance, remove all existing permissions, and grant Everyone full access.
</p>
<br />

<p>
<img width="306" alt="Image" src="https://github.com/user-attachments/assets/5e75fa4c-bb09-4489-b0b0-24439447ddbb" />
</p>
<p>
Finally, proceed with the osTicket setup in your browser by clicking Continue. Assign a name to your helpdesk as desired, and select a default email address to receive customer-submitted ticket notifications. 
</p>
<br />

<p>
<img width="445" alt="Image" src="https://github.com/user-attachments/assets/a70d31ed-e7c9-4681-87ca-7075726f67d6" />
</p>
<p>

In order to properly finish the database confguration we must first navigate to the osTicket-Installation-Files” folder to install HediSQL.
</p>
<br />


<p>
<img width="629" alt="Image" src="https://github.com/user-attachments/assets/16202a32-6a9e-431e-84ac-bf3dd0403e40" />
</p>
<p>

Once properly instlled we will create a new seesion using the HediSQL application and connect to it. Afterwards we will create a new database called 'osTicket'.
</p>
<br />

<p>
<img width="629" alt="Image" src="https://github.com/user-attachments/assets/e0b78adb-49ab-4758-80c9-1f16d6cdd25f" />
</p>
<p>

We can now go back to the osTicket set up page in the browser and enter the required information for MySQL database.
</p>
<br />

<p>
<img width="629" alt="Image" src="https://github.com/user-attachments/assets/3d764527-d579-47c8-a6f9-199f0ef5d281" />
</p>
<p>

With all the setup now complete we have succsesfully installed osTicket with no errors. 
</p>
<br />

<p>
<img width="629" alt="Image" src="https://github.com/user-attachments/assets/9ffbda05-2792-4fc5-9a4a-82ec99781b02" />
</p>
<p>

As a final check we will borse to the help dess login page at 'http://localhost/osTicket/scp/login.php'. Once we login the page will display this message with
</p>
<br />
