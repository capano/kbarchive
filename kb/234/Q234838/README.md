---
layout: page
title: "Q234838: MOD2000: Deleted Modules Not Are Removed from VSS Control"
permalink: /kb/234/Q234838/
---

## Q234838: MOD2000: Deleted Modules Not Are Removed from VSS Control

{% raw %}

	Article: Q234838
	Product(s): Microsoft SourceSafe
	Version(s): ; WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbdta modSSafe
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Office 2000 Developer 
	- Microsoft Visual SourceSafe for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you remove a module that is under source code control from a VBA project,
	you are not prompted to remove it from the Visual SourceSafe project. If you
	later create a new module with the same name as the module that you removed, you
	will not be able to add it to source code control. The VBA Source Code Control
	add-in will return the following error message:
	
	  No files are available to be added to source code control.
	
	CAUSE
	=====
	
	When you try to add an object to source code control that has the same name as
	an existing object in the Visual SourceSafe project, the VBA Source Code Control
	Add-in assumes that the object that you are trying to add is the same one that
	you previously removed from the VBA project. This happens even though the file
	name does not appear in the SCC Status window.
	
	RESOLUTION
	==========
	
	After you remove a module from a VBA project, remove it from source code control
	by deleting the corresponding item in the Visual SourceSafe Explorer.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in the Microsoft products that
	are listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create and save a new workbook in Microsoft Excel 2000.
	
	2. Press ALT+F11 to open the Visual Basic Editor.
	
	3. Insert two new modules into the VBA project. Accept the default names Module1
	  and Module2.
	
	4. On the File menu, click Save <project name>.
	
	5. Use the Add-in Manager to load the VBA Source Code Control add-in if it is
	  not already loaded.
	
	6. On the Add-ins menu, point to VBA Source Code Control, and then click Add
	  Project to SourceSafe. Make sure both modules are added to the source code
	  control project.
	
	7. Delete Module2 from the VBA project, and then close Excel. Note that you are
	  prompted to save the workbook, but you are not prompted to remove the file
	  from source code control.
	
	8. Reopen the workbook that you created in step 1, open the Visual Basic Editor,
	  and then insert a new module. Accept Module2 as the default name.
	
	9. On the File menu, click Save <project name>.
	
	10. On the Add-ins menu, point to VBA Source Code Control, and then click "Add
	  Files to SourceSafe". Note that you receive the error message mentioned in
	  the "Symptoms" section.
	
	Additional query words: pra
	
	======================================================================
	Keywords          : kbdta modSSafe 
	Technology        : kbSSafeSearch kbOfficeSearch kbAudDeveloper kbOffice2000Search kbOffice2000 kbSSafe600 kbOffice2000DevSearch
	Version           : :; WINDOWS:6.0
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
