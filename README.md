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
<img src="https://i.imgur.com/lBs30V8.png" height="80%" width="80%" alt="ping 'mainframe' again, it works 3"/>
</p>
<p>
In this step, we created a DNS A-record on DC-1 for “mainframe” and we had it point to DC-1’s Private IP address (which is 10.0.0.4).  Then we went back to Client-1 and tried to ping it and observed that it worked the second time.
</p>
<br />

<p>
<img src="https://i.imgur.com/MUkQSpZ.png" height="80%" width="80%" alt="(a) changed 'mainframe's' A-Record address to 8.8.8.8"/>
<img src="https://i.imgur.com/Il0MLCy.png" height="80%" width="80%" alt="(b) changed 'mainframe's' A-Record address to 8.8.8.8"/>
</p>
<p>
In this step, we went back to DC-1 and changed mainframe’s record address (IP address) to 8.8.8.8 .
</p>
<br />

<p>
<img src="https://i.imgur.com/PzgwSae.png" height="80%" width="80%" alt="same IP address 1"/>
<img src="https://i.imgur.com/m9vcUVO.png" height="80%" width="80%" alt="same IP address 2"/>
</p>
<p>
In this step, we went back to Client-1 and pinged “mainframe” again. We observed that it still pinged the old address (10.0.0.4).  The DNS cache also showed the same IP address for mainframe when observed.
</p>
<br />

<p>
<img src="https://i.imgur.com/IIQPHJB.png" height="80%" width="80%" alt="DNS flush 1"/>
<img src="https://i.imgur.com/X6zhW56.png" height="80%" width="80%" alt="DNS flush 2"/>
<img src="https://i.imgur.com/tYTmsqg.png" height="80%" width="80%" alt="DNS flush 3"/>
</p>
<p>
In this step, we flushed the DNS cache and observed that the cache is empty.
</p>
<br />

<p>
<img src="https://i.imgur.com/5DnOiYO.png" height="80%" width="80%" alt="New DNS record"/>
<img src="https://i.imgur.com/X8yc4ht.png" height="80%" width="80%" alt="New DNS record 2"/>
</p>
<p>
After we flushed the DNS cache, we attempted to ping “mainframe” again and observe the address of the new record is showing up (8.8.8.8)  The reason is because at first, Client-1 used the local cache instead of the DNS server in order to retrieve mainframe's IP address.  When we flushed the local cache and cleared all of the data out, Client-1 was forced to ask the DNS server for mainframe's IP address.  And when Client-1 asked the DNS server, it retrieved the updated IP address.
</p>
<br />

<p>
<img src="https://i.imgur.com/qs1Whdu.png" height="80%" width="80%" alt="tried a failed ping to 'search'"/>
</p>
<p>
In this step, we completed a CNAME Record exercise (A CNAME record maps an alias name to an actual IP address-name to name mapping).  We first tried to ping 'search', but the ping failed.
</p>
<br />

<p>
<img src="https://i.imgur.com/pEswut5.png" height="80%" width="80%" alt="created CNAME Record for 'search'"/>
<img src="https://i.imgur.com/f1oq0tm.png" height="80%" width="80%" alt="created CNAME Record for 'search'2"/>
<img src="https://i.imgur.com/nw9QCL1.png" height="80%" width="80%" alt="created CNAME Record for 'search'3"/>
</p>
<p>
In this step, we went back to DC-1 and created a CNAME record that points the host “search” to “www.google.com”.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In the last part of this lab, we went back to Client-1 and attempted to ping “search”, and we observed the results of the CNAME record.  Also, on Client-1, we did an nslookup for “search”, and observed the results of the CNAME record.  The CNAME record for 'search' should point to 'www.google.com'.
</p>
<br />
