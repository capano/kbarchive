---
layout: page
title: "Q264886: WD97: &quot;A Program Is Trying to Access...&quot; Warning in DMM"
permalink: /kb/264/Q264886/
---

## Q264886: WD97: &quot;A Program Is Trying to Access...&quot; Warning in DMM

{% raw %}

	Article: Q264886
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbdta word8 word97 kbmerge kbdmm
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	- Microsoft Direct Mail Manager for Windows 
	- Microsoft Outlook 98 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	In Direct Mail Manager, when you click Outlook Folders in the Locate List dialog
	box, you receive the following warning:
	
	  A program is trying to access e-mail addresses you have stored in Outlook. Do
	  you want to allow this?
	
	  If this is unexpected, it may be a virus and you should choose "No".
	
	When you click OK, your Outlook folders are displayed.
	
	CAUSE
	=====
	
	This behavior occurs if you have installed the Outlook E-mail Security Update.
	The Outlook E-mail Security Update provides additional levels of protection
	against malicious e-mail messages. The update changes the way that Outlook
	handles attachments and the way that Outlook can be controlled
	programmatically.
	
	For additional information about this update, please see one of the following
	articles in the Microsoft Knowledge Base, depending on which version of Outlook
	you have:
	
	  Q262631 OL2000: Information About the Outlook E-mail Security Update
	
	  Q262617 OL98: Information About the Outlook E-mail Security Update
	
	Additional query words: DMM wd97 ol98 patch virus
	
	======================================================================
	Keywords          : kbdta word8 word97 kbmerge kbdmm 
	Technology        : kbWordSearch kbOutlookSearch kbAudDeveloper kbWord97 kbWord97Search kbZNotKeyword2 kbOutlook98Search kbDMM kbZNotKeyword3
	Version           : WINDOWS:97
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
