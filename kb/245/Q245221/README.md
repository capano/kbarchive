---
layout: page
title: "Q245221: Setting IdleWinStationPoolCount to zero prevents client session"
permalink: /kb/245/Q245221/
---

## Q245221: Setting IdleWinStationPoolCount to zero prevents client session

{% raw %}

	Article: Q245221
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0 SP4
	Operating System(s): 
	Keyword(s): kbenv
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 SP4, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	When you configure Terminal Servers as user workstations that have the
	IdleWinStationPoolCount registry value set to 0 (zero), you may receive the
	following error message any time you attempt to connect to the Terminal Server
	using Terminal Server Client:
	
	  The Terminal Server has ended your connection.
	
	CAUSE
	=====
	
	This issue occurs in Service Pack 4.
	
	NOTE: This issue is corrected in Service Pack 5.
	
	RESOLUTION
	==========
	
	To resolve this issue use one of the following methods:
	
	Manually Reset the IdleWinStationPoolCount Value
	------------------------------------------------
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	Manually reset the IdleWinStationPoolCount value if you want client connections.
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Locate the IdleWinStationPoolCount value in the following registry key:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server
	
	3. On the Edit menu, click DWORD, type "0x1" (without the quotation marks), and
	  then click OK.
	
	4. Quit Registry Editor, and then restart the server.
	
	Install Windows NT Server, Terminal Server Edition Service Pack 5
	-----------------------------------------------------------------
	
	Microsoft has confirmed this to be a problem in Windows NT Server, Terminal
	Server Edition version 4.0. This problem has been corrected in the latest U.S.
	service pack for Windows NT Server, Terminal Server Edition version 4.0. For
	information on obtaining the service pack, query on the following word in the
	Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	MORE INFORMATION
	================
	
	Th IdleWinStationPoolCount value controls the number of idle sessions created by
	the server during startup. Each idle session loads an additional instance of
	Winlogon.exe and Csrss.exe in memory. This can consume more than 2 megabytes
	(MB) of memory per session. Some users or administrators may configure this
	registry value to 0 as a method of preserving resources. For additional
	information about using Terminal Server, click the article number below to view
	the article in the Microsoft Knowledge Base:
	
	  Q190164 Using Terminal Server as a User Workstation
	
	Additional query words: session terminalsvr
	
	======================================================================
	Keywords          : kbenv 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbNTTermServ400sp4 kbNTTermServSearch
	Version           : winnt:4.0 SP4
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
