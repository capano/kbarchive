---
layout: page
title: "Q78853: PRB: Conditional Breakpoints Cannot Always Be Set"
permalink: /kb/078/Q78853/
---

## Q78853: PRB: Conditional Breakpoints Cannot Always Be Set

{% raw %}

	Article: Q78853
	Product(s): Microsoft C Compiler
	Version(s): 1.0 1.5 1.51 1.52 2.0 2.1 4.0 5.0
	Operating System(s): 
	Keyword(s): kbDebug kbide
	Last Modified: 27-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Integrated Debugger, included with:
	   - Microsoft Visual C++ for Windows, 16-bit edition, versions 1.0, 1.5, 1.51, 1.52 
	   - Microsoft Visual C++, 32-bit Editions, versions 1.0, 2.0, 2.1, 4.0, 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	In the Visual Workbench debugger, an attempt to set conditional breakpoints may
	fail. A message box may appear containing a message such as
	
	  The breakpoint <breakpoint_name> cannot be set.
	
	Or, as with the Developer Studio debugger included with Visual C++ 4.0 and later,
	the conditional breakpoint may appear to be set, but when the debug session is
	initiated, a message box may appear containing the following text:
	
	  One or more of the breakpoints cannot be set and have been
	  disabled. Execution will stop at the beginning of the program.
	
	CAUSE
	=====
	
	This problem occurs only when you attempt to set the breakpoint while the
	specified variable is out of scope.
	
	RESOLUTION
	==========
	
	There are two methods to address this situation:
	
	- Trace into the program until the variable is in scope, then set the
	  breakpoint.
	
	- Specify the context of the variable when you set the breakpoint. For example,
	  specify a breakpoint on ""{main}a"" (without the quotation marks) instead of
	  on "a" (in both cases without quotation marks).
	
	MORE INFORMATION
	================
	
	Perform the following six steps to demonstrate this error with Visual C++
	versions 2.x and earlier:
	
	1. Create a new application to contain the code example below.
	
	2. From the Project menu, choose Options. In the Program Type list box, choose
	  QuickWin EXE and choose OK.
	
	3. Choose Build from the Project menu to build the sample program.
	
	4. Choose Breakpoints from the Debug menu; a dialog box appears.
	
	5. Set the Break field to "If Expr is True" and type "a" (without the quotation
	  marks) in the Expression edit control. Because the default length is 1 as is
	  the size of "a," choose the Add button, then choose OK.
	
	6. Press F5 to run the program.
	
	Perform the following six steps to demonstrate this error with the Developer
	Studio:
	
	1. Create a new console application project.
	
	2. Save the code example below as t.c and add it to the project.
	
	3. Choose Build t.exe from the Build menu.
	
	4. Choose Breakpoints... from the Edit menu. The Breakpoints dialog box appears.
	
	5. In the Location Tab, type "main" (without the quotation marks) in the Break
	  at field. Press the Condition button to display the Breakpoint Condition
	  dialog box. Type "a" (without the quotation marks) in the Break when
	  expression changes field. Press OK to close the Breakpoint Condition dialog
	  box. Press OK to close the Breakpoints dialog box.
	
	6. Press F5 to run the program.
	
	At this point, a message box appears with the error message listed in the
	SYMPTOMS section above and the breakpoint is not set. When you choose OK in the
	error message box, programs debugged with Visual C++ versions 2.x and earlier
	run to completion because no breakpoints are set; programs debugged with
	Developer Studio halt at the beginning of the program (as if a breakpoint were
	set) and may be stepped through if desired.
	
	If you are setting a breakpoint from within a C++ member function, you need to
	specify '{ClassName::Member}' in order to set the breakpoint properly.
	
	Sample Code
	-----------
	
	     /*
	      * Compile options needed: none
	      */ 
	
	     void main(void)
	     {
	        char a;
	
	        a = 'a';
	     }
	
	NOTE: The breakpoint evaluator doesn't take into account the preprocessor's
	#define statements.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbDebug kbide 
	Technology        : kbVCsearch kbAudDeveloper kbIntegratedDebugger
	Version           : 1.0 1.5 1.51 1.52 2.0 2.1 4.0 5.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
