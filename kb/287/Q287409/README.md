---
layout: page
title: "Q287409: Last Hardware Scan Date Is Incremented by One Month"
permalink: /kb/287/Q287409/
---

## Q287409: Last Hardware Scan Date Is Incremented by One Month

{% raw %}

	Article: Q287409
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0
	Operating System(s): 
	Keyword(s): kbConfig kbMMC kbServer kbsms200 kbsms200bug kbDataLoader kbInventory kbsmsAdmin kbsmsU
	Last Modified: 16-JUL-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 2.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When the site attachment process occurs between one primary site to another, the
	new child primary site forwards all of its client hardware inventory to the new
	parent primary site, along with other various configuration information about
	itself.
	
	When this process is complete, you can open the Resource Explorer in the Systems
	Management Server (SMS) administrators console at the parent primary site. When
	you view a computer that belongs to the child primary site under Workstation
	Status in Resource Explorer, you may observe that the last hardware scan date
	has been incremented by one month.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in the Microsoft products that
	are listed at the beginning of this article. This problem was first corrected in
	the Systems Management Server 2.0 Service Pack 4 Hotfix Rollup Package (HRP).
	
	For additional information about the SMS 2.0 SP4 HRP, click the article number
	below to view the article in the Microsoft Knowledge Base:
	
	  Q323206 SMS: List of Bugs Fixed in the Systems Management Server 2.0 SP4 HRP
	
	MORE INFORMATION
	================
	
	This problem does not affect the clients. As the clients report their next
	regularly scheduled inventory, the new and accurate hardware scan time is
	propagated to the clients' assigned sites and to all of the sites above it in
	the SMS hierarchy.
	
	The SMS command-line utility (Preinst.exe) with the /syncparent switch can also
	demonstrate the same problem.
	
	
	Additional query words: preinst.exe
	
	======================================================================
	Keywords          : kbConfig kbMMC kbServer kbsms200 kbsms200bug kbDataLoader kbInventory kbsmsAdmin kbsmsUtil 
	Technology        : kbSMSSearch kbSMS200
	Version           : :2.0
	Issue type        : kbbug
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
