---
layout: page
title: "Q57482: Graphics Library Code Limited to One Code Segment"
permalink: /kb/057/Q57482/
---

## Q57482: Graphics Library Code Limited to One Code Segment

{% raw %}

	Article: Q57482
	Product(s): See article
	Version(s): 2.00 2.01
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | | mspl13_c
	Last Modified: 17-JAN-1990
	
	The total amount of code an application calls from the graphics
	library must not exceed 64K in length. Therefore, if many different
	graphics functions are called from GRAPHICS.LIB and/or PGCHART.LIB,
	there is a possibility that you will receive the following link error
	message:
	
	   l1070 segment size exceeds 64K
	
	This limitation is related to the fact that the graphics library was
	built to be compatible with all memory models. The graphics library
	forces the use of the segment _TEXT for its code because all memory
	models can access this segment. As a result, if too many different
	graphics library functions are called, this segment may overflow and
	the only workaround is to reduce the number of functions needed from
	the graphics libraries.

{% endraw %}
