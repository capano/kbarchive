---
layout: page
title: "Q214791: Dr. Watson Log File May Not Contain Task List"
permalink: /kb/214/Q214791/
---

## Q214791: Dr. Watson Log File May Not Contain Task List

{% raw %}

	Article: Q214791
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 16-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The Drwtsn32.log file created by Dr. Watson may not contain a task list on
	systems that use extensible performance counter DLLs, such as Microsoft SQL
	Server's Sqlctr60.dll.
	
	CAUSE
	=====
	
	Dr. Watson uses the system performance counters to generate the task list. It is
	possible for the size of the returned performance data to change between
	successive calls to retrieve it. Dr. Watson was not sufficiently tolerant of
	such a change.
	
	RESOLUTION
	==========
	
	A supported fix that corrects this problem is now available from Microsoft, but
	it has not been fully regression tested and should be applied only to systems
	experiencing this specific problem. If you are not severely affected by this
	specific problem, Microsoft recommends that you wait for the next Windows NT 4.0
	service pack that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information on support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date      Time                 Size    File Name     Platform
	  -------------------------------------------------------------
	  01/20/99  12:43a               66,832  Drwtsn32.exe  (x86)
	  01/20/99  12:47a               90,384  Drwtsn32.exe  (Alpha)
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT version 4.0.
	
	Additional query words: 4.00
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
