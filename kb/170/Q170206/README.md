---
layout: page
title: "Q170206: FP97: How to Use Client Pull in FrontPage Web Documents"
permalink: /kb/170/Q170206/
---

## Q170206: FP97: How to Use Client Pull in FrontPage Web Documents

{% raw %}

	Article: Q170206
	Product(s): Word Front Page
	Version(s): 
	Operating System(s): 
	Keyword(s): kbdta
	Last Modified: 26-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FrontPage 97 for Windows 
	-------------------------------------------------------------------------------
	
	For a Microsoft FrontPage 98 version of this article, see Q194083.
	
	SUMMARY
	=======
	
	You can use client pull to set up a timed refresh period for your Web pages.
	When you use client pull, you can specify whether to automatically update the
	page or whether to proceed to another page after the specified time-out period
	has expired.
	
	MORE INFORMATION
	================
	
	To implement client pull, enter a special META element in the header of a
	Hypertext Markup Language (HTML) document. META elements are used within the
	header to embed document meta information that is not defined by other HTML
	elements. Client pull requires the use of the META element "HTTP- EQUIV" to
	implement the update. This element is then returned in the Hypertext Transfer
	Protocol (HTTP) response header.
	
	To add a META tag to the header of your HTML page, follow these steps:
	
	1. Start FrontPage Editor.
	
	2. On the File menu, click Page Properties, and then click the Custom tab.
	
	3. In the System Variables (HTTP-EQUIV) section, click Add.
	
	4. In the Name box, type "refresh" (without the quotation marks).
	
	5. In the Value box, type the value you want to use for seconds. For example,
	  type "30" (without the quotation marks).
	
	6. Click OK.
	
	7. Click OK again.
	
	  The following code is added to the header of your page:
	
	  <meta http-equiv="refresh" content="30">
	
	To create a link to another page, repeat the steps above, but in step 5, type the
	number of seconds to wait before refreshing, a semicolon and a space, followed
	by "URL=newpage.htm" (without the quotation marks). The meta value that
	refreshes the Newpage.htm document in five seconds should look like the
	following example:
	
	  5; url=newpage.htm
	
	The full line of code should read:
	
	  <meta http-equiv="refresh" content="5; url=newpage.htm">
	
	This technique is especially useful when you want to create a slide show effect
	with your Web pages.
	
	Additional query words: 97
	
	======================================================================
	Keywords          : kbdta 
	Technology        : kbFrontPageSearch kbFrontPage97 kbZNotKeyword2 kbFrontPage97Search
	Version           : :
	Hardware          : x86
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
