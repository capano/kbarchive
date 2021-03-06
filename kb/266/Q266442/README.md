---
layout: page
title: "Q266442: XCLN: Mail Stops Flowing from MS Mail Connector to Exchange Ser"
permalink: /kb/266/Q266442/
---

## Q266442: XCLN: Mail Stops Flowing from MS Mail Connector to Exchange Ser

{% raw %}

	Article: Q266442
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 23-OCT-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When message flow across an MS Mail connector to Exchange Server 5.5 stops, the
	following message may appear in the application log of Event Viewer:
	
	  Error 4536-Incomplete or missing routing information at <server name>.
	  Routing could not be determined due to an external member in a group
	  definition.
	
	Event IDs 4304, 4355, and 4395 also appear in the application log.
	
	CAUSE
	=====
	
	This issue can occur when the P1 directory no longer exists.
	
	RESOLUTION
	==========
	
	To resolve this issue, add the P1 directory and then restart the Microsoft Mail
	(PC) message transfer agent (MTA).
	
	MORE INFORMATION
	================
	
	To add the P1 directory, follow these steps:
	
	1. Verify that the permissions on the Exchange servers are correct.
	
	2. Copy the Network.glb file to a local drive, and then, from the command
	  prompt, type
	  "Network.glb" (without the quotation marks)
	  Confirm that the size of the Network.glb file is a multiple of 122 bytes, and
	  that the associated .xtn files are consistent.
	
	3. At the command prompt, run the Microsoft Mail for PC Networks Mail Integrity
	  Check (Mailint.exe).
	
	4. Add the P1 directory to the Maildata directory.
	
	5. Copy Populate.msm from another postoffice subdirectory to the P1 directory.
	
	6. In Control Panel, double-click Services, and then start PC MTA.
	
	For additional information on the Mail Integrity Check and Network.glb, click the
	article numbers below to view the articles in the Microsoft Knowledge Base:
	
	  Q132744 PC Gen: Description of Mail Integrity Check MAILINT.EXE
	
	  Q87467 PC DB: What the NETWORK.GLB File Is Used For
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
