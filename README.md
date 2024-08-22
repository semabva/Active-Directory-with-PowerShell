# ActiveDirectoryLab

## Description

This project demonstrates the creation of an Active Directory home lab environment with the use of Oracle VM Virtualbox. A creation of a Domain Controller (DC) is made on Microsoft Server 2019, along with Active Directory (AD). To simulate a large business environment, a creation of over 1000 users in AD is made with the help of a PowerShell script. 

## Environments Used

- **Oracle VM Virtualbox**
- **Microsoft Server 2019**
- **Windows 10** (22H2)

> Download the files above beforehand, as those are large and will take some time.

## Hardware Requirement

- *Minimum* : 2 GB on Domain Controller & 2 GB on Domain VMs
- *Recommended* : 4 GB on Domain Controller & 4 GB on Domain VMs

> For this lab a minimum of the systems total RAM should not be less then 8GB. The hosting system (your own computer) should preferably have more, as it will speed things up and make all things smoother/faster. 

## Languages and Utilities Used

- **Active Directory**
- **PowerShell**
- **CMD**
  
## Links

- **Oracle VMware:** https://www.virtualbox.org/wiki/Downloads
- **Microsoft Server 2019:** https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019
- **Windows 10 ISO:** https://www.microsoft.com/en-us/software-download/windows10

