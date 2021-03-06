---
layout: page
title: "Q155303: HOWTO: Create Shortcuts (Shell Links) within Windows"
permalink: /kb/155/Q155303/
---

## Q155303: HOWTO: Create Shortcuts (Shell Links) within Windows

{% raw %}

	Article: Q155303
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 4.0,5.0
	Operating System(s): 
	Keyword(s): kbVBp kbVBp400 kbVBp500 kbVBp600 kbGrpDSVB kbOSWinME
	Last Modified: 26-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Control Creation Edition for Windows, version 5.0 
	- Microsoft Visual Basic Learning Edition for Windows, version 5.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Sometimes it is necessary to create shortcuts to your applications or documents
	somewhere on another user's system. Do this by calling the fCreateShellLink API
	function found in the Stkit432.dll file that ships with the Setup ToolKit in
	Microsoft Visual Basic version 4.0 for Windows or the Vb5stkit.dll file that
	ships with the Setup Toolkit in Visual Basic 5.0. The steps that follow show you
	how to do this.
	
	MORE INFORMATION
	================
	
	Shell links, also known as shortcuts, are a convenient way to reference objects
	within the shell name space (the hierarchical structure of objects in the
	Microsoft Windows 95, Windows 98, and Windows Me shell) without having to keep
	track of the name and location of the original object. Shell links are referred
	to as shortcuts in the Context menu (that appears when you right- click an
	object) of shell objects. They are implemented internally through the IShellLink
	interface.
	
	Steps for Creating a Shell Link (Shortcut) to the Desktop
	---------------------------------------------------------
	
	1. Start a new project in Visual Basic. Form1 is created by default.
	
	2. Add a Command button (Command1) to Form1.
	
	3. Add the following code to the General Declarations section of Form1:
	
	        Option Explicit
	
	        'NOTE: In Visual Basic 5.0, change Stkit432.dll in the following
	        'statement to Vb5stkit.dll. 
	
	        Private Declare Function fCreateShellLink Lib "STKIT432.DLL" (ByVal _
	         lpstrFolderName As String, ByVal lpstrLinkName As String, ByVal _
	         lpstrLinkPath As String, ByVal lpstrLinkArgs As String) As Long
	
	        Sub Command1_Click()
	
	          Dim lReturn As Long
	
	          'Add to Desktop
	          lReturn = fCreateShellLink("..\..\Desktop", _
	          "Shortcut to Calculator", "c:\Winnt\system32\calc.exe", "")
	
	          'Add to Program Menu Group
	          lReturn = fCreateShellLink("", "Shortcut to Calculator", _
	          "c:\Winnt\system32\calc.exe", "")
	
	          'Add to Startup Group
	
	          'Note that on Windows NT, the shortcut will not actually appear
	          'in the Startup group until your next reboot.
	          lReturn = fCreateShellLink("\Startup", "Shortcut to Calculator", _
	          "c:\Winnt\system32\calc.exe", "")
	
	        End Sub
	
	4. Press the F5 key to run the project, and then click the Command button.
	
	NOTE: If you are running Windows NT, the above example works correctly. If you
	are running Windows 95, Windows 98, or Windows Me, change the Calc.exe path to
	the following:
	
	  C:\Windows\Calc.exe
	
	This creates a shortcut to the Calc.exe file on the user's desktop, a program
	group, and a reference to it in the Startup items.
	
	REFERENCES
	==========
	
	Please refer to the sample on the Visual Basic 5.0 and later CD-ROM:
	Tools\Unsupprt\ShellLnk
	
	In the Visual Studio CD-ROM: \common\Tools\vb\Unsupprt\ShellLnk
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q140443 How To Create a Shortcut on the Desktop
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbVBp kbVBp400 kbVBp500 kbVBp600 kbGrpDSVB kbOSWinME 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVBA500Search kbVBA500 kbVB500 kbVB400Search kbVB400 kbZNotKeyword3
	Version           : :4.0,5.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
