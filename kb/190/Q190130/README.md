---
layout: page
title: "Q190130: INFO: Description of VB 6.0 Run Time and OLE Automation Files"
permalink: /kb/190/Q190130/
---

## Q190130: INFO: Description of VB 6.0 Run Time and OLE Automation Files

{% raw %}

	Article: Q190130
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 6.0
	Operating System(s): 
	Keyword(s): kbwizard kbtophit kbAppSetup kbVBp kbVBp600 kbGrpDSVB kbDSupport
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When using the Visual Basic 6.0 Package and Deployment Wizard (PDW) to create an
	application distribution set, the PDW includes the file "VB6 Runtime and OLE
	Automation" with other files necessary to distribute the application. This
	article describes these necessary run time and core OLE files.
	
	MORE INFORMATION
	================
	
	The following files are the necessary run time and core OLE Automation files:
	
	Msvbvm60.dll - (Microsoft Visual Basic Virtual Machine) This file contains all
	intrinsic controls and functions necessary for any Visual Basic application to
	run. This file must be distributed with the application.
	
	Oleaut32.dll - Core OLE Automation file.
	
	Olepro32.dll - Placeholder file for old DLL (still must be used).
	
	Stdole2.tlb - Contains Standard OLE Type Library information.
	
	ASYCFILT.DLL - Filters for graphics images, such as .gif and JPEG's.
	
	NOTE: These files comprise the set of core OLE Automation files and Visual Basic
	6.0 run-time files, and must be used in conjunction with each other. Omission of
	one of these files may cause the system to become unstable.
	
	These files must be present on a target machine in order to run a Visual Basic
	6.0 application. When using the setup program generated by the PDW to install an
	application, these files are checked to ensure they exist and are the correct
	version before the second part of the installation program, Setup1.exe, runs.
	
	What following table lists the size, date, and version of the run time and OLE
	Automation files that shipped with Microsoft Visual Basic 6.0:
	
	  File           Version           Size           Date
	  ----           -------           ----           ----
	  Oleaut32.dll   2.30.4261         585KB          6/18/98
	  Olepro32.dll   5.0.4261          161KB          6/18/98
	  Stdole2.tlb    2.30.4261         18KB           6/17/98
	  ASYCFILT.DLL    2.30.4261        145KB          6/18/98
	  Msvbvm60.dll   6.00.8176         1,376KB        6/18/98
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q187282 : INFO: List of Visual Basic Run-Time Files Installed by Product
	
	Additional query words:
	
	======================================================================
	Keywords          : kbwizard kbtophit kbAppSetup kbVBp kbVBp600 kbGrpDSVB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVBA600 kbVB600
	Version           : :6.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}