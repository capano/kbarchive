---
layout: page
title: "Q163301: PPT: Sample VB Code to Check for Open Presentation"
permalink: /kb/163/Q163301/
---

## Q163301: PPT: Sample VB Code to Check for Open Presentation

{% raw %}

	Article: Q163301
	Product(s): Microsoft PowerPoint for Windows
	Version(s): MACINTOSH:98; WINDOWS:97
	Operating System(s): 
	Keyword(s): kbcode kbmacro kbProgramming kbdta kbdtacode KbVBA _IK11573
	Last Modified: 13-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft PowerPoint 98 Macintosh Edition 
	- Microsoft PowerPoint 97 for Windows 
	- Microsoft Visual Basic for Applications 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains a sample Microsoft Visual Basic for Applications function
	named IsPresentationOpen that determines whether a specific presentation is
	open. A sample macro (Sub procedure) named Driver is also included to
	demonstrate how to call the IsPresentationOpen function.
	
	MORE INFORMATION
	================
	
	Microsoft provides programming examples for illustration only, without warranty
	either expressed or implied, including, but not limited to, the implied
	warranties of merchantability and/or fitness for a particular purpose. This
	article assumes that you are familiar with the programming language being
	demonstrated and the tools used to create and debug procedures. Microsoft
	support professionals can help explain the functionality of a particular
	procedure, but they will not modify these examples to provide added
	functionality or construct procedures to meet your specific needs. If you have
	limited programming experience, you may want to contact a Microsoft Certified
	Partner or the Microsoft fee-based consulting line at (800) 936-5200. For more
	information about Microsoft Certified Partners, please visit the following
	Microsoft Web site:
	
	  http://www.microsoft.com/partner/referral/
	
	For more information about the support options that are available and about how
	to contact Microsoft, visit the following Microsoft Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In the sample below, IsPresentationOpen checks to see if a presentation
	named "test.ppt" is open. In your code, replace this file name with the name of
	your presentation.
	
	Sample Visual Basic Procedures
	------------------------------
	
	     Sub Driver()
	
	        Dim IsOpen As Boolean
	
	        ' Check to see whether test.ppt is open.
	        IsOpen = IsPresentationOpen("test.ppt")
	
	        ' Process the return value from IsPresentationOpen.
	        If IsOpen = True Then
	           MsgBox "The presentation is open.", vbInformation
	        Else
	           MsgBox "The Presentation is not open.", vbInformation
	        End If
	
	     End Sub
	
	     ' Function Name: IsPresentationOpen()
	     ' Arguments:     A string that represents the name of the presentation.
	     '                The string can include the full path or just the
	     '                presentation name.
	     ' Returns:       True if the presentation is open
	     '                False if the presentation is not open
	
	     Function IsPresentationOpen(strPresName As String) As Boolean
	
	        ' An object reference to a presentation.
	        Dim oPresObject As Presentation
	
	        Dim boolIsFullPath As Boolean
	
	        ' Check to see whether the full path was passed.
	        If (InStr(1, strPresName, ":\")) = 0 Then
	           boolIsFullPath = False
	        Else
	           boolIsFullPath = True
	        End If
	
	        ' Loop through the open presentations.
	        For Each oPresObject In PowerPoint.Presentations
	
	           If boolIsFullPath = True Then
	
	              ' Check for a match.
	              If (StrComp(oPresObject.FullName, _
	                       strPresName, _
	                       vbTextCompare) = 0) Then
	
	                 IsPresentationOpen = True
	                 Exit Function
	              End If
	
	           Else
	
	              ' Check for a match.
	              If (StrComp(oPresObject.Name, _
	                       strPresName, _
	                       vbTextCompare) = 0) Then
	                 IsPresentationOpen = True
	                 Exit Function
	              End If
	
	           End If
	
	        Next oPresObject
	
	        ' No match found.
	        IsPresentationOpen = False
	
	     End Function
	
	REFERENCES
	==========
	
	For more information about creating Visual Basic for Applications macros, click
	the Office Assistant in Microsoft PowerPoint, type "how to create a macro"
	(without the quotation marks), click Search, and then click to view "Create a
	macro in Visual Basic Editor."
	
	For more information about running Visual Basic for Applications macros, click
	the Office Assistant in Microsoft PowerPoint, type "how to run a macro" (without
	the quotation marks), click Search, and then click to view "Run a macro."
	
	NOTE: If the Assistant is hidden, click the Office Assistant button on the
	Standard toolbar. If the Assistant is not able to answer your query, please see
	the following article in the Microsoft Knowledge Base:
	
	  Q176476 OFF: Office Assistant Not Answering Visual Basic Questions
	
	For more information about getting help with Visual Basic for Applications,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q163435 VBA: Programming Resources for Visual Basic for Applications
	
	Additional query words: 8.00 ppt8 vba vbe macppt mac_ppt ppt98 powerpt
	
	======================================================================
	Keywords          : kbcode kbmacro kbProgramming kbdta kbdtacode KbVBA _IK11573 
	Technology        : kbHWMAC kbOSMAC kbPowerPtSearch kbZNotKeyword6 kbPowerPt97 kbPowerPt97Search kbPowerPt98Search kbPowerPt98 kbVBASearch kbZNotKeyword3
	Version           : MACINTOSH:98; WINDOWS:97
	Hardware          : MAC x86
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}