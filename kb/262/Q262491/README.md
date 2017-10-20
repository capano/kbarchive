---
layout: page
title: "Q262491: XADM: Information Store Crashes When Using Antivirus Application"
permalink: /kb/262/Q262491/
---

## Q262491: XADM: Information Store Crashes When Using Antivirus Application

{% raw %}

	Article: Q262491
	Product(s): Microsoft Exchange
	Version(s): 5.5 SP3
	Operating System(s): 
	Keyword(s): exc55sp3 kbExchange550preSP4fix kbExchange550sp4Fix kbgraphxlinkcritical
	Last Modified: 21-JUL-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 SP3 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you use Exchange Server with an antivirus software package that uses the
	Exchange Server antivirus application-programming interface (API), a Dr. Watson
	error message may be generated by the information store.
	
	The call stack is similar to the following:
	
	  # FramePtr RetAddr Param1 Param2 Param3 Function Name
	  00 0000000017b0ea68 00000000004a7b80 0000000000000000 0000000017b0eaa0
	  0000000000000000 STORE!EcOpenCvtatt+0xeb(0x01040610, 0x1B0C3D68, 0x00000000,
	  0x17B0EAA0, 0x00000000)
	  01 0000000017b0ea80 00000000004a7099 0000000000000000 0000000017b0eaa0
	  0000000000000000 STORE!CVTMINIMSG::HrOpenCvtatt+0x20(0x01040610, 0x00000000,
	  0x17B0EAA0, 0x00000000)
	  02 0000000017b0eaa0 00000000004a730d 000000001b0abfc8 0000000000000000
	  0000000000000000 STORE!CMDBMessage::OpenAttach+0x31(0x1B0ABFC8, 0x00000000,
	  0x00000000, 0x00000000, 0x17B0EAD4)
	  03 0000000017b0ead8 00000000004a7775 0000000000000000 0000000000000002
	  0000000000000000 STORE!CAttachTable::QueryRows+0xa0(0x00000000, 0x00000002,
	  0x00000000, 0x17B0EB08)
	  04 0000000017b0eb00 0000000000482c9e 0000000000000000 0000000017b0eb20
	  0000000000000000 STORE!RTFLIB_HrQueryAllRows+0xd5(0x00000000, 0x17B0EB20,
	  0x00000000, 0x00483260, 0x00000000, 0x1736C2D0)
	  05 0000000017b0eb64 000000006fff1965 0000000000000003 0000000000000000
	  0000000017b0fca8 STORE!MSGHOOK::ScGetAttachTableCache+0x10e(0x01040610,
	  0x00000003)
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Exchange Server 5.5.
	For additional information, click the following article number to view the
	article in the Microsoft Knowledge Base:
	
	  Q191914 XGEN: How to Obtain the Latest Exchange Server 5.5 Service Pack
	
	
	The following files are available for download from the Microsoft Download
	Center:
	
	  x86: DownloadDownload Q248838engi.exe now
	  (http://www.microsoft.com/downloads/release.asp?ReleaseID=25443)
	  Alpha: DownloadDownload Q248838enga.exe now
	  (http://www.microsoft.com/downloads/release.asp?ReleaseID=25444)
	
	For additional information about how to download Microsoft Support files, click
	the following article number to view the article in the Microsoft Knowledge
	Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft scanned this file for viruses. Microsoft used the most current
	virus-detection software that was available on the date that the file was
	posted. The file is stored on secure servers that prevent any unauthorized
	changes to the file.
	
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in Microsoft Exchange Server
	version 5.5 Service Pack 3. This problem was first corrected in Exchange Server
	5.5 Service Pack 4.
	
	MORE INFORMATION
	================
	
	This issue was first introduced in Build 5.5.2652.19 of the Store.exe file. If
	you previously installed build 5.5.2652.19 or later of the Store.exe file.
	
	Additional query words: vapi
	
	======================================================================
	Keywords          : exc55sp3 kbExchange550preSP4fix kbExchange550sp4Fix kbgraphxlinkcritical 
	Technology        : kbExchangeSearch kbZNotKeyword2 kbExchange550SP3
	Version           : :5.5 SP3
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}