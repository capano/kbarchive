---
layout: page
title: "Q124838: NICs That Work with Network Monitor"
permalink: /kb/124/Q124838/
---

## Q124838: NICs That Work with Network Monitor

{% raw %}

	Article: Q124838
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.0,1.1
	Operating System(s): 
	Keyword(s): kbhw kbnetwork smsnetmon kbHardware
	Last Modified: 31-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 1.0, 1.1 
	-------------------------------------------------------------------------------
	
	The following network interface cards (NICs), or network adapters, have
	been verified to work with Network Monitor. Microsoft has not tested every
	computer and/or device in all possible configurations.
	
	The following network adapters have been tested on the indicated platforms.
	
	X86  MIPS  ALPHA  Network Adapter
	X     X      X    3Com[R] 3C503 EtherLink II[R] (Coax & TP)
	X     X      X    3Com 3C503/16 EtherLink[R] II/16 (Coax & P)
	X     X           3Com 3C507 EtherLink 16 (Coax & TP)
	X     X      X    3Com 3C509 EtherLink III Parallel Tasking
	                    Adapter - ISA (Coax, TP and Combo)
	X                 3Com 3C523 EtherLink/MC (Coax & TP)
	X                 3Com 3C529 EtherLink III Parallel Tasking
	                    Adapter - MCA (Coax & TP)
	X     X      X    3Com 3C579 EtherLink III Parallel Tasking
	                    Adapter - EISA (Coax & TP)
	X                 3Com 3C770 FDDILink-F for Optical, UTP & STP[1, 106, 107]
	X                 COMPAQ NetFlex-2 ENET-TR Controller
	X                 COMPAQ NetFlex-2 TR Controller
	X                 COMPAQ NetFlex-2 DualPort ENET Controller
	X            X    DEC DE201 EtherWORKS Turbo/TP
	X                 Madge Smart 16/4 EISA Ringnode [1]
	     X           National Semiconductor DP83932 (Sonic) Motherboard
	                    Ethernet Controller on MIPS ARC/R4000 systems
	X     X      X    Novell/Eagle Technology NE2000
	X     X      X    Novell/Eagle Technology NE3200
	X                 Thomas-Conrad TC4046 MCA Token Ring Adapter [1]
	X                 Ungermann-Bass NIUps/EOTP
	X                 Xircom Corporate Series CreditCard Ethernet
	                    Adapter [1]
	X                 Xircom Pocket Ethernet III Adapter [1, 112, 113, 114]
	
	Technical Notes
	---------------
	
	  1   This device requires a driver from the \DRVLIB directory on
	      the Windows NT CD-ROM, or the Windows NT Driver Library.
	 106  This adapter is not supported on the Compaq ProSignia 500 and
	      DeskPro M series computers..
	 107  FDDI tested only.
	 112  Not compatible with IBM Thinkpad 700.
	 113  Non-bi-directional parallel ported machines may suffer
	      performance degradation when the driver for this adapter
	      is installed.
	 114  The Toshiba 4700CS and 4800CT are not supported in Bi-directional
	      mode with this adapter.
	
	The Windows NT Driver Library is provided on the Windows NT CD-ROM in the
	DRVLIB directory, as well as several locations for electronic transmission.
	
	
	Additional query words: sms prodsms Bloodhound Netmon
	
	======================================================================
	Keywords          : kbhw kbnetwork smsnetmon kbHardware 
	Technology        : kbSMSSearch kbSMS100 kbSMS110
	Version           : winnt:1.0,1.1
	
	=============================================================================
	

{% endraw %}
