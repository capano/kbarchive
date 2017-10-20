---
layout: page
title: "Q202002: SMS: PC BIOS Properties Should Be Updated for New Systems"
permalink: /kb/202/Q202002/
---

## Q202002: SMS: PC BIOS Properties Should Be Updated for New Systems

{% raw %}

	Article: Q202002
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:2.0
	Operating System(s): 
	Keyword(s): kbsms200 kbsms200bug
	Last Modified: 08-MAR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 2.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	In Systems Management Server (SMS) version 2.0, some newer IBM PS/2 systems may
	not have their PCBIOS data updated in the PCBIOS\Category table of the database.
	As a result, in addition to the PCBIOS information of newer systems not be
	discovered and entered into the database, the PC systems are not identified.
	
	CAUSE
	=====
	
	IBM does use the System Descriptor Table generated by INT 0x15 to identify the
	different models. Getcomp.exe uses this same table to report the PCBIOS
	property.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbsms200 kbsms200bug 
	Technology        : kbSMSSearch kbSMS200
	Version           : winnt:2.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}