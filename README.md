<h1 align="center">osTicket: Prerequisites and Installation</h1>

<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png"/>
</p>

<h2>Overview</h2>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Tutorial Guidelines</h2>

<h3>Step 1: Creating a virtual machine</h3>

[VM creation tutorial](https://github.com/Mwajiduddin/How-to-create-a-virtual-machine-in-Microsoft-Azure)

Log in Azure, go into Virtual machines, create a new Resource group, name it, select a region, choose Windows 10 Pro as the image, select a size with atleast 2 VCPUs since we need the processing power to run the osTicket program, create a username and password, check the Licensing box at the bottom left corner, click on "Review + create" and after the validation process click "Create."

<p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e1.png" />
</p>

<p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e2.png" />
</p>



<h3>Step 2: Enabling Internet Information Services (IIS) and installing CGI, PHP Manager, and Rewrite Module in your VM</h3>

Log into your Windows 10 Pro VM using Remote Desktop Connection, search "Control Panel" in the Windows search bar, click on "Programs", select "Turn Windows feature on or off", check the box next to "Internet Information Services" and expand it, expand "World Wide Web Services", expand "Application Development Features", check the CGI box and press OK. CGI installs PHP Manager which is necessary for osTicket to run.

<p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e3.png" />
</p>

<p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e4.png" />
</p>

After CGI is done installing, download and install both [PHP Manager](https://drive.google.com/file/d/1RHsNd4eWIOwaNpj3JW4vzzmzNUH86wY_/view) and [Rewrite Module](https://drive.google.com/file/d/1tIK9GZBKj1JyUP87eewxgdNqn9pZmVmY/view) in your virtual machine. 

<p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e5.png" />
</p>

<h3>Step 3: Creating PHP folder in C:\\ and downloading more files</h3>
 
Go to your VM's C:\\ path and create a new folder called "PHP." Then download [PHP 7.3.8](https://drive.google.com/file/d/1snNMtLdCOpMtkCyD4mvl9yOOmvVIp9fP/view), you'll be asked if you want to keep this download folder so select "Keep". 

 <p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e6.png" />
</p>

 <p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e7.png" />
</p>

 <p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e8.png" />
</p>

Extract its content into the new PHP folder by right clicking on the download folder, selecting the "Extract All" and choosing the path of the PHP folder you made in your C: drive. 

<p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e9.png" />
</p>

<p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e10.png" />
</p>

Download and install both [Microsoft Visual C++](https://drive.google.com/file/d/1s1OsGF3-ioO0_9LYizPRiVuIkb3lFJgH/view) and [MySQL Server](https://drive.google.com/file/d/1_OWh9p7VQLcrB0q_V7qT8yHl0xo5gv7z/view). When installing MySQL Server, select the "Typical" setup and launch it after installing. When launching, select the "Standard Configuration" option, proceed next to create your root password (keep it simple) and then finish installing MySQL Server. 

<p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e11.png" />
</p>

<p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e12.png" />
</p>

<p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e13.png" />
</p>
 
<h3>Step 4: Registering PHP in IIS and downloading osTicket</h3>

Search up "IIS" in the Windows search bar, run it as adminstrator, click on "PHP Manager", then click on "Register new PHP version", select the path of where php-cgi.exe is located then restart IIS.

<p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e14.png" />
</p>

<p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e15.png" />
</p>


<p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e16.png" />
</p>


Now [download osTicket](https://drive.google.com/file/d/1VeVXKlzHDRjeaVUL99ptq7qYbrbXdFxJ/view), once done copy the "upload" folder inside the osTicket download folder to this path C:\inetpub\wwwroot then rename the "upload" folder to "osTicket", go back to IIS and restart it.

<p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e17.png" />
</p>

Then click on the bottom arrow underneath "Sites" and "Default Web Site", select the osTicket folder and click on "Browse*:80(http)" where you will be prompted to the osTicket website on your web browser. 

<p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e18.png" />
</p>

<h3>Step 4: Enabling extentions on osTicket, disabling Inheritance and enabling Permissions</h3>

Go back to IIS, select "PHP Manager" in the osTicket folder, click on "Enable or disable an extention" at the bottom, then enable "php_imap.dll", "php_intl.dll", "php_opcache.dll" by selecting the file, clicking on "Enable" at the top right corner and now refresh the osTicket website in your browser.

<p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e19.png" />
</p>

<p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e20.png" />
</p>



After that go to C:\inetpub\wwwroot\osTicket\include, rename the "ost-sampleconfig.php" to "ost-config.php". Then right click on that file, go to Properties, select "Advanced" in the "Security" tab, click on "Disable Inheritance" -> "Remove all inherited permissions from this object", click on "Add" -> "Select a principal", type in "everyone" in the box, click "Check Names" and OK. Tick the box "Full Control" then hit "Apply" and OK.

<p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e21.png" />
</p>

<p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e22.png" />
</p>

<p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e23.png" />
</p>

<h3>Step 5: Setting up osTicket in your browser</h3>

Go back to osTicket site in your browser, select Continue at the bottom, and fill in the blanks of your own making. 

<p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e24.png" />
</p>


Download and install [HeidiSQL](https://docs.google.com/document/d/1WovrX2DaS9xkfaSr4LXyB4YnnWpXIgPCMMbbfgHmGVw/edit) and launch it after installing. Skip the update if prompted, click on "New" at the bottom left, type in the password that you made when installed MySQL Server and hit "Open." 

<p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e25.png" />
</p>

Right click "Unnamed", hover to "Create new", select "Database", name it "osTicket" and press OK. Now we can fill in the last portion of the osTicket website, remember our MySQL username is "root", click on "Install Now" and now you've successfully installed osTicket!

<p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e26.png" />
</p>

<p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e27.png" />
</p>

<h3>Step 6 : Cleaning up and logging in as an Admin</h3>

We're almost done with this section, we just need to clean up a bit and we start by deleting the "setup" folder that can be found from this path C:\inetpub\wwwroot\osTicket.

<p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e28.png" />
</p>

Now we need to reset the permission of the "ost-config.php" to "read only" and this file can be found from this path C:\inetpub\wwwroot\osTicket\include, right click it, go to "Properties", click on "Advanced" on the "Security" tab, select "Everyone", hit "Edit", just leave the "Read" and "Read and Execute" boxes ticked and press Apply and OK.

<p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e29.png" />
</p>

Now we will try to login in osTicket as an Admin that we created. 

Copy and paste this link in your browser: http://localhost/osTicket/scp/login.php, type in your credentials and you should be able to log in osTicket.

<p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e30.png" />
</p>

<p align="center">
<img src="https://github.com/Mwajiduddin/Mwajiduddin/blob/main/images/e31.png" />
</p>

  >**Note**: *Don't delete your virtual machine right now as the next tutorial continues on from this point.*






