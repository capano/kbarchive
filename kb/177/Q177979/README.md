---
layout: page
title: "Q177979: XFOR: Internet Message w/Message As Attachment Generates NDR"
permalink: /kb/177/Q177979/
---

## Q177979: XFOR: Internet Message w/Message As Attachment Generates NDR

{% raw %}

	Article: Q177979
	Product(s): Microsoft Exchange
	Version(s): winnt:5.0,5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	Messages sent from the Internet to the Microsoft Mail Connector (MSMI) that
	contain embedded messages may be rejected by the MSMI with a Non-Delivery Report
	(NDR).
	
	For example, when a message is sent from Microsoft Mail for PC Networks to an
	unknown address on the Internet via a Microsoft Exchange Server, you will
	normally receive an NDR for this message. The NDR may contain the original
	message as embedded attachment and has to pass through the Microsoft Mail
	Connector. At this point, the following Event Id is generated by the MSMI:
	
	  10000 MSExchangeMSMI
	  MDBEF parsing failed on Attachment Information.
	
	CAUSE
	=====
	
	The embedded message is not handled correctly by the Microsoft Mail Connector
	Interchange service.
	
	RESOLUTION
	==========
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server,
	Version 5.0. This problem has been corrected in the latest U.S. Service Pack for
	Microsoft Exchange Server version 5.0. For information on obtaining the Service
	Pack, query on the following word in the Microsoft Knowledge Base (without the
	spaces):
	
	  S E R V P A C K
	
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server version
	5.5. This problem has been corrected in the latest U.S. Service Pack for
	Microsoft Exchange Server version 5.5. For information on obtaining the Service
	Pack, query on the following word in the Microsoft Knowledge Base (without the
	spaces):
	
	  S E R V P A C K
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbZNotKeyword2
	Version           : winnt:5.0,5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}