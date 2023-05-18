<h1 align="center">osTicket: Prerequisites and Installation</h1>

<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png"/>
</p>

<h1>Introduction</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Tutorial Guideline</h2>

<h3>Step 1: Creating a virtual machine</h3>

Log in Azure, go into Virtual machines, create a new Resource group, name it, select a region, chose Windows 10 Pro as the image, select a size with atleast 2 VCPUs since we need the processing power to run the osTicket program, create a username and password, check the Licensing box at the bottom left corner, click on "Review + create" and after the validation process click "Create."

[VM creation process](https://github.com/Mwajiduddin/How-to-create-a-virtual-machine-in-Microsoft-Azure)

<h3>Step 2: Enabling Internet Information Services (IIS) and installing CGI, PHP Manager, and Rewrite Module in your VM</h3>

Log into your Windows 10 Pro VM using Remote Desktop Connection, search "Control Panel" in the Windows search bar, click on "Programs", select "Turn Windows feature on or off", check the box next to "Internet Information Services" and expand it, expand "World Wide Web Services", expand "Application Development Features", check the CGI box and press OK. CGI install PHP Manager which is necessary for osTicket to run.

After CGI is done installing, download and install both [PHP Manager](https://drive.google.com/file/d/1RHsNd4eWIOwaNpj3JW4vzzmzNUH86wY_/view) and [Rewrite Module](https://drive.google.com/file/d/1tIK9GZBKj1JyUP87eewxgdNqn9pZmVmY/view) in your virtual machine. 

<h3>Step 3: Creating PHP folder in C:\\ and downloading more files</h3>
 
 Go to your VM's C:\\ path and create a new folder called "PHP." Then download [PHP 7.3.8](https://drive.google.com/file/d/1snNMtLdCOpMtkCyD4mvl9yOOmvVIp9fP/view), you'll be asked if you want to keep this download folder so select "Keep". Extract its content into the new PHP folder by right clicking on the download folder and selecting the "Extract All" and select the path of the PHP folder you made in your C: drive. Download and install both [Microsoft Visual C++](https://drive.google.com/file/d/1s1OsGF3-ioO0_9LYizPRiVuIkb3lFJgH/view) and [MySQL Server](https://drive.google.com/file/d/1_OWh9p7VQLcrB0q_V7qT8yHl0xo5gv7z/view). When installing MySQL Server, select the "Typical" setup and launch it after installing. When launching, select the "Standard Configuration" option and proceed next to create  your root password and then finish installing MySQL Server. 
 
 <h3>Step 4: Register PHP in IIS and downloading osTicket</h3>

Search up "IIS" in the Windows search bar and run it as adminstrator, click on "PHP Manager", then click on "Register new PHP version", select the path of php-cgi.exe is located then restart IIS. Now [download osTicket](https://drive.google.com/file/d/1VeVXKlzHDRjeaVUL99ptq7qYbrbXdFxJ/view) and once done copy the "upload" folder inside the osTicket download folder to this path C:\inetpub\wwwroot then rename the "upload" folder to "osTicket" and go back to IIS and restart it. Then click on the bottom arrow underneath "Sites" and "Default Web Site", select the osTicket folder and click on "Browse*:80(http)" where you will be prompted by the osTicket website. 

<h3>Step 4: Enabling extentions on osTicket, disabling Inheritance and enabling Permissions</h3>

Go back to IIS, select "PHP Manager" in the osTicket folder, click on "Enable or disable an extention" at the bottom, then enable "php_imap.dll", "php_intl.dll", "php_opcache.dll" by selecting the file and click on "Enable" at the top right corner and now refresh the osTicket website in your browser. After that go to C:\inetpub\wwwroot\osTicket\include and rename the "ost-sampleconfig.php" to "ost-config.php". Then right click on the file, go to Properties, select "Advanced" in the "Security" tab, click on "Disable Inheritance" -> "Remove all inherited permissions from this object", click on "Add" -> "Select a principal", type in "everyone" in the box, click on "Check Names" and OK. Tick the box "Full Control" then hit "Apply" and OK.

<h3>Step 5: Setting up osTicket in your browser</h3>

Go back to osTicket site in your browser, select Continue at the bottom, and fill in the blanks of your own making. Download and install [HeidiSQL](https://docs.google.com/document/d/1WovrX2DaS9xkfaSr4LXyB4YnnWpXIgPCMMbbfgHmGVw/edit) and launch it after installing. Skip the update if prompted, click on "New" at the bottom left, type in the password that you made when installed MySQL Server and hit "Open." Right click it "Unnamed", hover to "Create new", select "Database", name it "osTicket" and press OK. Now we can fill in the last portion of the osTicket website, remember our MySQL username is "root", click on "Install Now" and now you've successfully installed osTicket!



<h3>Step 6 : Cleaning up and logging in as an Admin</h3>

We're almost done with this section, we just need to clean up a bit and we start by deleting the "setup" folder that can be found from this path C:\inetpub\wwwroot\osTicket. Now we need to reset the permission of the "ost-config.php" to "read only" and this file can be found from this path C:\inetpub\wwwroot\osTicket\include, right click it, go to "Properties", click on "Advanced" on the "Security" tab, select "Everyone", hit "Edit", just leave the "Read" and "Read and Execute" boxes ticked and press Apply and OK.

Now we will try to login into osTicket as an Admin that we created. So copy and paste this link in your browser: http://localhost/osTicket/scp/login.php, type in your credentials and you should be able to log in osTicket.



















































