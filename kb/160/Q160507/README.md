---
layout: page
title: "Q160507: Windows 95 OEM Service Release 2 CD-ROM Network.txt File"
permalink: /kb/160/Q160507/
---

## Q160507: Windows 95 OEM Service Release 2 CD-ROM Network.txt File

{% raw %}

	Article: Q160507
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:95
	Operating System(s): 
	Keyword(s): osr2 win95
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 OEM Service Release, version 2.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, you should first make a backup copy of the
	registry files (System.dat and User.dat). Both are hidden files in the
	Windows folder.
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that
	may require you to reinstall Windows 95. Microsoft cannot guarantee that
	problems resulting from the incorrect use of Registry Editor can be solved.
	Use Registry Editor at your own risk.
	
	NOTE: For information about how to edit the registry, view the Changing
	Keys And Values online Help topic in Registry Editor (Regedit.exe). Note
	that you should make a backup copy of the registry files (System.dat and
	User.dat) before you edit the registry.
	
	SUMMARY
	=======
	
	This article contains a copy of the information in the Network.txt file from the
	Windows 95 OEM Service Release 2 (OSR2) CD-ROM. Setup copies this file to the
	Windows folder.
	
	MORE INFORMATION
	================
	
	      -----------------------------------------------------------
	                   Microsoft Windows 95 README for Networks
	                                  August 1996
	      -----------------------------------------------------------
	
	                   (c) Copyright Microsoft Corporation, 1996
	
	This document provides complementary or late-breaking information
	to supplement the Microsoft Windows 95 documentation.
	
	HOW TO USE THIS DOCUMENT
	========================
	
	To view Networks.txt on screen in Notepad, maximize the Notepad window.
	
	To print Networks.txt, open it in Notepad or another word processor,
	and then use the Print command on the File menu.
	
	CONTENTS
	========
	
	CLIENT FOR NETWARE
	 Windows 95 and NetWare 3.12 and 4.01 Servers
	 Opening Files on NetWare 3.11 Servers
	 Lowercase Extended-Character Passwords on NetWare 4.1 Servers
	 Client for NetWare and Programs That Use External Files
	 Novell NetWare Login Scripts
	 Installing Novell Client32 Overwrites
	   NetWare Directory Services Files
	 Upgrading Over an Earlier Beta Version of Windows
	 Printing to NetWare Directory Services Printers
	PLUG AND PLAY NETWORK CARDS AND 16-BIT REAL-MODE DRIVERS
	INTEL ETHEREXPRESS 16 NICs AND PCI COMPUTERS
	WINDOWS FOR WORKGROUP SHARES
	RUNNING WINDOWS 95 FROM A SERVER
	 To Install Windows 95 over Previous Builds
	SUPPORT FOR THIRD-PARTY NETWORKS
	 LANDESK 2.0
	 SunSelect PC-NFS
	 Banyan VINES
	 DEC Pathworks
	 Artisoft LANtastic
	PRINTING TO A NETWORK PRINTER
	PROBLEMS PRINTING TO POSTSCRIPT PRINTERS OVER A NETWARE NETWORK
	ISSUES AND INSTALLATION OF MS-DLC WITH WINDOWS 95
	MICROSOFT TCP/IP PROTOCOL
	USER PROFILES OVER THE NETWORK
	NETWORK BACKUP AGENTS
	 Arcada Backup Exec Network Backup Agent
	 Cheyenne ARCserve Network Backup Agent
	REAL-MODE PROTOCOLS: WARNING ICONS ON YOUR NETWORK ADAPTER
	USING AN IBM THINKPAD WITH A DOCK II
	INTEL ETHEREXPRESS PRO /100B CARD NOT CORRECTLY DETECTED
	SETTING UP A WINS SERVER
	INTERLNK
	USING COMSPEC VARIABLES POINTING TO NETWORK COMMAND.COM FILES
	
	CLIENT FOR NETWARE
	==================
	
	Windows 95 and NetWare 3.12 and 4.01 Servers
	--------------------------------------------
	Windows 95 with Microsoft Client for NetWare can experience
	problems with NetWare 3.12 and 4.01 servers if packet burst is
	turned on. This is a known problem with these servers that Novell
	has fixed and posted on their forums. Download the file Pburst.exe
	from the Novell NetWare Forum on Compuserve or the Novell Web site
	(Ftp.Novell.com).
	
	Pburst.exe contains the patch for the affected servers.
	
	Opening Files on NetWare 3.11 Servers
	-------------------------------------
	Programs that open a large number of files consecutively in rapid
	succession might have occasional problems opening files on NetWare 3.11
	servers. This can also happen when opening a file in a folder for which
	you do not have file scan rights, such as an MS Mail shared post office.
	
	Possible error messages:
	
	- "File not found" error on a file you know exists
	- "Sharing violation" or "Lock violation" error
	- "Unable to open file" error
	- "File in use" error
	
	There are two solutions to these problems:
	
	- Obtain a patch file from Novell for the NetWare 3.11 server. Using
	 FTP, connect to ftp.novell.com. Go to /pub/netware/nwos/nw311/osnlm
	 and run 311ptd.exe. This program will extract the file os2opnfx.nlm.
	 Then, load the .nlm file onto the NetWare 3.11 server.
	 ("load os2opnfx.nlm")
	
	- Disable long filename support in Client for NetWare. This means that
	 you will not be able to use long filenames on any NetWare servers
	 from Windows 95. To disable long-filename support, carry out the
	 following steps:
	
	 1. Click the Start menu, click Run, and then type Regedit.
	 2. Go to
	    HKEY_Local_Machine\System\CurrentControlSet\Services\VxD\NWRedir
	 3. Create a new binary value named supportLFN with a value of 0.
	
	Lowercase Extended-Character Passwords on NetWare 4.1 Servers
	-------------------------------------------------------------
	In a NetWare 4.1 environment, Client for NetWare does not support
	passwords that use certain lowercase extended characters. Users
	need to change their password to all uppercase characters.
	
	Client for NetWare and Programs That Use External Files
	-------------------------------------------------------
	If you are using Microsoft Client for NetWare, and you run a program
	that needs to access an auxiliary file, your program will have problems
	if the auxiliary file is on a drive other than the one the program is
	on. This is because only the current drive is searched for auxiliary
	files; the search path is not searched. If you experience this problem,
	make sure the program and any auxiliary files are on the same drive.
	
	Novell NetWare Login Scripts
	----------------------------
	The Login Script Processor for the Microsoft Client for NetWare should
	correctly process all commands in your login scripts. However, you
	cannot load memory-resident programs (TSRs) from these scripts.
	
	Installing Novell Client32 Overwrites
	NetWare Directory Services Files
	-------------------------------------
	When you install Novell Client32, the Novell setup program replaces
	the Microsoft file Netdef.inf and renames it Netdef.bnw, and deletes
	the NDS setup file Nwnds.dll. The result is that after uninstalling
	Novell Client32, Service for NetWare Directory Services will not
	install.
	
	To work around this problem, carry out the following steps:
	
	1. Find the file Netdef.bnw and rename it Netdef.inf.
	
	2. Copy the Nwnds.dll file to the Windows\System directory on your
	  your hard disk by carrying out the following procedure:
	
	  1. Insert your Windows 95 installation CD into the CD-ROM drive.
	  2. Open an MS-DOS window.
	  3. Change to the Win95 directory on your CD-ROM, and then type the
	     following at the command prompt:
	
	     extract /l c:\windows\system precopy2.cab nwnds.dll
	
	Upgrading Over an Earlier Beta Version of Windows
	-------------------------------------------------
	If you upgrade this release of Windows over an earlier beta release,
	and you have Service for NetWare Directory Services installed, you
	will be prompted about version conflicts for the following files:
	
	- Nwnp32.dll (v. 4.0.969)
	- Nwlsproc.exe (v. 4.0.968)
	- Netware.tmp (v. 4.0.968)
	
	When you see the version conflict prompt, click No. After Windows is
	installed, you need to reinstall Service for NetWare Directory Services.
	To do this, carry out the following steps:
	
	1. In Control Panel, double-click the Network icon.
	2. Click Add, click Service, and then click Add.
	3. Follow the instructions on your screen.
	
	Printing to NetWare Directory Services Printers
	-----------------------------------------------
	You cannot install Client for NetWare Networks and Service for NetWare
	Directory Services (NDS) during the same installation session. If you
	do, your NDS printers will appear to be offline.
	
	If your printers appear to be offline, try carrying out the following
	steps:
	
	1. In Control Panel, double-click the Network icon.
	2. Remove both Client for NetWare Networks and Service for NDS.
	3. Restart your computer.
	4. In Control Panel, double-click the Network icon.
	5. Add Service for NDS.
	6. Restart your computer.
	
	NOTE:
	If your local area network is using NetWare 4.1 or later, there is no
	need to install Client for NetWare Networks separately. When you install
	Service for NDS, it also installs the Client for NetWare Networks.
	
	PLUG AND PLAY NETWORK CARDS AND 16-BIT REAL-MODE DRIVERS
	========================================================
	
	When you run the 16-bit real-mode driver for your Plug and Play
	network interface card (NIC), your Plug and Play card might appear
	not to function.
	
	The reason the card appears to malfunction is that on most computers,
	the Plug and Play card is inactive until Windows 95 enables it. 16-bit
	NIC drivers load before Windows 95 can turn on Plug and Play cards.
	Some 16-bit NIC drivers do not recognize Plug and Play cards (most
	NE2000 Plug and Play clones fall into this category). In this case,
	follow these steps to use your Plug and Play card with a 16-bit NIC
	driver:
	
	1. Run the Softset utility that comes with your Plug and Play card,
	  and then set the card to non-Plug and Play mode.
	2. Remove the network card from the list of devices in the Device
	  Manager listing: In Control Panel, double-click the System icon,
	  click the Device Manager tab, select the network card, and then
	  click Remove.
	3. Reinstall the network card using the Add New Hardware icon in
	  Control Panel.
	
	When you install a 32-bit protect mode NIC driver in the future, you
	can rerun Softset to turn on Plug and Play mode for your card. This
	problem does not happen if you are using a 32-bit protect-mode NIC
	driver.
	
	INTEL ETHEREXPRESS 16 NICs AND PCI COMPUTERS
	============================================
	
	If you are using an Intel EtherExpress 16-network interface card (NIC)
	in a PCI computer that has a Diamond Speed Star PCI video card, your
	system might hang or not initialize properly. These problems, according
	to Intel customer support, are not related to Windows 95 and happen
	on a variety of operating systems.
	
	If you have one of the following video cards, contact your vendor to
	obtain a new video BIOS update:
	
	  * Diamond Speed Star PCI video card with BIOS version 1.01
	  * Diamond Viper PCI VGA Video Adapter
	  * Diamond Stealth video card, BIOS v1.03
	
	Other PCI video cards might also cause problems with this Intel NIC.
	In general, if you experience problems with your EtherExpress 16 in
	a PCI computer other than those described above, please replace the
	card before reporting the problem to Microsoft.
	
	WINDOWS FOR WORKGROUP SHARES
	============================
	
	When you upgrade to Windows 95 from Windows for Workgroups, your
	shares are not maintained. The folders/directories you shared in
	Windows for Workgroups need to be reshared.
	
	RUNNING WINDOWS 95 FROM A SERVER
	================================
	
	Windows 95 can be set up to run from a network server. The Windows 95
	Resource Kit contains complete instructions for installing Windows
	in this environment (see Chapter 4, "Server Based Setup for Windows 95").
	
	The following configurations are supported:
	
	- Booting from hard disk using:
	 - Client for Microsoft Networks
	 - Client for NetWare Networks
	 - Novell Workstation Shell 3.x (NETX)
	 - Novell Workstation Shell 4.x (VLM)
	 - Banyan VINES DOS/Windows client
	
	- Booting from a floppy disk using:
	 - Client for Microsoft Networks
	 - Client for NetWare Networks
	 - Novell Workstation Shell 3.x (NETX)
	 - Novell Workstation Shell 4.x (VLM)
	 - Banyan VINES DOS/Windows client
	
	- Booting from a remote boot server using:
	 - Client for NetWare Networks
	 - Novell Workstation Shell 3.x (NETX)
	 - Novell Workstation Shell 4.x (VLM)
	
	To use one of the Microsoft clients, your network card must have
	both an NDIS2 (16-bit real mode) *AND* an NDIS3 (32-bit protect
	mode) driver. If your network card is a PCI, EISA, or ISAPNP card,
	you must run Windows over a real-mode client.
	
	To Install Windows 95 over Previous Builds
	------------------------------------------
	To install this final version of Windows 95 on network computers that
	are already running Windows 95, you have two choices:
	
	- Do a clean install on each  computer;
	 -or-
	- Upgrade each computer using the following procedure:
	
	 1. Shut down any clients running from the server.
	 2. Windows 95 must be installed on the server into the same folder
	    that you were using for previous builds. Delete everything in the
	    shared Windows 95 folder, and then run Netsetup.exe to install this
	    build into that folder.
	 3. Restart the client to a command prompt.
	 4. If you are using the Microsoft Client for NetWare Networks and use
	    map rooted  drives, you must start either NETX or VLM to run Setup.
	 5. Map drives to the machine folder and shared Windows 95 folder
	    as before. These must use the same drive letters as used in the
	    previous build, and map roots should be to the same folder level.
	 6. Run Setup for the new build.
	
	SUPPORT FOR THIRD-PARTY NETWORKS
	================================
	
	To install support for a third-party, real-mode network, you must be
	running the network when you run Windows 95 Setup. Windows 95 does not
	support installation of a real-mode network after Setup, unless you have
	a Windows 95-specific .inf file from your network vendor. For example,
	FTP includes a Windows 95 .inf in their 32-bit NFS client. Although
	Windows 95 supports other networks, network component files for networks
	other than Microsoft networks are not included with Windows 95. You must
	already have the files for the network you want to install.
	
	LANDESK 2.0
	-----------
	LANDESK version 2.0 uses a TSR named Usertsr.exe that might cause
	Windows 95 to stop responding when you use the Microsoft IPX/SPX-
	compatible protocol (Nwlink.vxd) or file and printer sharing for
	Microsoft Networks (Vserver.vxd).
	
	LANDESK version 2.01 fixes this problem, and the patch is available
	on Intel's BBS or from Intel product support. For the BBS and product
	support telephone numbers, consult the documentation that came with your
	copy of LANDESK.
	
	SunSelect PC-NFS
	----------------
	Windows 95 supports versions 5.0 or greater of SunSelect PC-NFS.
	If SunSelect PC-NFS is installed using an NDIS 2 LAN driver or an
	ODI LAN driver, then SunSelect PC-NFS can be installed as an additional
	16-bit network client along with 32-bit protected-mode clients. If you
	are using a SunSelect PC-NFS LAN Driver, Windows 95 can support PC-NFS
	only as the primary network. Additional 32-bit network providers are not
	possible in this case.
	
	Banyan VINES
	------------
	If you see a message during startup that the VINES version is not the
	latest, edit the Vines.ini file in the Windows folder so it contains
	the following lines:
	
	  [NEWREV]
	  dontcopy=1
	  vines.version=5.5x (x) USA      ; where x=your version
	  windows.version=3.95
	
	If you receive the message, "Vines NDIS Interface error: 1021. See
	NDISBAN.DOC for an error description," during startup, run the VINES
	utility PCCONFIG to change Banyan drivers to NDIS drivers. Also, make
	sure the section name matches the driver name in the Protocol.ini file.
	
	DEC Pathworks
	-------------
	Windows 95 provides support for upgrading over existing DEC
	PATHWORKS V5.0, V5.0A and V5.1 configurations. This makes it possible
	to run your existing real-mode PATHWORKS components while migrating
	to Windows 95. However, it is strongly recommended that you upgrade
	to DEC's PATHWORKS for Windows 95, which contains protected-mode
	components.
	
	Restrictions:
	PATHWORKS must be started before running Windows 95 Setup to
	automatically detect and upgrade PATHWORKS components. If PATHWORKS
	is not started or is not automatically detected, you will see startup
	errors when you run STARTNET. To correct this, add the appropriate
	"PATHWORKS V5.0 and above" protocol, using the Network icon in Control
	Panel.
	
	Once a system has been upgraded to Windows 95, you cannot change your
	PATHWORKS configuration using PWSETUP. However, all existing template
	configurations present when you upgrade are converted to work under
	Windows 95.
	
	PATHWORKS Native, DLC, X.25, and ISDN datalinks are converted to use
	an NDIS driver, if available, during the upgrade. If the replacement
	NDIS driver is not configured correctly or is not operating, startup
	will display an error and prevent loading of other PATHWORKS components.
	
	To correct this, double-click the Network icon in Control Panel, and
	verify that the adapter driver is configured correctly. If any changes
	are made to the adapter configuration, you must remove the "PATHWORKS
	V5.0 and above" protocol and add it again.
	
	PATHWORKS NetWare client licenses (CCS or FPA) are not currently
	supported with Windows 95. If you are using the Microsoft Client for
	NetWare Networks to connect to PATHWORKS for OpenVMS (NetWare) or
	PATHWORKS for OSF/1 (NetWare) servers, the server must have PATHWORKS
	FPS licenses.
	
	Long filenames do not work correctly on PATHWORKS servers up to and
	including version 5.0b. You will be able to create and delete LFN
	files and make and remove LFN folders, but the files and folders will
	not appear when you use the DIR command, or when you open an Explorer
	window to the PATHWORKS server. PATHWORKS server version 5.00 EC01
	corrects this problem and is available from DEC.
	
	Artisoft LANtastic
	------------------
	The LANtastic server cannot be run when Windows 95 is setting up.
	
	LANtastic also cannot be run in conjunction with networking support
	for other networks.
	
	PRINTING TO A NETWORK PRINTER
	=============================
	
	You might have problems setting up a printer that is shared by a third-
	party network server. The solution is to redirect LPT1 through an
	MS-DOS window to the third-party share, and then use the printer setup
	for LPT1.
	
	For example, if a network printer is connected to LPT1, follow these
	steps:
	
	1. At the MS-DOS prompt, type:
	
	  net use lpt1: \\servername\sharename
	
	  (This command might be different on the network you are using.
	  Check the product documentation to find out how to redirect
	  an LPT port.)
	
	2. Start Control Panel, double-click Printers, and then double-click
	  Add Printer.
	
	PROBLEMS PRINTING TO POSTSCRIPT PRINTERS
	OVER A NETWARE NETWORK
	=========================================
	
	If you have problems when printing to a PostScript printer over a
	network, (error messages on the printer; no output is printed), it
	might be due to incorrectly configured Banner Pages. To solve this
	problem, you can do one of the following:
	
	- Disable banner pages by removing the check mark from the Banner Pages
	 box on the Capture printer properties (open the Printers folder, click
	 the icon for the printer you are using, and then click Properties on
	 the File menu);
	 -or-
	- Ask your network administrator to correctly configure banner pages on
	 the Netware server for a PostScript printer.
	
	ISSUES AND INSTALLATION OF
	MS-DLC WITH WINDOWS 95
	-=========================
	
	Windows 95 contains MS-DLC and support for installing over an existing
	MS-DLC or IBM-DLC installation. Setup will detect DLC and make the
	appropriate changes to your configuration files for these. Refer to
	the Windows 95 Resource Kit, Chapter 10, for a complete description
	of DLC support.
	
	MICROSOFT TCP/IP PROTOCOL
	=========================
	
	If Microsoft's TCP/IP is the only protocol you have loaded on your
	system, the IP Address will not be added during Setup. If you have
	a DHCP server, open Control Panel, double-click the Network icon, and
	then close it. This will update the IP Address. (If you don't know if
	you have a DHCP server, check with your network administrator, or check
	if your IP address is already entered.)
	
	If you don't have a DHCP server, start Control Panel, double-click
	the Network icon, double-click TCP/IP, click the IP Address tab, and
	then enter your IP Address.
	
	If you are not updating from a previous Windows 95 installation (you
	are doing a "clean install"), to use DNS or LMHOSTS name resolution,
	make sure you have DNS enabled in the Network properties. To enable
	DNS, double-click the Network icon in Control Panel, double-click
	TCP/IP, click the DNS configuration tab, and then click Enable DNS.
	
	USER PROFILES OVER THE NETWORK
	==============================
	
	If you are using user profiles over a Windows NT or Novell NetWare
	network, and you include Start Menu/Programs, Network Neighborhood,
	and/or desktop icons in your profile, the server must have long
	filename support to ensure that these parts of the user profile work
	over the network.
	
	NETWORK BACKUP AGENTS
	=====================
	
	Arcada Backup Exec Network Backup Agent
	---------------------------------------
	To use the Arcada Backup Exec network backup agent included in
	Windows 95, you must have Arcada Backup Exec version 5.x.
	
	Cheyenne ARCserve Network Backup Agent
	--------------------------------------
	To use the Cheyenne ARCserve network backup agent included in
	Windows 95, you must have Cheyenne ARCserve version 5.01F. You might
	also use earlier versions if you obtain updated NLMs from Cheyenne
	Software.
	
	REAL-MODE PROTOCOLS: WARNING ICONS ON YOUR NETWORK ADAPTER
	==========================================================
	
	If you install a network that does not use protected-mode protocols,
	such as Novell Netware 3.x, you might see a yellow warning icon next
	to your network adapter in Device Manager. You can ignore this warning;
	your network is fully functional. To remove the warning icon, use the
	program, Extract.exe on Setup disk 1 to extract the file Ndis.vxd from
	your Windows 95 disks. Then, copy Ndis.vxd into your Windows\System
	folder. When you reboot your system, the yellow warning icon will no
	longer appear.
	
	USING AN IBM THINKPAD WITH A DOCK II
	====================================
	If you enable 32-bit PCMCIA support, and your network cards do not
	appear to work properly when inserted into the Dock II's PCMCIA slots;
	or, if you have an ISA network card in the Dock II that has a "Code 10"
	error in its properties in Device Manager, call the IBM Help Center.
	They will provide you with a file to correct this problem.
	
	INTEL ETHEREXPRESS PRO /100B CARD NOT CORRECTLY DETECTED
	========================================================
	
	Windows 95 does not correctly detect an Intel EtherExpress Pro /100B
	card during Setup or hardware detection. After Setup, an entry for
	"PCI Ethernet controller" appears under Other Devices in Device Manager,
	which shows that the device is functioning properly; however, the card
	doesn't work.
	
	To properly install the card, remove the PCI Ethernet controller from
	Device Manager, and then restart your computer. The card will then be
	detected; the Update Device Driver wizard will appear.  Insert the
	driver disk that came with the card, and then click Next. The wizard
	will search the disk and find drivers for the Intel 82557-based PCI
	Ethernet. This is correct. Click Finish and the card should work.
	
	SETTING UP A WINS SERVER
	========================
	
	To set up a WINS server, carry out the following steps:
	
	1. In Control Panel, double-click the Network icon.
	2. Click TCP/IP, and then click Properties.
	3. Click the WINS Configuration tab.
	4. Make sure that both the Primary WINS Server and Secondary WINS
	  Server boxes are filled in.
	
	  If you have only one WINS Server, you must enter the identical
	  information in both the Primary WINS Server and Secondary WINS
	  Server boxes.
	
	  If you do not fill in both boxes, your WINS setting will be
	  changed to Disable WINS Resolution when you restart your computer.
	
	INTERLNK
	========
	The InterLnk networking product contained in MS-DOS 6.x does not
	function properly in MS-DOS mode if you are using FAT32.
	
	USING COMSPEC VARIABLES POINTING TO NETWORK COMMAND.COM FILES
	=============================================================
	
	If you are on a network and are currently mapping your compspec to
	remote network file servers, you may get "incorrect DOS version"
	errors (and an explanation of the version shipping with Windows 95
	version 4.00.950 B being an updated ver 7.1 etc.). You need to map
	the comspec to the local copy or to a compatible version on the network.
	
	Additional query words: 95
	
	======================================================================
	Keywords          : osr2 win95 
	Technology        : kbWin95search kbOPKSearch
	Version           : WINDOWS:95
	
	=============================================================================
	

{% endraw %}