# Network Diagram
![](https://i.imgur.com/TiLTphN.png)


## Download Win 10

1. Go to https://www.microsoft.com/en-us/software-download/windows10 - click *"Download Now"* - Follow Installation

![](https://i.imgur.com/HzBDUAH.png)

3. Download *"Media Creation Tool"* - Open it to create Win10 ISO-file. 

4. Chose ISO-creation 
![](https://i.imgur.com/VgSk4mR.png)
5. Chose ISO-configuration 
![](https://i.imgur.com/YgfIjfL.png)

4. Wait for file to download.
   
![](https://i.imgur.com/6CndqKY.png)

## Download Win Server 10

1. Go to https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019 and download the Windows Server 2019 ISO-file. It might take some time, so make sure to enjoy a bit of coffee meanwhile :)
![](https://i.imgur.com/e3PLNpr.png)

## Download VirtualBox + Extension Pack

1. Download Oracle VM VirtualBox from https://www.virtualbox.org/wiki/Downloads. Choose your Operating System, for this installation Windows will work just fine. ![](https://i.imgur.com/m6yDb8z.png)

2. Install Oracle VM VirtualBox 
	- Open the Setup file from where you saved your downloaded file and press *"Next"* ![](https://i.imgur.com/uKIwmwF.png)
	- Choose your installation location if you want by pressing "*Browse*". Then press "*Next*". ![](https://i.imgur.com/hn1hRL2.png)

	- Press "*Next*" a few times and then "*Install*", once the installation is done press "*Finish*" ![](https://i.imgur.com/D8QE3Jh.png)


3. Add Extension Pack from Step 1 above, and follow the Installation process.

## Open Oracle VMWare & Create DC

1. Open the VMWare and click *"New"* and choose a name for your VM. I chose *"DC"* for convenience. Also, chose location of the ISO-image, along with the edition. Make sure to mark the *"Skip Unattended Installation"* click *"Next"*. 
![](https://i.imgur.com/wILYnAt.png)

2. Allocate enough Hardware resources to your VM. I suggest at least 4GB of RAM and 20GB of HDD Storage. ![](https://i.imgur.com/Fu0mxCq.png)
	![](https://i.imgur.com/tTU4roq.png)
3. Once you are happy with the specs of the VM, follow through the rest of the installation.

4. One thing that might be useful is the *ability to Copy/Paste & Drag/Drop* things between your computer and the VM, therefore I recommend changing a setting that allows for that. It's done under the *"Settings" and "Advanced tab"*. ![](https://i.imgur.com/4LbcdvK.png)
5. This DC will have *2 Network Interface Cards (NIC)*, also called *Network Adapters*, one for access to the Internet and one for the Internal network. Additional Network Adapter can be added under the *"Network"* setting. 
   ![](https://i.imgur.com/C1p3Fmy.png)
	![](https://i.imgur.com/uHoprGH.png)

## Install Windows Server 2019

1. To start the DC VM click the "Start" button. ![](https://i.imgur.com/FC7zmX2.png)
2. Begin Installation of Win Server 2019 by choosing your Language and Time options. ![](https://i.imgur.com/FSiLKkY.png)
3. Choose the "Windows Server 2019 Standard Evaluation with Desktop Experience". ![](https://i.imgur.com/hKeqNVL.png)
4. Follow the process, and chose the "Custom" Installation. ![](https://i.imgur.com/wvRhHKV.png)
5. Chose Storage for the Installation, since this VM only has one HDD, the choice is simple. ![](https://i.imgur.com/dRPRphk.png)
6. The Installation process might take a while with reboots and blackscreens. Make sure to not touch anything and let the installation complete. While the installation goes on, take a break and relax for a while. 
7. Once the Installation is done, make sure to set a password for you Administrator account.  ![](https://i.imgur.com/FIRFIMQ.png)
8. *To log in you have to press "Ctrl+Alt+Delete"*, however VM's can be tricky in that sense.
	Here is how to do it: Go to top toolbar, under: *"Input"* --> *"Keyboard"* --> *"Insert Ctrl+Alt+Delete"*. 

9. Close all the tabs and windows.
10. To ensure a better quality of life experience, with a smoother mouse, ability to make the VM window bigger etc. Install *"Guest Additions CD"* under the tab *"Devices"*, it is found in the *upper left corner of your VM*

![](https://i.imgur.com/TN6wIli.png)

11. Click the "*File Explorer*" on the taskbar, navigate to "*This PC*" and double-click the "*irtualBox Guest Additions*".![](https://i.imgur.com/CvenSzg.png)

12. Double-click the "*Windows-Additions-amd64*" and follow the installation by clicking "*Next*" on everything. 
13. Once done click the "*I want to manually reboot later*" and "*Next*".
14. Now shut down the VM, and restart it in VirtualBox. ![](https://i.imgur.com/IlizOOb.png)

## IP Adressing Setup

>The diagram tells us that our NIC 1 will get Internet from our router. Our NIC 2 however needs some configuration to work properly. Lets do that now.

1. For convenience lets rename this VM to *DC* so it's easy identified. *Right click the Start Icon* -> *System* ![](https://i.imgur.com/4fXOmI9.png)
2. *Rename this PC* and Reboot the computer.![](https://i.imgur.com/hLUelXI.png)

2. Identify the NIC by going to *Control Panel* -> *Network and Internet* -> *Network Connections* - there should be 2 NIC's. Usually named something like "Ethernet 1" etc.
	Lets find out which is for the Internet and which one is the Internal one.

3. *Doubleclick Ethernet 1* -> *Details* and the routers IP adress is visible in the *IPv4 DNS Server*. There is also an IPv4 address and a regular subnetmas (255.255.255.0). Thus this is the NIC that is connected to the Internet. ![](https://i.imgur.com/AY2V38t.png)

4. Rename it for conveniences sake to e.g *"INTERNET NIC"*.
5. Rename the second one to something like: *"Internal"*
6. Time to configure the IP addresses for the Internal NIC. *Doubleclick on Internal* -> click *"Internet Protocol verion 4 (TCP/IPv4)* and assign addresses below. ![](https://i.imgur.com/luNia6H.png)

7. Depending on the architecture of the network the IP addresses might vary, for this setup the IP address of the Internal NIC is *172.16.0.1* and submask of *255.255.255.0*.
   
	- The *Default gateway is empty*.
	- The DNS will be set to *127.0.0.1* which is an loopback address referring to itself, in this case the DC which will serve as its own DNS, as well as the DNS of the Client VM that will be connected to the DC. 


## Install AD & DS

>In this step we will perform the installation of Active Directory along with Domain Services. Active Directory Domain Services (AD DS) is a Microsoft tool that helps manage users, passwords, and access to files on a network. It makes things easier for administrators and keeps everything secure.

1. Go to *Server Manager* by clicking *Start* and opening *Server Manager* ![](https://i.imgur.com/eEJ71UU.png)
2. Click *Add roles and features* -> *Chose server* (there is only one named DC here)![](https://i.imgur.com/ieOUcC7.png)


3. Make sure to click the right option here *Active Directory Domain Services* ![](https://i.imgur.com/xyjjmS9.png)
4. Click *Add Features*. 

![](https://i.imgur.com/VtRd4C8.png)

5. Click *Next and Install*. 

![](https://i.imgur.com/dtxVb7F.png)

6. Now the AD software is installed, but the Domain creation remains, lets do that now. Click the *flag* followed by *"Promote this server to a domain controller"*.![](https://i.imgur.com/GLMy9qe.png)
7. Click *Add a new forest* and name it whatever you want and click *Next*![](https://i.imgur.com/SMgVIWF.png)
8. Set a password for (*DSRM*) in case you need to restore the Directory Services.![](https://i.imgur.com/sjK1O9C.png)
9. Now click *Next* until the *Install* button is shown, then click on that. This process might take a little while, just wait it out, afterwards the machine will restart. 
10. Once the machine reboots, login and now lets create a dedicated admin accout for ourselves, instead of using the built in one.
11. So, click *Start* and under *Windows Administrative Tools* click *Active Directory Users and Computers* ![](https://i.imgur.com/1RhAKsc.png)
12. Click on your *domain name* -> *New* -> *Organizational Unit* ![](https://i.imgur.com/0qSbwPp.png)
13. Name the OU to something suiting, like *ADMINS* 

![](https://i.imgur.com/kfMsMty.png)

14. *Create a new user* under the OU that was just created.

![](https://i.imgur.com/IIbEUVU.png)

15. Add First and Last name, along with a User logon name. It is common to use some sort of special naming for admin accounts, for example putting an *"a-"* prior to the name.

![](https://i.imgur.com/kzgs6A5.png)

16. Set a Password and press *Next*

![](https://i.imgur.com/ncCdBgk.png)

17. Now it's time to add this user to the *Domain Admins Group* by *Right clicking the user* -> *Properties* -> *Member Of* -> *Add* -> type in *"Domain Admins"* and click *Check Names* followed by pressing the *OK* ![](https://i.imgur.com/IFWqncD.png)
18. Now press *Apply* and confirm that the user member is now in the Domain Admins group, then press *OK*![](https://i.imgur.com/aLcSqbx.png)
19. Now lets *Sign out* and *Login as our new user*.

![](https://i.imgur.com/NducZse.png) ![](https://i.imgur.com/0Ux4R3g.png)

20. Done!

## Install RAS/NAT

> The purpose of this is to allow the Client on the Internal Virtual Network to be able and access the Internet through the Domain Controller (DC).

1. Go to the *Server Manager* under the *Start* menu. ![](https://i.imgur.com/5TFbUXx.png)
2. Click *Add roles and features*, click *Next* until you come to *Server Roles*, there click the *Remote Access* ![](https://i.imgur.com/hGIiKMh.png)
3. Click *Routing*.

![](https://i.imgur.com/X00rjwV.png)

4. And *Add Features*.

![](https://i.imgur.com/VPTOU7w.png)

5. Then click *Next* all the way and then *Install*, this will take a little while.
6. Once the installation is done, *Close* and go to *Tools* up in the right corner, followed by *Routing and Remote Access*. ![](https://i.imgur.com/goMLpnd.png)
7. This will open the Control Panel for Routing and Remote Access. Once there *Right click* on *DC* and chose *Configure and Enable Routing and Remote Access*.

![](https://i.imgur.com/sY6ZRXs.png)

8. Once there lick *Next* and chose *Network adress translation (NAT)![](https://i.imgur.com/tLSerKc.png)
9. Then choose the public interface, this is why naming the NIC's in the beginning makes things easier now. Click *Next*![](https://i.imgur.com/8I3KjaX.png)
10. Done! Time to set up the DHCP Server for the upcoming client.

## DHCP Setup

> This setup *allows the DC to distribute IP addresses to clients automatically*, with a set *lease time*, which in turn will allow the Client on the Virtual Network to access the internet. 

1. Once more navigate to *Add roles and features*, click *Next* and choose your *DC* server. Once here click *DHCP Server* and *Add Featyure* followed by *Next* and *Install*![](https://i.imgur.com/BrplHRd.png)
2. Once done, click *Close*.

![](https://i.imgur.com/etahNIP.png)

3. Great, now navigate to *Tools* and *DHCP*. ![](https://i.imgur.com/a37ge50.png)
4. Now lets set a scope of IP addresses that the DHCP will be handing out to clients by *Clicking* on IPv4 and chooseing *New Scope*![](https://i.imgur.com/RyyvGFN.png)
5. Set a name that for the scope, I went with the IP range to make it easier to see and click *Next*![](https://i.imgur.com/fgyWDCJ.png)
6. As seen in the diagram for this lab environment the scope of IP addresses is set to what is seen in the picture. *Length* can be set to *24* as that will give the network 254 available hosts. Click *Next*![](https://i.imgur.com/DFI2WYB.png)
7. *Lease duration* is simply put: *How long will an IP address be given to a device*. For a homelab like this, it can be whatever you like. If this was real environment, then it depends on that environment. The longer the lease, the longer that particular IP is locked to an device. Once lease is set click *Next*![](https://i.imgur.com/ogMzi1T.png)
8. Click *Configure options* and click *Next*![](https://i.imgur.com/C50OvuE.png)
9. Now its time to *specify the routers IP address*, in this case its the DC that serves as the router for the Internal Virtual Network, thus the DC's IP address is set. *Set the IP Adress* and click *Add* then *Next* ![](https://i.imgur.com/uBApXd3.png)
10. Here we see the DC's IP Address is added, click *Next*.

![](https://i.imgur.com/OybEeXY.png)

11. Click *Next*![](https://i.imgur.com/gyuLOcC.png)
12. *Activate the scope* and press *Next*![](https://i.imgur.com/tDamMjg.png)
13. Done! Time to get the PowerShell script going, that will add around 1000 users to the AD.

## Adding Users to AD with PowerShell Script.

>This PowerShell script will add around 1000 users to Active Directory.

As done earlier under: ("*Create DC, point 4*".) when setting up the DC Virtual Machine by allowing for *Copy/Paste* and *Clip/Drop* we can *copy/paste* the PowerShell script directly to the VM from our own computer. 

1. *Add your name to* "names.txt" file and save the file.
2. Click on *Start* --> *Windows PowerShell ISE* --> Rightclick *More* --> *Run as Administrator*.
3. Click *Yes* when asked for User Account Control.
4. Click on *Open* in top left corner. Locate the Powershell script that should be on the Desktop in a folder. *Open the script*.
![](https://i.imgur.com/4gFDciW.png)

5. By default we can't run scripts in Win Server, but since this is a lab-environment and we want to run the script so users can be added to AD, a Powershell command is needed.
   Run: *Set-ExecutionPolicy Unrestricted* and *click* "*Yes to all*".

![](https://i.imgur.com/NJaHzi2.png)

6. Navigate to the folder where the PowerShell script is.
![](https://i.imgur.com/nk9SzPu.png)

8. *Run the script* by navigating to the directory where the PowerShell script is and *click* "Play" in the top toolbar.
![](https://i.imgur.com/UOcpsuW.png)

## Create VM 2 (Client 1)

> Time to create a new VM that will be connected to the private Network.

1. In *Oracle VM* click on *New* and give this VM a name and chose a version. Then click on *next* and *add your hardware specifications.*
![](https://i.imgur.com/9oWN2wh.png)

2. Once the VM is set-up *right-click* and go to *settings* and navigate to *network* and under *adapter 1* choose *Internal Network* instead of the default NAT.

![](https://i.imgur.com/ttHzW4N.png)

3. Once done, *start the VM* by clicking on it.
4. Chose the location of the *Win10.iso* file downloaded earlier and proceed.
![](https://i.imgur.com/UCc97QS.png)
5. Follow the Installations and *skip the product key*.
![](https://i.imgur.com/Nis4aW0.png)
6. Choose *Windows 10 Pro* and click *next*

![](https://i.imgur.com/tONDaNQ.png)


7. Proceed and chose *Custom Installation* and click *next*
8. Wait for the installation to complete, and *don't press anything meanwhile*.
   ![](https://i.imgur.com/39q7oI1.png)

9. Fill in your *region* and *language* etc. Then click on *Continue with limited setup*
   ![](https://i.imgur.com/2PtANZ8.png)

10. *Fill in a username* and *skip password*
![](https://i.imgur.com/Mox3dgT.png)

11. I usually *turn off every option*.

## Join Domain

> The VM is up and running and now it needs to be given a proper name and join the Domain.

1. *Renaming the PC to "Client1"* by *right clicking "Start"* --> *System*

![](https://i.imgur.com/0UeHR6l.png)

2. *Scroll down to "Rename this PC (advanced)*
![](https://i.imgur.com/zqSKKDo.png)

3. Click the *Change* button

![](https://i.imgur.com/35QN5U1.png)

4. Set the computer name and make it *Member of Domain*.

![](https://i.imgur.com/XEyQVvb.png)

5. Enter *User name* and *Password*
![](https://i.imgur.com/XWqxO1d.png)

6. *Reboot the PC*

We are all done! This lab simulates a simple corporate environment network.
Hope you enjoyed this lab. Take care! 

## Credits

This project was made with the help of Josh Madakors video which can be found [Here](https://youtu.be/MHsI8hJmggI?si=4qqk4cJWn9cxtlSX)


