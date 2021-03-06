---
layout: page
title: "Q156369: XCON: MTA Doesn't Accept IA5 in General Text Body Part"
permalink: /kb/156/Q156369/
---

## Q156369: XCON: MTA Doesn't Accept IA5 in General Text Body Part

{% raw %}

	Article: Q156369
	Product(s): Microsoft Exchange
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kb3rdparty kbusage
	Last Modified: 04-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	It is impossible to send a message from a remote message transfer agent (MTA) to
	Microsoft Exchange Server over a 1988 X.400 connector. The message is rejected
	with a non-delivery report (NDR). In the Microsoft Exchange Server Application
	Event log you will see the following error message:
	
	  Event ID: 210
	  Source: MSExchangeMTA
	  Type: Error
	  Description:
	  An internal MTA error occurred. Content conversion for message
	  C=FR;A=ATLAS;P=RPEXC;L=7705001613031996/A07679/LSPT failed.
	  Conversion error: 4096, Object at fault: 06000057,
	  Original content type: 56010A01,
	  New content type: 2A864886F7140501.[MTA DISP:FANOUT 26 9] (14)
	
	CAUSE
	=====
	
	This error will occur when the remote MTA is configured to send all message
	content as a General Text Body Part and sends a message containing only IA5
	characters. This configuration is possible with the DEC MRX product.
	
	General Text Body Part has a parameter for designating character set
	registrations. Currently the Microsoft Exchange Server system sends out
	{C0,G0,G1} == {1,6,100} for character set ISO8859-1.
	
	  1   == C0 control characters like LF, CR and so forth
	  6   == ISO646 basic 7 bit characters for ASCII in G0
	  100 == ISO8859-1 G1 extended Latin 1 chars
	
	Inbound, the MTA checks for the presence of 6 and 100, and if it has both, it
	then uses the ISO8859-1 tables to do the conversion, otherwise an NDR message is
	sent with invalid content type because no support for other character sets
	exists.
	
	
	RESOLUTION
	==========
	
	A possible workaround is to configure the remote MTA so that it does not send
	all messages as General Text Body Part.
	
	This fix allows Microsoft Exchange to accept General Text Body Part with the
	following registered character sets {C0,G0} == {1,6}.
	
	To resolve this problem, obtain the hotfix mentioned below.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange version 4.0.
	This problem was corrected in the latest Microsoft Exchange 4.0 U.S. Service
	Pack. For information on obtaining the service pack, query on the following word
	in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kb3rdparty kbusage 
	Technology        : kbExchangeSearch kbExchange400 kbZNotKeyword2
	Version           : winnt:4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
