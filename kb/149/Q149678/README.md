---
layout: page
title: "Q149678: BUG: File Dates Do Not Change After a Rollback"
permalink: /kb/149/Q149678/
---

## Q149678: BUG: File Dates Do Not Change After a Rollback

{% raw %}

	Article: Q149678
	Product(s): Microsoft SourceSafe
	Version(s): 
	Operating System(s): 
	Keyword(s): kbSSafe400bug kbSSafe500bug kbSSafe600bug
	Last Modified: 08-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual SourceSafe, 16-bit, for Windows, versions 4.0, 5.0, 6.0 
	- Microsoft Visual SourceSafe, 32-bit, for Windows 4.0 
	- Microsoft Visual SourceSafe for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The date and time display in the right pane of the SourceSafe Explorer does not
	update after you roll back the file. You must check the file out and then check
	it back in or undo checkout to synchronize the file date and time in the right
	pane of the SourceSafe Explorer.
	
	RESOLUTION
	==========
	
	Check the file out, and then undo the checkout to restore the file's original
	date and time in the SourceSafe Explorer Display.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Problem
	--------------------------
	
	1. Find or create a file with some history that you can use to observe an time
	  change between versions.
	
	2. Click this file in the right pane of the SourceSafe Explorer, and then look
	  at its history.
	
	3. Pick an item in the history where there is a noticeable difference in the
	  date or time.
	
	4. Click Rollback, and then click OK. Notice that the date and time of the file
	  are the same in the file pane of the SourceSafe Explorer. To synchronize the
	  date and time, check out the file, and then check it in or undo the checkout.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbSSafe400bug kbSSafe500bug kbSSafe600bug 
	Technology        : kbSSafeSearch kbAudDeveloper kbSSafe600 kbSSafe400 kbSSafe500 kbSSafe16bitSearch kbSSafe32bitSearch
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
