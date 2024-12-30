
<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

-  Azure Virtual Machine
-  Internet Information Services (IIS)
-  PHP Manager
-  Rewrite Module
-  VC Redist
-  MySQL
-  Heidi SQL
-  osTicket v1.15.8

<h2>Installation Steps</h2>

<img width="818" alt="Screenshot 2024-11-16 at 9 25 07 AM" src="https://github.com/user-attachments/assets/6b87f898-44a8-4453-a1fa-69ff2b758989" />

Before installing any files, you need to ensure that Internet Information Services (IIS) is installed. Since you're setting up osTicket locally, IIS is required for it to work properly. Here's how to enable IIS on your Windows system:
1. Open the Control Panel.
2. Go to Programs, then click on Turn Windows Features On or Off.
3. In the Windows Features dialog, expand Internet Information Services.
4. Expand Web Management Tools and check the box for IIS Management Console.
5. Next, expand World Wide Web Services, then expand Application Development Features.
6. In the Application Development Features section, enable CGI.
7. Click OK to confirm your selections.
After completing these steps, IIS will be enabled on your system, allowing you to proceed with the installation of osTicket.
</p>
<p>

</p>
<br />

<p>
<img width="1280" alt="Screenshot 2024-11-30 at 12 10 05 PM" src="https://github.com/user-attachments/assets/401c3744-c245-4287-ac94-a9ce32b984ce" />
</p>
<p>
Once IIS is installed, the next step is to download and install the PHP Manager for IIS. You can find  PHPManagerforIIS_V1.5.0.msi in the installation files folder. After PHP Manager for IIS is installed, install the rewrite_amd64_en-US.msi installer. This should be done  after the PHP Manager installation.</p>
<br />

<p>
<img width="1280" alt="Screenshot 2024-11-30 at 12 11 53 PM" src="https://github.com/user-attachments/assets/e364648f-06b2-4331-9fe2-753beedcf27a" />
</p>
<p>
Once the Rewrite Module is installed, create a  folder named C:\PHP on your C: drive. This folder will be used to store the contents of PHP 7.3.8 . Next, locate the file php-7.3.8-nts-Win32-VC15-x86.zip  from the installation files. Extract all the files from this zip archive into the newly created C:\PHP directory.</p>
<br />

<img width="1280" alt="Microsoft Visual C+ + 2015-2022" src="https://github.com/user-attachments/assets/a993c541-f056-4558-be14-a0475aca9e10" />


Next,  install VC_redist.x86.exe from the installation files.


<img width="1280" alt="Screenshot 2024-11-30 at 12 20 37 PM" src="https://github.com/user-attachments/assets/29a48e76-3c9b-4e68-a7b6-7c29cf452f16" />


 install MySQL 5.5.62 (mysql-5.5.62-win32.msi) from the installation files folder. During the MySQL setup process, click agree, then click Typical installation option, and proceed with the installation. Once complete, run the Configuration Wizard.
In the Configuration Wizard, click standard configuration and check the option to Install as Windows Service. Make sure  “Launch the MySQL Server automatically” option is enabled. For MySQL credentials, use root as the username and Password1 as the password. Note that in a real-world scenario, stronger credentials should be used.


<img width="1280" alt="Screenshot 2024-11-30 at 12 26 27 PM" src="https://github.com/user-attachments/assets/999f5590-58dd-42be-8134-b81f2224c4c0" />
<img width="1280" alt="Screenshot 2024-11-30 at 12 28 13 PM" src="https://github.com/user-attachments/assets/985a5d54-8ac7-450f-8f5b-8a9abd86be50" />


Before continuing  the osTicket installation, some configurations need to be made in IIS. First, open IIS as an administrator and click PHP Manager. In PHP Manager, click on Register new PHP version. Click Browse,  locate and click the php-cgi.exe file found in the PHP folder created earlier. After registering the PHP version, go back to the IIS Management Console and reload the IIS server to enable the changes.


<img width="1280" alt="Screenshot 2024-11-30 at 12 49 35 PM" src="https://github.com/user-attachments/assets/b72480b3-e934-4831-b1e7-177ee66b785e" />


From the installation files, download osTicket v1.15.8. Extract and copy the "upload" folder to the following path: c:\inetpub\wwwroot. Within the c:\inetpub\wwwroot folder, rename "upload" to "osTicket." Reload the IIS server afterwards.


<img width="1280" alt="Screenshot 2024-11-30 at 12 56 55 PM" src="https://github.com/user-attachments/assets/a255f0f4-db5c-440d-984f-e1d7b51108dc" />
<img width="1280" alt="Screenshot 2024-11-30 at 12 57 12 PM" src="https://github.com/user-attachments/assets/e98e87a9-b878-46f5-8e4b-4e397eb39172" />
<img width="1280" alt="Screenshot 2024-11-30 at 1 00 47 PM" src="https://github.com/user-attachments/assets/8968f9c5-1c9b-4131-b013-09e6a89c94cb" />


In the IIS console, navigate to Sites > Default > osTicket. Click on *browse 80, this will open the installation page for osTicket. Before continuing with the installation, some PHP extensions need to be enabled in IIS. go to PHP Manager within the osTicket menu in IIS. Select Enable or disable an extension, then enable the extensions: php_imap.dll, php_intl.dll, and php_opcache.dll.


<img width="1280" alt="Screenshot 2024-11-30 at 1 02 02 PM" src="https://github.com/user-attachments/assets/ab885304-f62c-430a-aa87-a13a460b1c60" />
<img width="1280" alt="Screenshot 2024-11-30 at 1 05 29 PM" src="https://github.com/user-attachments/assets/5a633473-36f5-4fb8-b072-a402c08ae92f" />


Before you continue installing osTicket, you need to rename a file and adjust its permissions. Go to C:\inetpub\wwwroot\osTicket\include, and rename ost-sampleconfig.php to ost-config.php.
Next, change the permissions for the renamed ost-config.php file. Right-click on the file, click Properties, and go to the Security tab. Click Disable inheritance, then choose to Remove all inherited permissions. After, add new permissions for the everyone group, granting  Full control.


<img width="1280" alt="Screenshot 2024-11-30 at 1 17 38 PM" src="https://github.com/user-attachments/assets/a25e81b3-0cd2-4858-94ca-4883177d6005" />


Download and install HeidiSQL from the installation files. after it’s installed, open HeidiSQL and create a new session. Enter the password you made for the MySQL installation. After connecting, right-click on Unnamed in the session > Create new > Database. Name the database osTicket.


<img width="1280" alt="Congratulations!" src="https://github.com/user-attachments/assets/9a5b1401-6946-4477-9b7e-a40c00ebdc81" />
<img width="1280" alt="Screenshot 2024-11-30 at 1 27 20 PM" src="https://github.com/user-attachments/assets/ff589212-7fec-4ace-9a65-0b9b9800f810" />


In the osTicket browser window, fill in the required information to complete the setup. For  MySQL database credentials, use the same login details you made during the MySQL and HeidiSQL setup.
Once the setup is complete, osTicket should be successfully installed. However, before using osTicket, some cleanup tasks are needed. First, delete the setup folder located in C:\inetpub\wwwroot\osTicket. Then, go to C:\inetpub\wwwroot\osTicket\include, and adjust the permissions for the ost-config.php file. Ensure that the file no longer has full access for Everyone. Change the permissions to Read only.
