---
layout: page
title: "Q130466: PRB: Double-click in File Manager Starts Wrong FoxPro Version"
permalink: /kb/130/Q130466/
---

## Q130466: PRB: Double-click in File Manager Starts Wrong FoxPro Version

{% raw %}

	Article: Q130466
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:3.0
	Operating System(s): 
	Keyword(s): kbenv
	Last Modified: 11-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When an .APP file is started from a program icon or by double-clicking in File
	Manager, Visual FoxPro is invoked instead of FoxPro for Windows and Visual
	FoxPro fails.
	
	When a FoxPro version 2.x .APP file is invoked from Visual FoxPro, Visual FoxPro
	fails and displays this error message:
	
	  Object file "<Drive:\Pathname\file.app" was compiled in a previous version
	  of FoxPro.
	
	When you click OK, you remain in the Visual FoxPro interactive development
	environment.
	
	CAUSE
	=====
	
	When Visual FoxPro is installed, the .APP file extension is automatically
	associated with Visual FoxPro, not FoxPro for Windows.
	
	WORKAROUND
	==========
	
	Use any one of the following three possible solutions. The first applies to
	Windows NT, and the second and third apply to any Windows platform.
	
	- Using REGEDT32 in Windows NT, revise the software hive entry of
	  HKEY_Local_Machine under Software, Classes, APP from the value of
	  Visual.FoxPro.Application.3 to MSFoxPro. Be careful when using the Registry
	  Editor.
	
	-or-
	
	- In the File Manager, select any FoxPro version 2.x .APP file. Then choose
	  Associate from the File menu. In the Associate dialog box, associate the
	  files with the .APP extension to Microsoft FoxPro for Windows. Click the OK
	  button, and the registry will be automatically updated. Attempting to change
	  the association in any other fashion causes a general protection (GP) fault
	  in the File Manager.
	
	-or-
	
	- Revise your application icons to have a fully-qualified path that invokes
	  your application. A sample command line for an application might be something
	  like this:
	
	  C:\FPW26\FOXPROW.EXE INVOICES.APP
	
	STATUS
	======
	
	This behavior is by design.
	
	Additional query words: kbfest VFoxWin
	
	======================================================================
	Keywords          : kbenv 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300
	Version           : WINDOWS:3.0
	
	=============================================================================
	

{% endraw %}
