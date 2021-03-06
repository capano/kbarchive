---
layout: page
title: "Q242308: HOWTO: Find a Window Handle from an Instance Handle"
permalink: /kb/242/Q242308/
---

## Q242308: HOWTO: Find a Window Handle from an Instance Handle

{% raw %}

	Article: Q242308
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbAPI kbSDKWin32 kbVBp kbVBp400 kbVBp500 kbVBp600 kbGrpDSVB kbDSupport
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Shell function in Microsoft Visual Basic is used to execute an application.
	Often, it is useful to get a Window handle (hWnd) to the application so you can
	manipulate it using the Windows APIs. However, the Shell function returns an
	Instance handle (hInstance), which is different from a Window handle. This
	article shows how to create and use a GetWinHandle() function to return a Window
	handle based on an Instance handle.
	
	MORE INFORMATION
	================
	
	By using the FindWindow() and GetWindow() APIs (or using EnumWindows in Visual
	Basic 5.0 or later), you can loop through the Window handle list. For each
	window handle, you can check to see if it has a parent window with GetParent().
	If the Window handle does not have a parent handle, you have reached the main
	window for an application. You can call GetWindowThreadProcessID(), which yields
	the instance handle of the process for the given window handle, to check the
	instance handle of the application against the instance handle received from the
	Shell() function.
	
	Step-by-Step Example
	--------------------
	
	1. Start a new Standard EXE project in Visual Basic. Form1 is created by
	  default.
	
	2. Add a CommandButton (Command1) to the form.
	
	3. From the Project menu, add a new module to the project, and enter the
	  following declarations and functions:
	
	  Public Const GW_HWNDNEXT = 2
	
	  Public Declare Function GetParent Lib "user32" (ByVal hwnd As Long) As Long
	  Public Declare Function GetWindow Lib "user32" (ByVal hwnd As Long, _
	    ByVal wCmd As Long) As Long
	  Public Declare Function FindWindow Lib "user32" Alias "FindWindowA" _
	    (ByVal lpClassName As String, ByVal lpWindowName As String) As Long
	  Public Declare Function GetWindowText Lib "user32" Alias "GetWindowTextA" _
	    (ByVal hwnd As Long, ByVal lpString As String, ByVal cch As Long) As Long
	  Public Declare Function GetWindowThreadProcessId Lib "user32" _
	    (ByVal hwnd As Long, lpdwprocessid As Long) As Long
	
	  Function ProcIDFromWnd(ByVal hwnd As Long) As Long
	     Dim idProc As Long
	     
	     ' Get PID for this HWnd
	     GetWindowThreadProcessId hwnd, idProc
	     
	     ' Return PID
	     ProcIDFromWnd = idProc
	  End Function
	        
	  Function GetWinHandle(hInstance As Long) As Long
	     Dim tempHwnd As Long
	     
	     ' Grab the first window handle that Windows finds:
	     tempHwnd = FindWindow(vbNullString, vbNullString)
	     
	     ' Loop until you find a match or there are no more window handles:
	     Do Until tempHwnd = 0
	        ' Check if no parent for this window
	        If GetParent(tempHwnd) = 0 Then
	           ' Check for PID match
	           If hInstance = ProcIDFromWnd(tempHwnd) Then
	              ' Return found handle
	              GetWinHandle = tempHwnd
	              ' Exit search loop
	              Exit Do
	           End If
	        End If
	     
	        ' Get the next window handle
	        tempHwnd = GetWindow(tempHwnd, GW_HWNDNEXT)
	     Loop
	  End Function
	
	4. Add the following code to the form:
	
	  Sub Command1_Click()
	     Dim hInst As Long             ' Instance handle from Shell function.
	     Dim hWndApp As Long           ' Window handle from GetWinHandle.
	     Dim buffer As String          ' Holds caption of Window.
	     Dim numChars As Integer       ' Count of bytes returned.
	     
	     ' Shell to an application
	     hInst = Shell("calc.exe")
	     
	     ' Begin search for handle
	     hWndApp = GetWinHandle(hInst)
	     
	     If hWndApp <> 0 Then
	        ' Init buffer
	        buffer = Space$(128)
	        
	        ' Get caption of window
	        numChars = GetWindowText(hWndApp, buffer, Len(buffer))
	     
	        ' Display window's caption
	        MsgBox "You shelled to the Application: " & Left$(buffer, numChars)
	     End If
	  End Sub
	
	5. Press the F5 key to run the application. Click Command1 to see that the
	  Calculator has been shelled and to see a message box displaying "You shelled
	  to the Application: Calculator."
	
	REFERENCES
	==========
	
	Topic in MSDN : "More about handles and process IDs"
	
	For additional information on using the EnumWindows functions to find a specified
	window, click the article number below to view the article in the Microsoft
	Knowledge Base:
	
	  Q183009 HOWTO: Enumerate Windows Using the WIN32 API
	
	For additional information on performing this task in 16-bit versions of VB,
	click the article number below to view the article in the Microsoft Knowledge
	Base:
	
	  Q127030 How to Find a Window Handle Based on an Instance Handle
	
	Additional query words:
	
	======================================================================
	Keywords          : kbAPI kbSDKWin32 kbVBp kbVBp400 kbVBp500 kbVBp600 kbGrpDSVB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600 kbVB400Search kbVB400
	Version           : WINDOWS:4.0,5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
