---
layout: page
title: "Q166076: New Event IDs for SNA Server Print Service"
permalink: /kb/166/Q166076/
---

## Q166076: New Event IDs for SNA Server Print Service

{% raw %}

	Article: Q166076
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:3.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, version 3.0 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	There is no way to know if the printer is out of paper or if the printer is
	offline.
	
	RESOLUTION
	==========
	
	There are two new events logged in the Windows NT Application Event log for SNA
	Server Print Service:
	
	  Event ID 3
	  Severity=Warning
	  The NT Print Spooler has reported an error on printer %1.%n
	
	  Event ID 4
	  Severity=Warning
	  The NT Print Spooler has reported that printer %1 is out of paper.%n
	
	To resolve this problem, obtain the hotfix mentioned below.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server version 3.0. This
	problem was corrected in the latest Microsoft SNA Server 3.0 U.S. Service Pack.
	For information on obtaining the service pack, query on the following word in
	the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	Additional query words:
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300
	Version           : WINDOWS:3.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
