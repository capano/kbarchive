---
layout: page
title: "Q77815: Novell NetWare Shell History 3.02, 3.21, and 3.22"
permalink: /kb/077/Q77815/
---

## Q77815: Novell NetWare Shell History 3.02, 3.21, and 3.22

{% raw %}

	Article: Q77815
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 3.0,3.0a
	Operating System(s): 
	Keyword(s): 
	Last Modified: 07-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.0, 3.0a 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The following information describes problems and enhancements addressed by, and
	the version history of, Novell's 3.02, 3.21, and 3.22 workstation shells.
	
	This information applies to Microsoft Windows versions 3.0, and 3.0a. This
	information does not apply to later versions of Windows.
	
	MORE INFORMATION
	================
	
	Netware 3.02
	------------
	
	Files           Versions        Dates
	-----           --------        -----
	
	NET3.COM        3.02            2-06-91
	NET4.COM        3.02            2-06-91
	XMSNET3.EXE     3.02            2-06-91
	XMSNET4.EXE     3.02            2-06-91
	EMSNET3.EXE     3.02            2-06-91
	EMSNET4.EXE     3.02            2-06-91
	
	Problems/Enhancements Addressed by 3.02
	---------------------------------------
	
	- 3.02 corrected a problem with file caching that was introduced with the
	  NetWare Shell 3.01e. 3.01e users experience problems when running Paradox,
	  Quattro, and Lotus 1-2-3 with the extended memory shells.
	
	- The speed of file caching is enhanced, which improves the speed of file read
	  and writes.
	
	- Some applications such as DESQview, NetRemote, and so on that use EMS, or XMS
	  occasionally hang when used with earlier versions of the enhanced memory
	  shells.
	
	- Unloading the shell relinquishes all connections in 3.02 (previously retained
	  one connection).
	
	- When setting parameter Cache Buffers=0 in NET.CFG, the shell caching is
	  turned off.
	
	- 3.02 corrected a problem where capturing to a file results in print files.
	  These files are now created and printed correctly.
	
	- 3.02 added two new NET.CFG parameters, DOS NAME and ENVIRONMENT PAD.
	
	        DOS NAME = name
	
	  This option specifies the name of the DOS version used by the workstation.
	  This should correspond to the OS name in the Login script and the name of the
	  DOS directory. This could be MSDOS, PCDOS, DRDOS, and so on, and cannot be
	  longer than five characters.
	
	        ENVIRONMENT PAD = number
	
	  This option specifies the number of bytes that can be added to the environment
	  space for storing search drive path. If you are specifying many long paths
	  for search drives with the MAP command, you may need to add extra environment
	  space to hold those names. This can be any number from 17 to 512; 17 is the
	  default. We recommend that you leave this option at the default value unless
	  you are encountering environment space problems.
	
	Netware 3.21
	------------
	
	Files           Versions        Dates
	-----           --------        -----
	<BR/><BR/>
	NET3.COM        3.21            7-18-91
	NET4.COM        3.21            7-18-91
	XMSNET3.EXE     3.21            7-18-91
	XMSNET4.EXE     3.21            7-18-91
	EMSNET3.EXE     3.21            7-18-91
	EMSNET4.EXE     3.21            7-18-91
	
	Problems/Enhancements Addressed by 3.21
	---------------------------------------
	
	- Generic Shell: NETX.COM works with all current versions of MS-DOS (that is,
	  versions 3.x to present).
	
	- Using the Preferred Server function caused some machines to hang randomly.
	
	- The /c = option was added to allow flexible naming of the shell configuration
	  file (NET.CFG).
	
	- The /f option was added to allow the shell to be unloaded after it had been
	  loaded high.
	
	- 3.21 added support for EMS memory handle names.
	
	- 3.21 added support for international date and time formats.
	
	- 3.21 corrected a problem with being denied simultaneous access to a shared
	  file.
	
	- 3.21 corrected "call 5" functions for programs ported from CPM to MS- DOS.
	
	- 3.21 added a feature to display the version of MS-DOS that is currently
	  running when the shell is loaded.
	
	- 3.21 resolved a problem where Btrieve files were being corrupted when the
	  server was downed improperly.
	
	- 3.21 corrected a cache problem that was causing a WordPerfect disk-full
	  error.
	
	- 3.21 corrected the DOS NAME parameter problem with the EMS and XMS shell. The
	  EMS and XMS shells would hang when loading if the MS-DOS NAME was used.
	
	- 3.21 corrected the problem with "P_STATION" returning bad information in the
	  Login script. (This problem only occurred with the version 3.2 shell.)
	
	- The MS-DOS 5.0 Load High command did not work properly with NET5.COM.
	  NETX.COM version 3.21 will work with the MS-DOS 5.0 Load High command.
	
	- The MS-DOS 5.0 MEM program was not displaying program names after the shell
	  was loaded. This functionality works with this release of the shell.
	
	- The MS-DOS Attrib command was unable to find hidden directories on network
	  drives.
	
	- 3.21 corrected a problem with remote boot on workstations with hard drives.
	
	- 3.21 added a date code to the shell. When you run Netx I, the shell will
	  display the shell version, date of creation, and copyright information.
	
	- The 3.21 shell was enhanced to locate the Master environment regardless of
	  its location.
	
	Netware 3.22
	------------
	
	Files           Versions        Dates
	-----           --------        -----
	
	NETX.COM        3.22            7-31-91
	XMSNETX.EXE     3.22            7-31-91
	EMSNETX.EXE     3.22            7-31-91
	
	Problems/Enhancements Addressed by 3.22
	---------------------------------------
	
	- 3.22 corrected a problem with remote boot and MS-DOS 5.0. Previously, the
	  shell would look to drive F rather than drive A (the virtual drive).
	
	REFERENCES
	==========
	
	Novell Shell's HISTORY.TXT, 9-2-91
	
	Additional query words: 3.00 3.00a work station net ware 3.0 3.0a kbnetwork
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin300 kbWin300a
	Version           : :3.0,3.0a
	
	=============================================================================
	

{% endraw %}
