---
layout: page
title: "Q157230: DisKeeper 1.1 Causes Errors During Windows NT 4.0 Upgrade"
permalink: /kb/157/Q157230/
---

## Q157230: DisKeeper 1.1 Causes Errors During Windows NT 4.0 Upgrade

{% raw %}

	Article: Q157230
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kb3rdparty kbsetup
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you are upgrading a computer to Windows NT 4.0, you may receive the
	following error message:
	
	  The procedure entry point NTDiskeeper could not be located in the dynamic
	  link library Ntdll.dll.
	
	This error can be generated by either the Dkfat.exe or Dkntfs.exe module, and can
	occur even if the services are stopped before you begin the upgrade process.
	
	CAUSE
	=====
	
	This behavior can occur if you are upgrading a computer on which DisKeeper 1.1
	by Executive Software is installed. DisKeeper 1.1 replaces the Windows NT kernel
	with a modified version.
	
	RESOLUTION
	==========
	
	To work around this behavior, uninstall DisKeeper 1.1 before you upgrade the
	computer to Windows NT 4.0.
	
	MORE INFORMATION
	================
	
	Executive Software has announced an updated version of DisKeeper that is
	designed for Windows NT 4.0. For additional information, please contact
	Executive Software.
	
	The third-party product discussed in this article is manufactured by a vendor
	independent of Microsoft; we make no warranty, implied or other- wise, regarding
	this product's performance or reliability.
	
	Additional query words: prodnt
	
	======================================================================
	Keywords          : kb3rdparty kbsetup 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : 4.0
	
	=============================================================================
	

{% endraw %}