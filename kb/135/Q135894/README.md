---
layout: page
title: "Q135894: Windows 95 CD-ROM General.txt File"
permalink: /kb/135/Q135894/
---

## Q135894: Windows 95 CD-ROM General.txt File

{% raw %}

	Article: Q135894
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 95
	Operating System(s): 
	Keyword(s): win95
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains a copy of the information in the General.txt file from the
	Windows 95 CD-ROM. Setup copies this file to the Windows folder.
	
	MORE INFORMATION
	================
	
	 -----------------------------------------------------------------
	        Microsoft Windows 95 README for General Information
	
	                          August l995
	 -----------------------------------------------------------------
	
	            (c) Copyright Microsoft Corporation, 1995
	
	This document provides complementary or late-breaking information to
	supplement the Microsoft Windows 95 documentation.
	
	------------------------
	How to Use This Document
	------------------------
	
	To view General.txt on screen in Notepad, maximize the Notepad window.
	
	To print General.txt, open it in Notepad or another word processor,
	then use the Print command on the File menu.
	
	--------
	CONTENTS
	
	STARTUP PROBLEMS
	APPLETS
	DISK TOOLS
	DISKS AND CDs
	DRIVERS
	PRINTING
	REMOVABLE MEDIA
	MICROSOFT FAX
	PEN SERVICES
	MS-DOS CODE PAGE
	---------
	
	STARTUP PROBLEMS
	================
	
	There is a compatibility issue with some PCI-based display adapters.
	If you have a PCI-based computer and your computer stops responding:
	- On the first startup after installing your PCI display adapter
	- In Safe Mode Startup
	- When your display is set to 640x480, 16 colors
	then you need to replace the Vga.drv file by copying
	\Drivers\Display\Vga\Vga.drv to your Windows\System directory.
	
	If you are running Windows 95 on a 386-based computer and Windows 95
	will not start even in Safe Mode, you need to replace Vga.vxd. If you
	purchased Windows 95 on a CD-ROM, copy \Drivers\Display\OldVga\Vga.vxd
	to your Windows\System directory. If you purchased Windows 95 on
	floppy disks, contact Microsoft Products Support Services to get this
	updated  file.
	
	Computers with Cyrix CPU
	------------------------
	If you have an Epson 866C or Microcenter Winbook computer, you may
	experience periodic general protection faults. To fix this problem:
	
	1. Copy WB16off.exe from Windows 95 Setup Disk 1 (or if your product
	  is on CD, from the \Win95 directory) to your Windows directory.
	2. Add the following line to your Autoexec.bat file:
	
	  c:\windows\wb16off.exe
	
	Micron Computers
	----------------
	Micron M5-P1 series: BEFORE INSTALLING WINDOWS 95, users of Micron
	M5-PI series (P-60, P-66) need to be sure that the BIOS read/write
	jumper (W22) is set to the read-only position. Setting up with this
	jumper in the read\write position may cause BIOS corruption during
	Windows 95 installation. For more information, in the United States
	contact Micron Technologies at (208) 465-3434. Outside the U.S.,
	contact your local hardware provider.
	
	Micron P90 and P100: BEFORE INSTALLING WINDOWS 95, users of Micron P90
	and P100 systems need to make sure their BIOS version is N15 or later.
	For more information, in the U.S. contact Micron Technologies at
	(208) 465-3434. Outside the U.S., contact your local hardware
	provider.
	
	Undefined Dynalink Error
	------------------------
	If you receive an "undefined dynalink" error, it's likely that a
	program you are running uses an earlier version of QuickTime that
	conflicts with the current version. To resolve this problem, you need
	to delete the QuickTime files from the program's directory. To do
	this, carry out the following procedure:
	
	  1. Restart your computer.
	  2. Click the Start button, click Find, and then click Files Or
	     Folders.
	  3. In the Named box, type the following:
	
	     qt*.*, *.qtc
	
	  4. Make sure the Look In box specifies your C drive, and then click
	     Find Now.
	  5. Delete all the QuickTime files in the program's directory.
	     Be sure NOT to delete any QuickTime files in the \Windows or
	     \Windows\System directories.
	  6. Restart your computer.
	
	You can also contact Apple for information about QuickTime version
	2.02, or you can download it from CompuServe.
	
	System Detection Error -- BIOS Could Lead to Data Loss
	------------------------------------------------------
	If your computer displays the following message:
	
	       System Detection
	
	       Your computer uses a BIOS that could lead to data loss if you
	       run Windows 95.
	
	       Please update the BIOS before installing Windows 95. For more
	       information, contact your computer manufacturer.
	
	you can still install Windows 95 by carrying out the following
	procedure.
	
	NOTE: Microsoft takes no responsibility for any damange that may
	result from this operation.
	
	  1. Copy the contents of the Windows 95 CD-ROM (or floppy disk 1) to
	     your hard disk.
	  2. At the MS-DOS prompt, type the following:
	
	     extract precopy2.cab msdet.inf
	
	  3. At the command prompt, type the following:
	
	     edit msdet.inf
	
	  4. On the Search menu, click Find.
	  5. In the Find What box, type the following:
	
	     [BadDSBios]
	
	  6. Click Find Now.
	  7. Insert a semicolon before each of the two lines following the
	     [BadDSBios] heading.
	  8. Save your changes, and then run Setup again.
	
	Dell Latitude XP Portable Computers with Docking Stations
	---------------------------------------------------------
	Some early Dell portable computers can experience problems if you
	start up while attached to a docking station and you have a PCMCIA
	card inserted in a PCMCIA slot. Although the PCMCIA card will be seen
	by Windows 95, the card will not function. To work around this
	problem, you should eject the PCMCIA card and reinsert it. The
	computer and PCMCIA card should recover. This problem is fixed in
	later Dell BIOS versions. For a BIOS upgrade, contact Dell Computer
	Corporation.
	
	APPLETS
	=======
	
	Backup, Known Problems
	----------------------
	- Backup does not work with all tape drives. If you install Backup
	 and get a message that your tape drive has not been detected, click
	 the Help button to see a list of supported tape drives.
	- If a backup to tape moves less than 1.5 MB per minute, you may have
	 a conflict between the tape unit and your video card. The workaround
	 is to start the backup operation and then open a full-screen MS-DOS
	 box until the operation has finished.
	- Windows 95 Help, Windows Explorer, and disk tools have links to the
	 Windows 95 Backup program. If you did not install Backup, and you
	 have the MS-DOS 5 Backup.exe file in your path, these links will
	 automatically start the MS-DOS Backup program.
	
	Briefcase, Known Problem
	------------------------
	If you have Briefcase installed and then you enable user profiles (for
	multiple users on the same computer), Briefcase does not copy to each
	profile correctly. To work around this problem, carry out the
	following procedure:
	
	  1. After you enable user profiles, delete the My Briefcase icon
	     from the desktop.
	
	  2. Use your right mouse button to click the desktop, click New, and
	     then click Briefcase.
	
	HyperTerminal, Known Problems and General Information
	-----------------------------------------------------
	- If a session is open, HyperTerminal does not recognize when a
	 PCMCIA modem is inserted.
	- When receiving a file, HyperTerminal does not know if the disk
	 is full.
	- To use the CTRL keys for Cut, Copy, and Paste in HyperTerminal, you
	 need to use Windows keys instead of Terminal keys. To change this
	 setting, in HyperTerminal, click the Settings tab.
	- In File Transfer, HyperTerminal does not send files with attributes
	 marked as System or Hidden.
	- If a Windows 3.1 TAPI service provider is already installed on your
	 system when you upgrade to Windows 95, you will experience problems
	 with HyperTerminal. To work around these problems, you can use the
	 Telephony icon in Control Panel to  remove and then reinstall the
	 TAPI service provider, or you can run the utility Tapiutil.exe. You
	 can download Tapiutil.exe from ftp.microsoft.com, or www.microsoft.com.
	
	ScanDisk, Known Problems
	------------------------
	- If you have created or named files or folders while using different
	 code pages, ScanDisk may report errors about these files or the
	 folders they reside in. If you are affected by this, open ScanDisk's
	 Advanced dialog box and make sure Check Files For Invalid File Names
	 is not checked. Note that turning off this option may inhibit
	 ScanDisk's ability to detect or repair seriously damaged folders.
	
	WordPad, Known Problem
	----------------------
	- File/Print Preview may not show the page layout accurately, but
	 the line breaks are shown accurately.
	
	DISK TOOLS
	==========
	
	- If you create a Briefcase and then compress a drive that contains
	 files to which it refers, the Briefcase's association to the files
	 will be lost. The files will still exist, but you will need to
	 reassociate them with the Briefcase.
	- If you use INTERLNK, do not use ScanDisk, DriveSpace, or the Disk
	 Defragmenter to operate on a drive on a remote computer.
	- AT&T Mail versions 2.5 and earlier will install a TSR that prevents
	 disk utilities from being able to repair disks. If you are running
	 one of these earlier versions, contact AT&T for information about
	 their latest release.
	
	DISKS AND CDs
	=============
	
	- The NEC 260GW ATAPI CD-ROM that shipped with older Gateway computers
	 is now supported through protect-mode drivers. In order for protect
	 mode support to work, the real-mode driver needs to be loaded in
	 Config.sys.
	- The NEC 3X, firmware version 2.2, can give bad data and is not
	 supported by Windows 95.
	
	DRIVERS
	=======
	
	EZ-Drive
	--------
	EZ-Drive is supported through the protected-mode IDE driver.
	
	Adaptec EZ SCSI
	---------------
	Adaptec EZ SCSI Windows version will not run. The MS-DOS version will
	work with Windows 95.
	
	Arco AcideJL
	------------
	If you are using this adapter, the driver AcideJL.386 causes a
	conflict when Windows 95 is installed from earlier versions of
	Windows. However, you can install Windows 95 from MS-DOS.
	
	Promise 2300+ Drivers
	---------------------
	MS-DOS (Eide2300.sys): Works fine; you can get extra performance by
	installing this driver.
	
	Windows 3.1 (Eide2300.386): Works fine, but does not add any value.
	Setup removes this driver.
	
	Windows 95 (Ptivgapi.mpd): This driver is still in beta and its use
	is not recommended at this time.
	
	PRINTING
	========
	
	Compaq Prolinea or DeskPro computers
	------------------------------------
	If you have one of the Compaq Prolinea or DeskPro models listed
	following this topic, and you are using a parallel attached printer
	that supports bidirectional communications (such as the HP LaserJet
	Series 4 & 5 printers, some Lexmark LaserPrinters, and possibly
	others), you may experience problems resulting in timeout errors when
	printing. To correct this problem, copy a newer LPT driver (Lpt.vxd)
	from the \Drivers\Printer\Lpt directory of the Windows 95 CD to your
	\Windows\System directory. You can also obtain this file from the
	Windows Driver Library. If the problem persists, make sure that the
	ECP port on your computer is configured for DMA channel 3. To do this,
	look up "DMA channel" in the Windows Help Index.
	
	  Compaq Prolinea 450
	  Compaq Prolinea 466
	  Compaq Prolinea 4100
	  Compaq Prolinea 5100
	  Compaq Prolinea 5120
	  Compaq Prolinea 5133
	  Compaq Prolinea 575
	  Compaq Prolinea 590
	  Compaq DeskPro 450
	  Compaq DeskPro 466
	  Compaq DeskPro 4100
	  Compaq DeskPro 5100
	  Compaq DeskPro 5120
	  Compaq DeskPro 5133
	  Compaq DeskPro 575
	  Compaq DeskPro 590
	
	REMOVABLE MEDIA
	===============
	
	Syquest Removable IDE Cartridge
	-------------------------------
	This is supported. You need to add the following line to the [386enh]
	section of your system.ini file:
	  RemovableIDE=1
	
	MICROSOFT FAX
	=============
	
	You need a Class 1 fax modem to take advantage of advanced security
	features and to exchange editable binary files using Microsoft Fax.
	You can use Class 2 fax modems to send and receive traditional Group 3
	faxes.
	
	The first time you start a portable PC with a new hardware
	configuration, Windows 95 may start with all printers off line. This
	includes the fax printer. To correct this problem, do the following:
	
	  1. Click the Start menu, and then click Settings.
	  2. Click Printers, and then double-click the icon for the Microsoft
	     Fax printer.
	  3. On the Printer menu, make sure that Work Offline is not checked.
	
	Windows for Workgroups 3.11 network fax clients cannot connect to a
	Windows 95 network fax server, and vice-versa. A patch is available
	from Microsoft Product Support that will enable a Windows for
	Workgroups 3.11 client to connect to a Windows 95 NetFax server.
	
	If you are using your computer as a Microsoft Fax NetFax server, do
	not shut down or log off of Microsoft Exchange or Windows 95 while
	faxes are being sent or are still in the fax queue.
	
	While fax is in automatic answer mode, programs that are not TAPI-
	enabled will not be able to use the modem. This includes all 16-bit
	communication programs. By default, Microsoft Fax is set up to let
	a 16-bit program use the modem and will not automatically answer
	incoming faxes. If you do not use other 16-bit communication programs
	and you want to have Microsoft Fax automatically answer all incoming
	calls as fax calls, do the following:
	
	  1. Right click the fax machine icon, located on the taskbar near
	     the clock.
	  2. Click Modem Properties.
	  3. Change the answer mode to Answer After 3 Rings.
	
	Individual phone systems and different modems may differ in the amount
	of time they need to answer incoming fax calls. Setting the answer
	mode to answer after three rings may actually result in the phone's
	being answered after two or four rings. If you experience this
	problem, you can adjust the minimum number of rings either higher or
	lower to compensate for these differences.
	
	CAS modems, such as the Intel Satisfaxion 200i, Satisfaxion 400i, and
	GammaLink CAS modems, are not supported. A firmware revision is
	available from Intel for the Satisfaxion 400i that will convert this
	modem to be Class 1 compatible. For more information, contact Intel.
	
	Do not manually change any of the printer spool settings on the
	properties sheet or the Microsoft Fax printer.
	
	Microsoft Fax is recommended only for computers with at least 8 MB of
	memory.
	
	When you send a fax by using the Microsoft Exchange New Message form,
	you cannot have the fax message on the cover page. To send a
	one-page fax with your fax message on the cover page, you must use
	the Send Fax wizard. To open the Send Fax wizard, click the Compose
	menu in Microsoft Exchange, and then click the New Fax menu. Or, click
	the Start button, point to Programs, point to Accessories, and then
	click the Fax folder. If you are faxing only a short note,
	performance is better when you put the note on the cover page.
	
	To include a message on the cover page, the cover page must contain
	the note field. If the note field is not present, the message
	appears on the second page of the fax.
	
	The network fax server component of Microsoft Fax has only been tested
	and known to work with Microsoft File and Printer Sharing for
	Microsoft Networks or Microsoft File and Printer Sharing for NetWare
	Networks.
	
	If you change a setting in Microsoft Fax while Microsoft Exchange is
	running, the change will probably not take effect until you log off
	and exit from Microsoft Exchange, and then restart it.
	
	If you send a fax to a Windows for Workgroups 3.11 At Work Fax user,
	and the message includes multiple recipients on the Cc: list, the
	only addresses that will be visible on the fax user's message are
	the fax addresses. However, all messages will be sent correctly.
	
	The File Send command in some programs may not work properly. This
	includes Microsoft Works version 3.0, Lotus 1-2-3, Aldus Pagemaker,
	and others. If you cannot reliably send a fax by using the File Send
	command, either attach the file to a fax or use the File Print
	command from within the program.
	
	When you use the fax configuration properties sheet to browse to a
	cover page, a link (.lnk) to this cover page is created in your
	Windows directory. If you already have a cover page (.cpe) in your
	Windows directory with the same name, this name will appear in the
	cover pages list twice, but you can select only one of them. It is
	recommended that you delete one of the files by using Windows
	Explorer.
	
	If you send an editable fax to a Windows for Workgroups 3.11 At Work
	Fax user, the fax recipient may not see any names on the Cc or Bcc
	line if the message was sent to duplicate or non-Fax addresses.
	However, the message will be delivered to all recipients.
	
	If you are using the Microsoft NetFax service for faxing, and you use
	the Microsoft Fax "Request a Fax" program to retrieve a fax, the
	returned information wil be sent to the NetFax server. It will then
	have to be forwarded to you manually by the system administrator.
	
	PEN SERVICES
	============
	
	Microsoft Corp. distributes Pen Services for Windows 95 through the
	Original Equipment Manufacturer (OEM) channel. As such, the Windows
	95 product does not include Pen Services for Windows 95.
	
	Contact your pen hardware OEM for your Pen Services for Windows 95
	upgrade.
	
	MS-DOS CODE PAGE
	================
	
	Depending on the country selected, Windows 95 automatically uses
	MS-DOS code page 437 or 850. If you need to use a different code
	page, such as 861 or 865, use the Changecp.exe utility program.
	This program is included in the Windows 95 Resource Kit and the
	CD-ROM version of Windows 95. It is also available from the
	Microsoft Download Service or from your local Microsoft subsidiary.
	
	Additional query words: w_works
	
	======================================================================
	Keywords          : win95 
	Technology        : kbWin95search kbZNotKeyword3
	Version           : 95
	
	=============================================================================
	

{% endraw %}
