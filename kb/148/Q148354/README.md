---
layout: page
title: "Q148354: PC NTMMTA: Contents of the Readme File, MMTA.TXT"
permalink: /kb/148/Q148354/
---

## Q148354: PC NTMMTA: Contents of the Readme File, MMTA.TXT

{% raw %}

	Article: Q148354
	Product(s): Microsoft Mail For PC Networks
	Version(s): WINDOWS:3.5; :3.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 07-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for PC Networks, version 3.5 
	- Microsoft Mail Multitasking MTA for Windows NT, version 3.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains the contents of the MMTA.TXT Readme file included on the
	Multitasking MTA for Windows NT Server version 3.5 disk.
	
	MORE INFORMATION
	================
	
	                   ------------------------------------------------------
	                 Microsoft Mail Multitasking MTA version 3.5
	                               README File
	           ------------------------------------------------------
	
	                 (C) Copyright Microsoft Corporation, 1991-95
	
	This document (MMTA.TXT) contains important information that
	supplements the Microsoft Mail Multitasking Message Transfer Agent
	Administrator's Guide.
	
	INFORMATION FOR MICROSOFT MAIL ADMINISTRATORS
	=============================================
	
	This section covers the following topics:
	
	1. New features on the MMTA
	  1.1  Hosted on Windows NT Server version 3.51
	  1.2  Run as a Windows NT service
	  1.3  Services can be remotely created and monitored
	2. Differences from previous releases
	  2.1  Drive usage when running as a Windows NT service
	  2.2  Warning regarding Windows NT File Manager and delivery to
	       postoffices hosted on Novell NetWare file servers while running
	       as a Windows NT service
	  2.3  EXTERNAL.INI and DISPATCH.INI Files
	  2.4  DrivesNovell .INI Option
	  2.5  Permanent drive mapping
	  2.6  Limit of External or Dispatch services per Windows NT computer
	  2.7  Home postoffice on NetWare servers
	  2.8  Remote service creation of External and Dispatch services
	  2.9  Remote monitoring of the External and Dispatch services
	  2.10 MONITOR.EXE command-line switches
	  2.11 SCHDIST.EXE will not run as a Windows NT service
	3. Eicon WAN services for Windows NT and the MMTA
	4. Specific Windows NT notes
	  4.1  Windows NT event logs
	  4.2  Notes for Banyan administrators
	  4.3  Using Performance Monitor
	
	1. New Features of the MMTA
	---------------------------
	
	This release of the Microsoft Mail Multitasking Message Transfer Agent has a
	number of new features over the previous version. These features are described
	in the following subsections.
	
	1.1 Hosted on Windows NT Server Version 3.51
	--------------------------------------------
	
	This release requires Windows NT Server version 3.51, build 1057 or higher.
	
	1.2 Runs as a Windows NT Service
	--------------------------------
	
	This release supports the External MTA and Dispatch directory- synchronization
	applications running as services under Windows NT.
	
	Note: The user associated with the service must have the Windows NT "Log on as a
	Service" privilege. For more details, see "Configuring a Windows NT Service" in
	Chapter 2 of the Administrators Guide.
	
	1.3 Services Can Be Created and Monitored Either Locally or Remotely
	--------------------------------------------------------------------
	
	The Microsoft Mail Service Manager application created in the Microsoft Mail
	program group allows you to create and monitor services on either the Windows NT
	Server you have installed to or on a remote LAN/WAN- connected Windows NT
	Server.
	
	2. Notes for Administrators
	---------------------------
	
	2.1 Drive Usage When Running as a Windows NT Service
	----------------------------------------------------
	
	When running as a service under Windows NT, it is recommended that you do not
	make drive connections from the File Manager or command prompt in the range used
	by MMTA services. Each service that is connecting to multiple postoffices will
	use three drives. The first is for the home postoffice, and the others are for
	dynamic drives. It is suggested that you monitor the service, check which drives
	are being used, and if you do need to connect to another server, use an unused
	drive.
	
	2.2 Warning regarding Windows NT File Manager and delivery to
	   postoffices hosted on Novell NetWare file servers while running
	   as a Windows NT service
	-------------------------------------------------------------------------------------------------------------------------------------------------------------
	
	When the MMTA is running as a Windows NT service and messages are being sent or
	received from a postoffice hosted on a NetWare file server, selecting the File
	Manager Window.Refresh option may freeze that MMTA instance. The MMTA will
	display an error "Drive is either local, used or greater than LASTDRIVE." To
	recover from this, stop and restart the MMTA instance. It is strongly suggested
	that this option not be selected in File Manager when an MMTA service is
	running.
	
	Note: This will leave a connected drive that cannot be disconnected. The only way
	to clear this drive is to reboot Windows NT.
	
	2.3 Executable and .INI Files
	-----------------------------
	
	When running as a Windows NT service, all executables and .INI files must either
	be local to the computer the service is hosted on or a UNC path must be given.
	
	Note:. There is a greater reliance in this release on the EXTERNAL.INI and
	DISPATCH.INI files. Command-line switches are still available, but it is
	suggested you move all commands to the .INI file.
	
	2.4 DrivesNovell .INI Option
	----------------------------
	
	The DrivesNovell .INI file option has been removed and all paths to postoffices
	must be in the DrivesUNC format. For more details about the DrivesUNC option,
	see the "Connecting Postoffices" section in Appendix A of the MMTA
	Administrator's Guide.
	
	2.5 Permanent Drive Mapping
	---------------------------
	
	When running as a Windows NT service, only the home postoffice is mapped as a
	permanent drive. All others will be handled dynamically.
	
	NOTE: Specific drive mappings cannot be specified to either the External or
	Dispatch services.
	
	2.6 Limit of External or Dispatch Services per Windows NT Computer
	------------------------------------------------------------------
	
	If each service that is created is one which includes LAN/WAN connections to
	other postoffices, there is a maximum of 7 concurrent MMTA services that can be
	run on each Windows NT server. This is because each service maps one drive for
	its home postoffice and two for its dynamic range. If an eighth service is
	started, a Windows NT error 2140 will be displayed by the Windows NT service
	manager.
	
	Note: If a service has the Single Postoffice Service option checked in the
	Microsoft Mail Service Manager, that service will only use one drive mapping.
	
	2.7 Home Postoffice on NetWare Servers
	--------------------------------------
	
	A service that is created with the Home Postoffice set to a postoffice hosted on
	a NetWare Server will need the service account to have a valid account with the
	same name on the NetWare server. The password must also be the same.
	
	2.8 Remote Service Creation of External and Dispatch Services
	-------------------------------------------------------------
	
	When a service is created remotely, the path given to the executables and .INI
	file must be able to be reached from the computer where the service is created.
	It is suggested that UNC paths be given in that case.
	
	2.9 Remote Monitoring of the External and Dispatch Services
	-----------------------------------------------------------
	
	The MMTA now allows for monitoring of the External or Dispatch services either
	from the Windows NT computer the service is running on or a remote Windows NT
	computer. For more details, see the "External Configurations for the MS-DOS
	Workstations" section of Chapter 3 of the Administrators Guide.
	
	2.10 Monitor from a Command Line
	--------------------------------
	
	The Monitor option in the Microsoft Service Manager application is also able to
	be called from the command line using the following command:
	
	  Monitor [external|dispatch] <\\computer_name> <instance_name>
	
	External|Dispatch - The type of service
	\\computer_name   - Name of the Windows NT Server running the service
	instance_name     - Name of the instance that should be monitored
	
	Note: If you want to monitor specific instances regularly, create a batch file
	containing the preceding command and place it on your Windows NT desktop or in
	the Start folder.
	
	2.11 SCHDIST.EXE Will Not Run as a Windows NT Service
	-----------------------------------------------------
	
	SCHDIST.EXE is not supported as a Windows NT service and can only be run from
	within a Windows NT command prompt.
	
	3. Eicon WAN Services for Windows NT and the MMTA
	-------------------------------------------------
	
	For information about installing the Eicon Gateway software, see the Eicon
	documentation and Appendix F, "X.25 Settings for Mail," in the Microsoft Mail
	Administrator's Guide. Your Eicon setup must match the configuration of the line
	leased from your X.25 carrier. The X.25 service must be running. Values vary by
	carrier and installation-- confirm all values set by the ECCFG program with your
	carrier.
	
	Before running the MMTA to use X.25 communications, the Eicon X.25 card must be
	installed on the Windows NT computer running the Eicon WAN Services for Windows
	NT Version 3, Release 2. For more information about installing and testing these
	components, see the documentation that comes with the Eicon product.
	
	The Multitasking MTA uses a series of translation files to convert the OS/2 X.25
	API calls to Windows NT API calls. This process of converting APIs is known as
	"thunking." The X.25 thunk layer relies on 3 DLL files and the Eicon WAN
	services for NT service. These .DLL files are:
	
	1. WINNT\SYSTEM32\OS2\DLL\X25.DLL
	
	2. WINNT\SYSTEM32\X25T32.DLL
	
	3. WINNT\SYSTEM32\X25NTM8.DLL
	
	The Microsoft Mail Administrator's Guide provides information about options that
	are critical when setting up the Eicon board and software. For the configuration
	option Number Of TVCs, a value of 004 is suggested. The correct value depends on
	the line installed--a different value could be appropriate for your
	configuration.
	
	4. Specific Windows NT Tips
	---------------------------
	
	4.1 Windows NT Event Logs
	-------------------------
	
	When the MMTA is running in trusted Windows NT domains, the Security event log
	will have an entry for every connection the MMTA makes. It is suggested that you
	set a limit to the size of the event log.
	
	4.2 Notes for Banyan Administrators
	-----------------------------------
	
	The Multitasking MTA cannot service postoffices hosted on Banyan servers when
	running as a Windows NT service. These servers can be serviced by the MMTA in a
	console. For notes on the syntax for accessing a Banyan server with a UNC path,
	see the Release Notice for the Banyan Enterprise Client for Windows NT Version
	5.56 (5) or higher.
	
	4.3 Using Performance Monitor
	-----------------------------
	
	Performance Monitor is a graphical tool for measuring the performance of your own
	Windows NT-based computer or other Windows NT-based computers on a network. It
	is located in the Administrative Tools group of both the Windows NT Workstation
	and Windows NT Server products. On each computer, you can view the behavior of
	objects such as processors, memory, cache, threads, and processes. Each of these
	objects has an associated set of counters that provide information on such
	things as device usage, queue lengths, and delays, as well as information used
	for throughput and internal congestion measurements. It provides charting,
	alerting, and reporting capabilities that reflect current activity along with
	ongoing logging. You can also open log files at a later time for browsing and
	charting as if they were reflecting current activity.
	
	This section discusses memory usage and which counters are effective in detecting
	memory bottlenecks.
	
	4.3.1 Memory - Pages/sec
	------------------------
	
	Pages/sec is the number of pages read from the disk or written to the disk to
	resolve memory references to pages that were not in memory at the time of the
	reference. As a rule, you can assume that if the average of this counter is
	consistently greater than 5, then memory is probably becoming a bottleneck in
	the system. Once this counter starts to average consistently at 10 or above,
	performance is significantly degraded and disk thrashing is probably occurring.
	
	4.3.2 Memory - Available Bytes
	------------------------------
	
	Available Bytes displays the amount of free physical memory. If this counter
	stays consistently below 1 MB on servers and 4 MB on workstations, paging is
	occurring and performance is less than optimal.
	
	4.3.2 Memory - Committed Bytes
	------------------------------
	
	Committed Bytes displays the size of virtual memory (in bytes) that has been
	committed (as opposed to simply reserved). If this counter is greater than the
	amount of main memory, it indicates that main memory may not be large enough to
	accommodate all functions of all currently active processes--some paging may be
	inevitable. However, before making such an assumption, you should check Memory -
	Pages/sec and Memory - Page Faults/sec. If the Memory - Pages/sec is greater
	than 10 (10 is a reasonable guideline, but varies with disk hardware) and Memory
	- Page Faults/sec is greater than Memory - Cache Faults/sec, then you are paging
	too much.
	
	When Memory - Committed bytes approaches the Memory - Commit Limit and the page
	file has already reached maximum page file size, there are simply no more pages
	available, in main memory or in the page file. The Memory - Commit Limit is the
	amount of virtual memory that can be committed without extending the page file.
	If this occurs on a server running Windows NT Server, you may experience 3
	errors in the Event Log. (EVENTVWR.EXE is located in the Administrative Tools
	group). They are from the source: SRV.
	
	  2020: The server was unable to allocate from the system paged pool because
	  the pool was empty.
	
	  2001: The server was unable to perform an operation due to a shortage of
	  available resources.
	
	  2016: The server was unable to allocate virtual memory.
	
	  If this occurs, it is generally related to a memory leak in another process.
	  To determine the process at fault, you can monitor each process's Page File
	  bytes or Working Set.
	
	Another condition you may want to be aware of is the following nonpaged pool
	error in the server's Event Log:
	
	  2019: The server was unable to allocate from the system nonpaged pool because
	  the pool was empty.
	
	  Nonpaged pool pages cannot be paged out to the paging file, but instead
	  remain in main memory as long as they are allocated. By default,
	  NonPagedPoolSize is dynamically calculated as follows:
	
	  You can monitor the system's nonpaged pool allocation with the "Memory Pool
	  Non Paged Bytes" counter. If there is a shortage of nonpaged pool, you may
	  also see the following error on a remote system or even the local system:
	
	  Not enough storage available to process this command. If this occurs, start
	  looking at each process's nonpaged pool allocation. This is generally caused
	  by an application incorrectly making system calls and using up all allocated
	  nonpaged pool.
	
	4.3.4 Adding More Memory
	------------------------
	
	To determine how much memory to add, use the following formula:
	
	  Paging File - % Usage - MAX * Page file size = number of bytes used
	
	Add together the bytes used for all page files. This is the amount of memory that
	would need to be added to allow all of the applications to perform their
	operations with minimum paging. For example, if your page file is 100 MB and the
	% Usage MAX is 20%, then you would need 20 MB additional RAM to have a system
	that does minimal paging. The reason this formula only gives you an idea about
	how much memory to add is that a) not all page file "in use" code is accessed
	all of the time; and b) the formula ignores the requirements for code and mapped
	files not backed by the paging file. Therefore, this estimate is neither an
	upper bound, nor a lower bound--it is only an "indication." The truth is that
	there is no good way to know how much memory to add at this time. A more
	accurate way to measure the amount of memory an application would require is to
	run the application on a very large machine and measure the needs under some
	slight memory pressure. (There is a tool in the Windows NT Resource Kit, volume
	3, Utilities, called Response Probe, that can aid in this area.)
	
	NOTE: Adding memory without upgrading the secondary cache size sometimes degrades
	processor performance. This is because the secondary cache now has to map the
	larger memory space, usually resulting in lowered hit rates in the cache. This
	slows down processor-bound programs because they are scattered more widely in
	memory after memory has been added. (Secondary cache refers to the physical
	cache memory chip(s) usually located on the motherboard, as opposed to within
	the processor itself. In the future, processors will be built with secondary
	cache on the same substrate as the processor chip, or even within the processor
	chip itself.)
	
	Additional query words: 3.50
	
	======================================================================
	Keywords          :  
	Technology        : kbZNotKeyword2 kbMailSearch kbZNotKeyword3 kbMailPCN350 kbMailMMTA350NT
	Version           : WINDOWS:3.5; :3.5
	
	=============================================================================
	

{% endraw %}
