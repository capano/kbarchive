---
layout: page
title: "Q127858: MSB Human: ErrMsg: Wave Error 10 and 7"
permalink: /kb/127/Q127858/
---

## Q127858: MSB Human: ErrMsg: Wave Error 10 and 7

{% raw %}

	Article: Q127858
	Product(s): Microsoft Home Kids Products
	Version(s): WINDOWS:1.0
	Operating System(s): 
	Keyword(s): kbenv kberrmsg kbmm kbsound kbtoolkbfaq
	Last Modified: 08-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Scholastic's Magic School Bus series: Explores the Human Body for Windows, version 1.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you start The Magic School Bus Explores The Human Body, or run Sound Test
	in the Bus Stop utility, you receive the following error message:
	
	In Windows 95/98
	----------------
	
	  Wave Error 10: MMSYSTEM263 This is not a registered MCI device.
	
	  -or-
	
	  Wave Error 7: MMSYSTEM263 This is not a registered MCI device.
	
	In Windows 3.1
	--------------
	
	  Wave Error 10: The specified device is not open or is not recognized by MCI.
	
	  -or-
	
	  Wave Error 7: The specified device is not open or is not recognized by MCI.
	
	If you choose OK, the program continues without any further problems, although
	every time you encounter a compressed wave sound, you get the same error
	message.
	
	CAUSE
	=====
	
	This error message occurs if the Windows MCI Sound driver is not installed.
	
	RESOLUTION
	==========
	
	To correct this problem, follow the steps outlined below for your version of
	Microsoft Windows.
	
	Windows 95/98
	-------------
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Click Multimedia.
	
	3. Click the Advanced (Devices in Windows 98) tab.
	
	4. Double-click Media Control Devices.
	
	5. Make sure that Wave Audio Device (Media Control) is listed on this branch. If
	  it is not, follow the instructions in the section below called Installing
	  Wave Audio Device under Windows 95/98, and then, restart with step 1, above.
	
	6. Click Wave Audio Device (Media Control), and then click Properties.
	
	7. Click the "Use This Media Control Device" check box to select it, and then
	  click OK.
	
	Installing Wave Audio Device under Windows 95/98
	------------------------------------------------
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Add New Hardware, and then click Next.
	
	3. When you are prompted "Do you want Windows to search for your new hardware?"
	  click No, and then click Next.
	
	4. In the list of Hardware types, click Sound, Video And Game Controllers, and
	  then click Next.
	
	5. In the Manufacturer section, click Microsoft MCI, then click Wave Audio
	  Device (Media Control). Click Next, and then click Finish.
	
	6. Restart Windows.
	
	Installing Wave Audio Device under Windows 3.x
	----------------------------------------------
	
	1. In the Main group in Program Manager, double-click the Control Panel icon to
	  start Control Panel.
	
	2. Double-click the Drivers icon.
	
	3. Click Add.
	
	4. In the List Of Drivers box, select [MCI] Sound and then choose the OK button.
	
	5. When you are prompted, insert the requested Microsoft Windows disk and click
	  OK.
	
	After following these steps, Human Body should run successfully.
	
	If this does not resolve the issue, there may be some other problems playing
	compressed audio. For one possible solution, please see the following articles
	in the Microsoft Knowledge Base:
	
	  Q121132 MSACM 2.0: Compressed Audio Will Not Play
	
	  Q100546 MSACM 1.0: Compressed Audio Will Not Play
	
	  Q133365 Windows 95/98: Troubleshooting Problems with Compressed Audio
	
	
	MORE INFORMATION
	================
	
	MCI Sound enables Windows to play compressed audio. Some of the sounds in Magic
	School Bus Explores the Human Body are compressed.
	
	
	Additional query words: kids mskids msb msbhb msbss frizz kbmm winmsbhuman msbhuman sound errmsg wav .wav kbimu
	
	======================================================================
	Keywords          : kbenv kberrmsg kbmm kbsound kbtool kbfaq
	Technology        : kbHomeProdSearch kbZNotKeyword kbKidsSearch kbScholasticHuman kbMSBSearch
	Version           : WINDOWS:1.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
