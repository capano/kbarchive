---
layout: page
title: "Q76801: SideKick Versions Earlier than 2.0 Conflict with MS-DOS 5/6"
permalink: /kb/076/Q76801/
---

## Q76801: SideKick Versions Earlier than 2.0 Conflict with MS-DOS 5/6

{% raw %}

	Article: Q76801
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:5.x,6.0,6.2,6.21,6.22
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 5.0, 5.0a, 6.0, 6.2, 6.21, 6.22 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	SideKick versions earlier than 2.0 may conflict with Microsoft MS-DOS version
	5.0 or later. The machine may lock up when invoking SideKick or when running
	programs such as MS-DOS Shell, MS-DOS Editor, or QBasic. SideKick version 2.0
	may solve this problem. It is also recommended that you use the LOADFIX command
	with SideKick 2.0.
	
	MORE INFORMATION
	================
	
	Conflicts with MS-DOS 5.0 and later arise because SideKick versions earlier than
	2.0 use file control blocks (FCBs) instead of file handles, which under MS-DOS
	version 5.0 and later are handled differently. SideKick 2.0 uses file handles,
	which eliminates this problem. Other conflicts may occur because the memory
	resident portion of SideKick conflicts with programs such as Shell, Editor, and
	QBasic. Shell is most likely to experience problems with earlier versions of
	SideKick because it is also a terminate-and-stay-resident (TSR) program.
	
	For more information or to obtain an upgrade, contact Borland International
	technical support.
	
	The products included here are manufactured by vendors independent of Microsoft;
	we make no warranty, implied or otherwise, regarding these product's performance
	or reliability.
	
	
	Additional query words: 6.22 5.00 5.00a 6.00 3rdparty 6.20
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS621 kbMSDOS622 kbMSDOS620 kbMSDOS600 kbMSDOS500 kbMSDOS500a
	Version           : MS-DOS:5.x,6.0,6.2,6.21,6.22
	
	=============================================================================
	

{% endraw %}