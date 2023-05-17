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
