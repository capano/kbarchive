---
layout: page
title: "Q185910: SMS: SMS Database Schema Is Not Published"
permalink: /kb/185/Q185910/
---

## Q185910: SMS: SMS Database Schema Is Not Published

{% raw %}

	Article: Q185910
	Product(s): Microsoft Systems Management Server
	Version(s): 1.0,1.1,1.2,2.0
	Operating System(s): 
	Keyword(s): kbDatabase kbsms200 kbsms100 kbsms110 kbsms120 smsdatabase
	Last Modified: 31-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 1.0, 1.1, 1.2, 2.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	A common question for Systems Management Server support is "How do I run queries
	against the Systems Management Server database?" Another common question is
	"Where can I find the Systems Management Server database schema?"
	
	MORE INFORMATION
	================
	
	The database schema is not published. Microsoft reserves the right to alter the
	database schema to improve performance or add functionality. A published schema
	would lend itself to static assumptions for access to Systems Management Server
	data. If the schema is changed, those assumptions are no longer valid.
	
	Because the schema is not available, Microsoft strongly recommends that you not
	query directly against the Systems Management Server database. Instead, you
	should perform queries for information from the database in one of two ways. You
	can query internally through the Systems Management Server Administrator
	program, or externally by using Microsoft Excel, Microsoft Access, Microsoft SQL
	Server, Crystal Reports, or similar programs, and then only through the Systems
	Management Server Views generated by Systems Management Server SQL View
	Generator.
	
	REFERENCES
	==========
	
	For additional information, please see the following article(s) in the Microsoft
	Knowledge Base:
	
	  Q133253 Generating SQL Scripts for SMS Views
	
	  Q134717 Query Results Display Only First Data Record
	
	  Q150814 Creating Audited Software Report with Crystal Reports
	
	  Q153534 Retrieving SMSVIEW Data Using MS Access
	
	  Q181556 Cannot Query on Historical Inventory with SmsView.exe
	
	NOTE: The new SMS web reporting tool is available at Web Reporting Tool
	(http://www.microsoft.com/downloads/release.asp?ReleaseID=28039)
	http://www.microsoft.com/downloads/release.asp?ReleaseID=28039
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbDatabase kbsms200 kbsms100 kbsms110 kbsms120 smsdatabase 
	Technology        : kbSMSSearch kbSMS100 kbSMS110 kbSMS120 kbSMS200
	Version           : :1.0,1.1,1.2,2.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}