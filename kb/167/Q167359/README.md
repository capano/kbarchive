---
layout: page
title: "Q167359: FIX: extern Declaration Generates Extra Constructor Call"
permalink: /kb/167/Q167359/
---

## Q167359: FIX: extern Declaration Generates Extra Constructor Call

{% raw %}

	Article: Q167359
	Product(s): Microsoft C Compiler
	Version(s): winnt:4.0,4.1,4.2,5.0,6.0
	Operating System(s): 
	Keyword(s): kbcode kbtool kbVC400bug kbVC410bug kbVC420bug kbVC500bug kbVC600bug kbVS600sp4fix kbVS
	Last Modified: 20-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, versions 4.0, 4.1 
	- Microsoft Visual C++, 32-bit Enterprise Edition, versions 4.2, 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Professional Edition, versions 4.2, 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	An extern declaration incorrectly causes an extra constructor call when the
	extern declaration and the global declaration appear in the same translation
	unit.
	
	NOTE: Here, translation unit means the source file and any included files
	considered as though they were all one file. Please see the example code in the
	"More Information" section.
	
	RESOLUTION
	==========
	
	There are many potential workarounds. The basic condition is that the extern
	declaration cannot appear after the global variable declaration in the same
	translation unit. One of the easiest ways to assure this condition is to place
	the offending global variable declaration(s) in a source file of their own that
	is included in the project, but not included in any other source files (please
	see the example code in the "More Information" section).
	
	A supported fix for Visual C++ 6.0 that corrects this problem is now available
	from Microsoft, but it has not been fully regression tested and should be
	applied only to systems experiencing this specific problem.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information on support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	The English version of this fix should have the following file attributes or
	later:
	
	+---------------------------------------------------------------------+
	| Name     | Size      | Date     | Time    | Version      | Platform | 
	+---------------------------------------------------------------------+
	| c1xx.dll | 1,196,083 | 2/8/2000 | 5:39 AM | 12.00.8769.0 | x86      | 
	+---------------------------------------------------------------------+
	
	
	NOTE: If this product was already installed on your computer when you purchased
	it from the Original Equipment Manufacturer (OEM) and you need this fix, please
	call the Pay Per Incident number listed on the preceding Web site. If you
	contact Microsoft to obtain this fix, a fee may be charged. This fee is
	refundable if it is determined that you only require the fix you requested.
	However, this fee is non-refundable if you request additional technical support,
	if your no-charge technical support period has expired, or if you are not
	eligible for standard no-charge technical support.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug was corrected in the latest service pack for
	Visual Studio 6.0.
	
	For additional information about Visual Studio service packs, click the article
	numbers below to view the articles in the Microsoft Knowledge Base:
	
	  Q194022 INFO: Visual Studio 6.0 Service Packs, What, Where, Why
	
	  Q194295 HOWTO: Tell That a Visual Studio Service Pack Is Installed
	
	You can download the latest Visual Studio service pack from the following
	Microsoft Web site:
	
	  Visual Studio Product Updates
	  (http://msdn.microsoft.com/vstudio/downloads/updates.asp)
	
	MORE INFORMATION
	================
	
	Sample Code
	-----------
	
	  /* Compile Options Needed: /GX */ 
	  // File MyClass.h
	
	  #include <iostream>
	
	  #pragma once
	
	  struct MyClass {
	     MyClass()
	              {std::cout << "MyClass ctor Exectuing" << std::endl;}
	  };
	
	  MyClass X;
	  // End File MyClass.h
	
	  // File main.cpp
	  #include "myclass.h"
	
	  extern MyClass X;
	
	  int main()
	  {
	     return 0;
	  }
	  // End File main.cpp
	
	When you build and run the preceding code, you will see that MyClass::MyClass()
	is called twice. One of the calls is generated by the global variable
	declaration in the file MyClass.h and the other by the extern declaration in the
	file main.cpp. One possible workaround is to remove the declaration of the
	global variable X from MyClass.h and create a third file, globals.cpp that
	contains the declaration of the global variable X. By doing this, the
	declaration of the global variable resides in a different translation unit than
	the extern declaration(s).
	
	  /* Compile Options Needed: /GX */ 
	  // File MyClass.h
	
	  #include <iostream>
	
	  #pragma once
	
	  struct MyClass {
	     MyClass()
	              {std::cout << "MyClass ctor Exectuing" << std::endl;}
	  };
	
	  // End File MyClass.h
	
	  // File Globals.cpp
	  #include "MyClass.h"
	
	  MyClass X;
	  // End File Globals.cpp
	
	  // File main.cpp
	  #include "myclass.h"
	
	  extern MyClass X;
	
	  int main()
	  {
	     return 0;
	  }
	  // End File main.cpp
	
	When you build and run the program, it now shows that MyClass::MyClass() is only
	called once.
	
	Additional query words: sp4
	
	======================================================================
	Keywords          : kbcode kbtool kbVC400bug kbVC410bug kbVC420bug kbVC500bug kbVC600bug kbVS600sp4fix kbVS600sp5fix 
	Technology        : kbVCsearch kbVC400 kbAudDeveloper kbVC410 kbVC420 kbVC500 kbVC600 kbVC32bitSearch kbVC500Search
	Version           : winnt:4.0,4.1,4.2,5.0,6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}