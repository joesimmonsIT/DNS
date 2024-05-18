<p align="center">
<img src="https://i.imgur.com/qxQbpWh.png"/>
</p>

<h1> Exploring and Understanding Domain Name System (DNS) </h1>
This tutorial highlights the exploration and understanding of Domain Name System (DNS).<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- DNS Manager
- Command Prompt

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Check for Mainframe Record
- Creating an A-Record for Mainframe
- Mainframe Traffic
- DNS Cache
- Changing Mainframe IP Address
- Mainframe Traffic with New IP Address
- Creating CNAME Record

<h2> Check for Mainframe Record </h2>

<p>
<img src="https://i.imgur.com/LxpH2vi.png"/>
</p>
<p>
Go to Azure Portal (Portal.Azure.com). <br /> <br />
Select "Virtual Machines" icon. <br /> <br />
Select "Client-1". <br /> <br />
Copy Public IP Address. <br /> <br />
Go to "Remote Desktop Connection". <br /> <br />
Paste Public IP Address. <br /> <br />
Select "Connect". <br /> <br />
Select "More choices". <br /> <br />
Select "Use a different account". <br /> <br />
Enter Domain Admin Username. <br /> <br />
Enter Domain Admin Password. <br /> <br />
Select "Ok". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/C3Cf9oC.png"/>
</p>
<p>
Go to Azure Portal (Portal.Azure.com). <br /> <br />
Select "Virtual Machines" icon. <br /> <br />
Select "DC-1". <br /> <br />
Copy Public IP Address. <br /> <br />
Go to "Remote Desktop Connection". <br /> <br />
Paste Public IP Address. <br /> <br />
Select "Connect". <br /> <br />
Enter Domain Admin Username. <br /> <br />
Enter Domain Admin Password. <br /> <br />
Select "Ok". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/yex7ORX.png"/>
</p>
<p>
Open Remote Desktop Connection for Client-1. <br /> <br />
Go to the "Windows Pane". <br /> <br />
Type "cmd" in the search bar and Press Enter. <br /> <br />
Type "whoami" and Press Enter. <br /> <br />
Type "hostname" and Press Enter. <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/IumMFiw.png"/>
</p>
<p>
Type "ping (spacebar) mainframe" and Press Enter. <br /> <br />
Mainframe is not registered with the DNS hence the error message. <br /> <br />
</p>
<br />

<h2> Creating an A-Record for Mainframe </h2>
<p>
<img src="https://i.imgur.com/MqXXFy7.png"/>
</p>
<p>
Open Remote Desktop Connection to "DC-1". <br /> <br />
Select "Tools". <br /> <br />
Select "DNS". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/BmfTJEc.png"/>
</p>
<p>
Select "Forward Lookup Zones".
</p>
<br />

<p>
<img src="https://i.imgur.com/Ma0qvHU.png"/>
</p>
<p>
Observe the Private IP Addresses for Client-1 and DC-1.
</p>
<br />

<p>
<img src="https://i.imgur.com/K4q2EHV.png"/>
</p>
<p>
Right Click inside the white space. <br /> <br />
Select "New Host". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/ZGotP0k.png"/>
</p>
<p>
Name: mainframe.
</p>
<br />

<p>
<img src="https://i.imgur.com/OuEDDeX.png"/>
</p>
<p>
Go to "Virtual Machines". <br /> <br />
Select "DC-1". <br /> <br />
Collapse "Networking". <br /> <br />
Select "Network settings". <br /> <br />
Select "Network interface". <br /> <br />
Copy Private IP Address. <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/15HeKub.png"/>
</p>
<p>
Go back to DNS. <br /> <br />
Paste Private IP Address. <br /> <br />
Select "Add Host". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/s5p4E7H.png"/>
</p>
<p>
Select "Ok".
</p>
<br />

<p>
<img src="https://i.imgur.com/d9w0vQw.png"/>
</p>
<p>
Observe that "mainframe" has been added to the DNS.
</p>
<br />

<h2> Mainframe Traffic </h2>
<p>
<img src="https://i.imgur.com/vcuehvT.png"/>
</p>
<p>
Go back to "Command Prompt". <br /> <br />
Type "ping(spacebar) mainframe" and Press Enter. <br /> <br />
Observe the traffic for mainframe. <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/irhrgh7.png"/>
</p>
<p>
Type "nslookup (spacebar) mainframe" and Press Enter. <br /> <br />
Observe that "DC-1" and "mainframe" have the same Private IP Address since we configured it that way. <br /> <br />
</p>
<br />

<h2> DNS Cache </h2>
<p>
<img src="https://i.imgur.com/yfrV2Kb.png"/>
<img src="https://i.imgur.com/wKyjZ1A.png"/>
</p>
<p>
Type "ipconfig (spacebar)/displaydns" and Press Enter. <br /> <br />
Observe the DNS data for "mainframe" and "DC-1". <br /> <br />
</p>
<br />

<h2> Changing Mainframe IP Address </h2>
<p>
<img src="https://i.imgur.com/4d4rOVv.png"/>
</p>
<p>
Return to the DNS Manager. <br /> <br />
Select "mainframe". <br /> <br />
Right Click and Select "Properties". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/aANh6FV.png"/>
</p>
<p>
Change IP Address to 8.8.8.8. <br /> <br />
Select "Apply". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/WmDMCOz.png"/>
</p>
<p>
Select "Ok".
</p>
<br />

<p>
<img src="https://i.imgur.com/GO6TJ9t.png"/>
</p>
<p>
Observe "mainframe" IP Address has been updated to 8.8.8.8
</p>
<br />

<h2> Mainframe Traffic with New IP Address </h2>
<p>
<img src="https://i.imgur.com/O6rdC5s.png"/>
</p>
<p>
Go back to "Command Prompt". <br /> <br />
Type "ping (spacebar) mainframe" and Press Enter. <br /> <br />
Observe the traffic results are still displaying the original IP Address since the DNS was not flushed. <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/xToZfxx.png"/>
<img src="https://i.imgur.com/sywm0t9.png"/>
</p>
<p>
Type "ipconfig (spacebar)/displaydns" and Press Enter. <br /> <br />
The DNS Data is also remaining the same since the DNS was not flushed yet. <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/WtX4pSY.png"/>
</p>
<p>
Type "ipconfig (spacebar)/flushdns" and Press Enter. <br /> <br />
Observe the message "operation requires elevation", the DNS can only be flushed when application opened as administrator. <br /> <br />
Close application. <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/r9LGOoc.png"/>
</p>
<p>
Go to "Windows Pane". <br /> <br />
Type "cmd" in the search bar. <br /> <br />
Select "Run as administrator". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/eXIxwRj.png"/>
</p>
<p>
Type "ipconfig (spacebar)/displaydns and Press Enter. <br /> <br />
Observe DNS Data. <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/AxHLxyN.png"/>
</p>
<p>
Type "ipconfig (spacebar)/flushdns" and Press Enter. <br /> <br />
DNS has successfully been flushed. <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/G9skEnq.png"/>
</p>
<p>
Type "ping (spacebar) mainframe" and Press Enter. <br /> <br />
Observe the new mainframe traffic from updated IP Address. <br /> <br />
</p>
<br />

<h2> Creating CNAME Record </h2>
<p>
<img src="https://i.imgur.com/0yzgRCg.png"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/VN1qHMA.png"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/z7cHD40.png"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/2b5CDTW.png"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/yB5DSYk.png"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/SuwUE3f.png"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

