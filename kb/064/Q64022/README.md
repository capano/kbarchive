---
layout: page
title: "Q64022: Watch Value Can Display Incorrect Value of Far Memory"
permalink: /kb/064/Q64022/
---

## Q64022: Watch Value Can Display Incorrect Value of Far Memory

{% raw %}

	Article: Q64022
	Product(s): See article
	Version(s): 2.50
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | s_quickasm | mspl13_c
	Last Modified: 25-JUL-1990
	
	If the sample code is compiled with debug information, a watch window
	set on the "fptr" pointer will display incorrect values.
	
	Sample Code
	-----------
	
	#include <stdio.h>
	unsigned char far * fptr;
	void main()
	{
	     int c;
	     fptr=(unsigned char far *)0xd0000600;
	     for (c=0; c < 50; c++)
	          printf("%d\n", fptr[c]);
	}
	
	When fptr[c] is displayed as a watch value entry, it will show values
	that are different than the output screen. QuickC 2.00 and CodeView
	show the same watch value as the output screen.
	
	Microsoft is researching this problem and will post new information
	here as it becomes available.

{% endraw %}
