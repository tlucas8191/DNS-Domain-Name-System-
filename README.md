<p align="center">
<img src="https://i.imgur.com/roNiQqw.png" alt="DNS _ IPS ADDRESS Logo"/>
</p>

<h1>Building Intuition for DNS</h1>
In this tutorial, we look to get a basic understanding of what DNS (Domain Name System) is and how it works. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Understanding DNS](https://www.youtube.com/watch?v=MqBGjappbTk)

<h2>Environments and Technologies Prerequisites and Requirements Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Active Directory Domain Services running in Azure on VM DC-1 (requirement)
- A client machine running in Azure on VM Client-1 and joined to the domain (requirement)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Windows Server 2022

<h2>High-Level Steps</h2>

- Inspect DNS A-Records on the server (hostname to IP Address mappings)
- Create some of our own A-Records on the server and observe from the client
- Delete records from the server and inspect/clear the client DNS cache to gain understanding
- Discuss CNAME records (mapping one name to another name)

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/FUP0ll8.png" height="80%" width="80%" alt="Logging into DC-1"/>
<img src="https://i.imgur.com/3SoeoqC.png" height="80%" width="80%" alt="Logging into Client-1"/>
</p>
<p>
In this step, we logged into DC-1 as domain admin account and also logged into Client-1 as an admin.
</p>
<br />

<p>
<img src="https://i.imgur.com/pINBayL.png" height="80%" width="80%" alt="pinging 'mainframe', it fails"/>
<img src="https://i.imgur.com/8yl2YSZ.png" height="80%" width="80%" alt="pic of why pinging 'mainframe' fails"/>
</p>
<p>
In this step, inside of Client-1, we tried to ping “mainframe”, but it fails because “mainframe” does not have a DNS record.
</p>
<br />

<p>
<img src="https://i.imgur.com/SnTAP69.png" height="80%" width="80%" alt="create A-Record for 'mainframe'"/>
<img src="https://i.imgur.com/KoyVZI3.png" height="80%" width="80%" alt="create A-Record for 'mainframe'2"/>
<img src="https://i.imgur.com/p7jOuVZ.png" height="80%" width="80%" alt="ping 'mainframe' again, it works"/>
<img src="https://i.imgur.com/ouajxEg.png" height="80%" width="80%" alt="ping 'mainframe' again, it works 2"/>
</p>
<p>
In this step, we created a DNS A-record on DC-1 for “mainframe” and we had it point to DC-1’s Private IP address (which is 10.0.0.4).  Then we went back to Client-1 and tried to ping it and observed that it worked the second time.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create a DNS A-record on DC-1 for “mainframe” and have it point to DC-1’s Private IP address
Go back to Client-1 and try to ping it. Observe that it works.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create a DNS A-record on DC-1 for “mainframe” and have it point to DC-1’s Private IP address
Go back to Client-1 and try to ping it. Observe that it works.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create a DNS A-record on DC-1 for “mainframe” and have it point to DC-1’s Private IP address
Go back to Client-1 and try to ping it. Observe that it works.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create a DNS A-record on DC-1 for “mainframe” and have it point to DC-1’s Private IP address
Go back to Client-1 and try to ping it. Observe that it works.
</p>
<br />
