---
layout: page
title: "Q317099: PRB: &quot;550 Quoted Name Does Not Match IP Address&quot; SMTP Error Msg"
permalink: /kb/317/Q317099/
---

## Q317099: PRB: &quot;550 Quoted Name Does Not Match IP Address&quot; SMTP Error Msg

{% raw %}

	Article: Q317099
	Product(s): Internet Information Server
	Version(s): 4.0,5.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server versions 4.0, 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you send e-mail messages to remote Simple Mail Transfer Protocol (SMTP)
	servers, you may receive the following error message:
	
	  550 Quoted name does not match IP Address
	
	On the local SMTP server that sent the e-mail message, a file that has the .rtr
	file name extension and that is associated with the e-mail message contains the
	following lines:
	
	  <username@domainname.com>
	  Remote connection was abruptly disconnected.
	
	In a Network Monitor trace of this scenario, after the local SMTP server
	[sourceIP:3768] sends the EHLO command to the remote SMTP server
	[destinationIP:25], as follows
	
	  EHLO <sourceFQDN>
	
	the remote SMTP server returns the following response to the local SMTP server:
	
	  550 Quoted name does not match IP Address
	
	CAUSE
	=====
	
	On public DNS servers, the A record for the source fully qualified domain name
	(FQDN) does not point to the source IP address that is owned by the source mail
	server.
	
	This kind of problem typically occurs when Network Load Balancing (NLB) or the
	Microsoft Windows NT Load Balancing Service (WLBS) is involved. With NLB or
	WLBS, the FQDN is mapped to the virtual IP address that is used to implement
	load balancing. The remote SMTP server enables a feature to perform reverse DNS
	queries, and rejects the requests from the IP address that does not match the
	FQDN name that it claims. Therefore, the source FQDN of the virtual name does
	not match the real IP address of one node in the NLB or WLBS because it points
	to the virtual IP address of the NLB or WLBS.
	
	RESOLUTION
	==========
	
	To resolve this problem, use either of the following methods:
	
	- On the source server, change the DNS records so that the source FQDN matches
	  the source IP address.
	
	- For NLB or WLBS, follow these steps to create individual DNS records in the
	  DNS server for each node, and then change the FQDN setting for each node to
	  individual the FQDN name in the SMTP service:
	
	  1. In the Microsoft Management Console (MMC), click SMTP Site Properties.
	
	  2. Click the Delivery tab.
	
	  3. Type the proper string in the Fully-qualified domain name box.
	
	  4. Click OK.
	
	STATUS
	======
	
	This behavior is by design.
	
	
	Additional query words: WLBS NLS IIS SMTP 550
	
	======================================================================
	Keywords          :  
	Technology        : kbiisSearch kbiis500 kbiis400
	Version           : :4.0,5.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
