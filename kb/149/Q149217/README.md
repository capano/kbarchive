---
layout: page
title: "Q149217: XCLN: Microsoft Exchange Message Size Limitations"
permalink: /kb/149/Q149217/
---

## Q149217: XCLN: Microsoft Exchange Message Size Limitations

{% raw %}

	Article: Q149217
	Product(s): Microsoft Exchange
	Version(s): WINDOWS:4.0,5.0; winnt:4.0
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 24-MAR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 4.0 
	- Microsoft Exchange MS-DOS client, versions 4.0, 5.0 
	- Microsoft Exchange Windows 3.x client, versions 4.0, 5.0 
	- Microsoft Exchange Windows 95/98 client, versions 4.0, 5.0 
	- Microsoft Exchange Windows NT client, versions 4.0, 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The following is a list of 14 questions and answers dealing with Microsoft
	Exchange message and attachment size limitations and the number of messages and
	attachments that can be stored.
	
	MORE INFORMATION
	================
	
	Q. What is the limit to the number of addresses in the header fields?
	
	A. That depends on the client platform. The Win16 limit is smaller than the Win32
	limit, but we have tested with 1500+ on Win16 and 2000+ on Win32. These are
	total recipients because we count To:, Cc:, and Bcc: objects, although
	Distribution Lists count as 1. There is no hard limit, it is based on the amount
	of memory available on the client computer.
	
	Q. What is the limit to the number of distribution lists that can be included in
	the To:, Cc:, and Bcc: fields?
	
	A. It's the same as the limit on the number of addresses.
	
	Q. What is the limit to the number of attachments that can be sent with a single
	message?
	
	A. None, it's based on available disk space. There is a 16GB limit on the
	Microsoft Exchange Server store.
	
	Q. What is the limit to the total size of a message?
	
	A. The total size of the message, including attachments, is only limited by the
	16GB Microsoft Exchange Server store limit. However, the text of the message is
	limited to 1,048,756 characters.
	
	Q. What is the limit to the number of Distribution List nesting levels for
	hierarchical Distribution Lists?
	
	A. None.
	
	Q. What is the limit to the number of folder nesting levels?
	
	A. None.
	
	Q. What is the limit to the number of names that can be contained in a
	Distribution List?
	
	A. 5,000
	
	Q. What is the limit to the number of items that can be contained in a single
	folder?
	
	A. In the personal folders store (PST), it's 16,000. In the Microsoft Exchange
	Server store, there is no limit. Again, it's based on the 16GB storage limit.
	
	Q. What is the limit to the number of messages that can held in the Inbox?
	
	A. In the PST, the basic limitation is that 16,000 messages can be stored in a
	single folder. In the Microsoft Exchange Server, there is no limit. The
	administrator may set a user quota. If the quota is exceeded, the user will not
	be allowed to create or send new messages but they will still receive messages.
	The quota is based on size, not number of messages. In all of this, the only
	real limit is that the Microsoft Exchange Server store cannot be larger than
	16GB. The number of messages that will fit into the 16GB is the real limit and
	with single instance storage the actual limit is much higher.
	
	Q. What is the limit to the number of messages that can be held in the Outbox?
	
	A. All folders are the same, so it's 16,000 for a PST and no limit for the
	Microsoft Exchange Server store.
	
	Q. Is there a limit to the number of times a message can be forwarded?
	
	A. No, however, Microsoft Exchange does perform loop detection for forward rules
	and that limit is 240.
	
	Q. What is the limit to the size of messages that can be sent via gateways or the
	MTA?
	
	A. None, however the Administrator can set limits at each link point (MTA to MTA
	or out gateways). If a message exceeds that limit, the user will receive an
	Non-Delivery Report stating that they have exceeded the size limit.
	
	Q. What is the limit to the number of attachments that can be sent via gateways
	or the MTA?
	
	A. None. The administrative limits can be applied here also, so limits can be set
	for controlling the throughput of a link.
	
	Q. What is size limit for an individual's message store?
	
	A. None. The administrator can set quotas on the Microsoft Exchange Server store,
	but that is an administrative control issue.
	
	Additional query words: faq 1MB megabyte body
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbExchangeSearch kbExchange500 kbExchange400 kbExchangeClientSearch kbZNotKeyword kbZNotKeyword2 kbZNotKeyword3 kbExchange400DOS kbExchange500DOS kbExchange400NT kbExchange500NT kbExchange400Win95 kbExchange500Win95
	Version           : WINDOWS:4.0,5.0; winnt:4.0
	
	=============================================================================
	

{% endraw %}