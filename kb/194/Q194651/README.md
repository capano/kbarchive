---
layout: page
title: "Q194651: XCON: Empty Subject Msg Can Cause NDR When Sent Through X.400"
permalink: /kb/194/Q194651/
---

## Q194651: XCON: Empty Subject Msg Can Cause NDR When Sent Through X.400

{% raw %}

	Article: Q194651
	Product(s): Microsoft Exchange
	Version(s): winnt:5.0,5.5
	Operating System(s): 
	Keyword(s): exc55sp2fix exc5 exc55
	Last Modified: 20-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When sending a message with an empty subject field through an X.400 connector to
	ATLAS, the French X.400 provider, ATLAS generates a non-delivery-report (NDR)
	back to the originator with the following message:
	
	  diagnostic = Syntax- error
	
	CAUSE
	=====
	
	Exchange Server is encoding the empty subject field with:
	
	- length = 1
	
	- value = 00
	
	In ITU Recommendation X.420, the subject field is defined as following:
	
	  SubjectField ::= TeletexString (SIZE (0..128))
	
	According to ITU Recommendation T0 to T63, the null character is not a valid T61
	character.
	
	RESOLUTION
	==========
	
	Exchange Server 5.0
	-------------------
	
	A supported fix that corrects this problem is now available from Microsoft, but
	has not been fully regression-tested and should be applied only to systems
	experiencing this specific problem. If you are not severely affected by this
	specific problem, Microsoft recommends that you wait for the next Microsoft
	Exchange Server version 5.0 service pack that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information on support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Component: Message Transfer Agent (MTA)
	
	  File Name      Version
	  --------------------------
	  Address.dll    5.0.1461.72
	  Dbserver.sch   5.0.1461.72
	  Dcprods.cat    5.0.1461.72
	  Ems_rid.dll    5.0.1461.72
	  Emsmta.exe     5.0.1461.72
	  Infoplog.cfg   5.0.1461.72
	  Infotlog.cfg   5.0.1461.72
	  Infoxlog.cfg   5.0.1461.72
	  Mmiext.dll     5.0.1461.72
	  Mtacheck.exe   5.0.1461.72
	  Mtamsg.dll     5.0.1461.72
	  P2.xv2         5.0.1461.72
	  P3.tpl         5.0.1461.72
	  P772.tpl       5.0.1461.72
	  X400om.dll     5.0.1461.72
	  X400omv1.dll   5.0.1461.72
	
	
	Exchange Server 5.5
	-------------------
	
	To resolve this problem, obtain the latest service pack for Exchange Server
	version 5.5. For more information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q191014 XGEN: How to Obtain the Latest Exchange Server 5.5 Service Pack
	
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Component: Message Transfer Agent (MTA)
	
	  File Name      Version
	  -------------------------
	  Dbserver.sch   5.5.2428.0
	  Dcprods.cat    5.5.2428.0
	  Ems_rid.dll    5.5.2428.0
	  Emsmta.exe     5.5.2428.0
	  Info4log.cfg   5.5.2428.0
	  Infodlog.cfg   5.5.2428.0
	  Infollog.cfg   5.5.2428.0
	  Infotlog.cfg   5.5.2428.0
	  Mtacheck.exe   5.5.2428.0
	  Mtamsg.dll     5.5.2428.0
	  P2.xv2         5.5.2428.0
	  X400om.dll     5.5.2428.0
	  X400omv1.dll   5.5.2428.0
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	versions 5.0 and 5.5.
	
	Additional query words: ndr
	
	======================================================================
	Keywords          : exc55sp2fix exc5 exc55 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbZNotKeyword2
	Version           : winnt:5.0,5.5
	Issue type        : kbprb
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}