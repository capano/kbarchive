---
layout: page
title: "Q115109: INFO: @ Cannot Be Used As a Delimiter with the APPEND Command"
permalink: /kb/115/Q115109/
---

## Q115109: INFO: @ Cannot Be Used As a Delimiter with the APPEND Command

{% raw %}

	Article: Q115109
	Product(s): Microsoft FoxPro
	Version(s): MACINTOSH:2.5b,2.5c; MS-DOS:2.5,2.5a,2.5b,2.6; WINDOWS:2.5,2.5a,2.5b,2.6,3.0,5.0,6.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 29-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FoxPro for Windows, versions 2.5, 2.5a, 2.5b, 2.6 
	- Microsoft FoxPro for MS-DOS, versions 2.5, 2.5a, 2.5b, 2.6 
	- Microsoft FoxPro for Macintosh, versions 2.5b, 2.5c 
	- Microsoft Visual FoxPro for Windows, versions 3.0, 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The at sign ("@") cannot be used as a delimiter in FoxPro versions 2.5 and 2.6
	for MS-DOS and Windows when you are using the APPEND command to append
	information from an ASCII text file.
	
	MORE INFORMATION
	================
	
	A number of UNIX-based products such as EMPRESS generate ASCII files using @
	signs as delimiters. The following is an example of an ASCII file generated by
	EMPRESS version 6.0 running on a Sun Microsystems SPARC workstation:
	
	  704@575@1111@JOHN B SMITH
	  704@575@1122@FRANKLIN T WOND
	  704@575@1133@ALICIA J ZELAYA
	
	However, when you use @ as a delimiter with the APPEND command, as in the
	following example
	
	  APPEND FROM <Text_Filename> DELIMITED WITH @
	
	(where the <Text_Filename> is the name of the ASCII file), FoxPro will not
	recognize the @ sign as a delimiter and will try to include each record from the
	ASCII file in the first field of the FoxPro .DBF file.
	
	To correct this problem:
	
	1. In the Command window, type the following to open the text file: MODIFY FILE
	  <Text_Filename>
	
	2. From the Edit menu, choose Find.
	
	3. Type "@" (without the quotation marks) in the Look For text box, and type ","
	  (without the quotation marks) in the Replace With text box. Then choose
	  Replace All.
	
	4. Save the file, and then use the following APPEND statement: APPEND FROM
	  <Text_Filename> DELIMITED WITH ,
	
	Additional query words: FoxMac FoxDos FoxWin
	
	======================================================================
	Keywords          :  
	Technology        : kbHWMAC kbOSMAC kbVFPsearch kbAudDeveloper kbFoxproSearch kbZNotKeyword3 kbFoxPro250bMac kbFoxPro250cMac kbFoxPro250DOS kbFoxPro250aDOS kbFoxPro250bDOS kbFoxPro260DOS kbFoxPro260 kbFoxPro250 kbFoxPro250a kbFoxPro250b kbVFP300 kbVFP500 kbVFP600
	Version           : MACINTOSH:2.5b,2.5c; MS-DOS:2.5,2.5a,2.5b,2.6; WINDOWS:2.5,2.5a,2.5b,2.6,3.0,5.0,6.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}