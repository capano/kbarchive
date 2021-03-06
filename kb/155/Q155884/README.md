---
layout: page
title: "Q155884: SNA Server 2.x IP Communication Fails w/15 Char Domain Names"
permalink: /kb/155/Q155884/
---

## Q155884: SNA Server 2.x IP Communication Fails w/15 Char Domain Names

{% raw %}

	Article: Q155884
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.1,2.11,2.11 SP1
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.1, 2.11, 2.11 SP1, on platform(s):
	   - the operating system: Microsoft Windows NT 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	If you configured multiple SNA Servers in the same Microsoft Windows NT domain
	(in the case of version 2.11, the same SNA Server subdomain) but are separated
	by TCP/IP routers, the backup and member SNA Servers will not be able to locate
	the SNA Server primary configuration server if the Windows NT domain name is 15
	characters long.
	
	When you start SNA Server Admin on a backup SNA Server, you will get the
	following popup error message:
	
	  The Primary SNA Server for the domain is not active.
	  OK to attempt to open to a Backup SNA Server in read only mode?
	
	This problem will occur with SNA Server 2.11 or 2.11.sp1 on any version of
	Windows NT (3.5, 3.51 or 4.0).
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q148969 Troubleshooting SNA Server Communication over an IP Router
	
	
	CAUSE
	=====
	
	The SnaBase service was not properly opening the correct mailslot name if the
	Windows NT domain name is 15 characters long.
	
	
	RESOLUTION
	==========
	
	See below for availability of an SNA Server fix for this problem. There is no
	workaround for the problem, except to change the Windows NT domain name to a
	name less than 15 characters.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft SNA Server version
	2.11. This problem was corrected in the latest Microsoft SNA Server 2.11 U.S.
	Service Pack. For information on obtaining the service pack, query on the
	following word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	
	Additional query words: prodsna
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbAudDeveloper kbSNAServSearch
	Version           : WINDOWS:2.1,2.11,2.11 SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
