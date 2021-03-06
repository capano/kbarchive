---
layout: page
title: "Q254608: Configuring Phonebook Entry for Callback Causes Extra Devices"
permalink: /kb/254/Q254608/
---

## Q254608: Configuring Phonebook Entry for Callback Causes Extra Devices

{% raw %}

	Article: Q254608
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	On a computer with Routing and Remote Access Services (RRAS) installed,
	configuring a phonebook entry or a dial-on demand (DOD) entry for callback
	causes additional devices to be created as follows:
	
	  U.S. Robotics 56K Message V.34 only (COM1)
	  U.S. Robotics 56K Message V.34 only (COM1) 12345
	  U.S. Robotics 56K Message V.34 only (COM1) 12345
	  U.S. Robotics 56K Message V.34 only (COM1) 12345
	
	This causes callback not to work because it is unable to match the originally
	selected name against a valid entry.
	
	CAUSE
	=====
	
	This problem only occurs on computers with RRAS installed.
	
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Windows NT 4.0 service pack that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date      Time      Version     Size     File name     Platform
	  ---------------------------------------------------------------
	  2/21/00   07:11 PM  4.1.1.100   396,048  Rasdlg.dll    Intel
	  2/21/00   07:11 PM  4.1.1.100   577,808  Rasdlg.dll    Alpha
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
