---
layout: page
title: "Q169859: XADM: Event ID 1081 and Service Specific Error 0x00000057"
permalink: /kb/169/Q169859/
---

## Q169859: XADM: Event ID 1081 and Service Specific Error 0x00000057

{% raw %}

	Article: Q169859
	Product(s): Microsoft Exchange
	Version(s): winnt:5.0
	Operating System(s): 
	Keyword(s): kbusage exc5
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	After you restore an on-line backup, the information store produces a service
	specific error 0x00000057. The following event ID is generated in the
	application event log:
	
	  Event ID: 1081
	  Source: MSExchangeIS
	  Description: MSExchangeIS is unable to recover the database because error
	  0x00000057 occurred after a restore operation.
	
	CAUSE
	=====
	
	When the information store tries to start after an on-line restore, it attempts
	to read the RestoreInProgress key to determine how to handle the on-line
	restore. In this case, the Data parameter in the EDB_RstMap value was corrupt,
	and Microsoft Information Store service failed attempting to read this string.
	
	Hex 57 converts to Dec. 87. When using NET HELPMSG 87, this produces the error
	message:
	
	  The parameter is incorrect.
	
	The Exchange Server-aware backup software restored the RestoreInProgress key
	incorrectly. The EDB_RstMap value had invalid entries in the DATA field. It
	looked as follows:
	
	Name:  EDB_RstMap
	  Type:  Reg_Multi_SZ
	  Data:  \\Server\D$\exchsrvr\mdbdata\pub.edb
	  \\Server\D$\exchsrvr\mdbdata\priv.edb
	  q
	  \\Server\D$\exchsrvr\mdbdata\PUB.
	
	Note the line with the q.
	
	RESOLUTION
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	To correct the problem, the above string needs to be modified to reflect the
	proper database paths. Do the following:
	
	1. Start the Registry Editor (Regedt32.exe).
	
	2. Locate the EDB_RstMap registry value under the following key in the
	  registry:
	
	     HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSExchangeIS\Res
	     toreInProgress
	
	3. Click String on the Edit menu, type the appropriate paths, and then click
	  OK.
	
	  Here is an example of a correct EDB_RstMap Key:
	
	     Value 3
	        Name:  EDB_RstMap
	        Type:  Reg_Multi_SZ
	        Data:  \\<Server_Name>\D$\exchsrvr\mdbdata\priv.edb
	                 \\<Server_Name>\D$\exchsrvr\mdbdata\priv.edb
	               \\<Server_Name>\D$\exchsrvr\mdbdata\pub.edb
	                 \\<Server_Name>\D$\exchsrvr\mdbdata\pub.edb
	
	4. Quit the Registry Editor.
	
	
	Additional query words: ArcServer disaster recovery
	
	======================================================================
	Keywords          : kbusage exc5 
	Technology        : kbExchangeSearch kbExchange500 kbZNotKeyword2
	Version           : winnt:5.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
