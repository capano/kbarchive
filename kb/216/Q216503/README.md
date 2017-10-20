---
layout: page
title: "Q216503: PRB: Problems Showing an ATL Dialog as Modeless in ATL .exe"
permalink: /kb/216/Q216503/
---

## Q216503: PRB: Problems Showing an ATL Dialog as Modeless in ATL .exe

{% raw %}

	Article: Q216503
	Product(s): Microsoft C Compiler
	Version(s): 2.1,3.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbATL210 kbATLWC kbDlg kbVC500 kbVC600 kbATL300 kbGrpDSMFCATL
	Last Modified: 13-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Active Template Library (ATL), versions 2.1, 3.0, included with:
	   - Microsoft Visual C++, 32-bit Enterprise Edition, versions 5.0, 6.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, versions 5.0, 6.0 
	   - Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	   - Microsoft Visual C++.NET (2002) 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The ATL Object Wizard dialog box provides an option to create an ATL dialog box
	object. However, the following problems are found when displaying the ATL dialog
	box object as a modeless dialog box from within an ATL .exe project:
	
	- Clicking OK or Cancel causes an assertion failure.
	
	- The TAB or accelerator key doesn't work as expected.
	
	CAUSE
	=====
	
	The code generated by the ATL wizard is designed to show the dialog box as a
	modal dialog box.
	
	RESOLUTION
	==========
	
	Add/modify the code below to the ATL .exe project to show the ATL dialog box as
	modeless dialog box:
	
	1. The EndDialog() call in both the OnOK() and OnCancel() functions cause the
	  assertion failure. Call DestroyWindow() instead for modeless dialog box:
	
	  LRESULT OnOK(WORD wNotifyCode, WORD wID, HWND hWndCtl, BOOL& bHandled)
	  {
	     DestroyWindow();
	     PostQuitMessage(0); // OPTIONAL - call this to terminate the app.
	     return 0;
	  }
	
	  LRESULT OnCancel(WORD wNotifyCode, WORD wID, HWND hWndCtl, BOOL& bHandled)
	  {
	     DestroyWindow();
	     PostQuitMessage(0); // OPTIONAL - call this to terminate the app.
	     return 0;
	  }
	
	2. Modify the GetMessage() loop in the _tWinMain() function so IsDialogMessage()
	  is called for a modeless dialog box. This method takes care of both the tab
	  and accelerator keys processing problem:
	
	  MSG msg;
	  while (GetMessage(&msg, 0, 0, 0))
	  {
	     if ((gModelessDlg) && 
	        (!::IsDialogMessage(gModelessDlg->m_hWnd,&msg)))
	        DispatchMessage(&msg);
	  }
	
	  NOTE: TranslateMessage() is not required in the GetMessage() loop.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Use the ATL COM Wizard to generate an ATL .exe project.
	
	2. On the Insert menu, click New ATL Object to insert a dialog box object from
	  the Micellaneous category of the ATL Object Wizard dialog box. Name the
	  dialog box class, CMyDialog.
	
	3. Add the following code to the file that contains the _tWinMain() function to
	  show CMyDialog as a modeless dialog box:
	
	  // Include the header file for CMyDialog and declare a global variable of 
	  // CMyDialog type.
	  #include "mydialog.h" 
	  CMyDialog* gMainDialog = NULL;
	
	  extern "C" int WINAPI _tWinMain(HINSTANCE hInstance, 
	     HINSTANCE /*hPrevInstance*/, LPTSTR lpCmdLine, int /*nShowCmd*/)
	  {
	     // ... other stuff
	
	     // Show the CMyDialog as a modeless dialog box.
	     gMainDialog = new CMyDialog;
	     gMainDialog->Create(GetDesktopWindow());
	     gMainDialog->ShowWindow(SW_SHOW);
	
	     MSG msg;
	     while (GetMessage(&msg, 0, 0, 0))
	        DispatchMessage(&msg);
	
	     // ... other stuff
	
	     // Destroy the C++ object for the modeless dialog box.
	     if (gMainDialog)
	        delete gMainDialog;  
	
	     // ... other stuff
	  }
	
	REFERENCES
	==========
	
	(c) Microsoft Corporation 1999, All Rights Reserved. Contributions by Yeong-Kah
	Tam, Microsoft Corporation.
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbATL210 kbATLWC kbDlg kbVC500 kbVC600 kbATL300 kbGrpDSMFCATL 
	Technology        : kbVCsearch kbAudDeveloper kbATLsearch kbVCNET
	Version           : :2.1,3.0,5.0,6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}