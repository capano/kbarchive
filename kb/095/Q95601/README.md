---
layout: page
title: "Q95601: Windows Err Msg: Corrupt Swap File or Unsupported DOS Version"
permalink: /kb/095/Q95601/
---

## Q95601: Windows Err Msg: Corrupt Swap File or Unsupported DOS Version

{% raw %}

	Article: Q95601
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:6.0,6.2,6.21,6.22; WINDOWS:3.0,3.0a,3.1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 16-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 6.0, 6.2, 6.21, 6.22 
	- Microsoft Windows versions 3.0, 3.0a, 3.1 
	- Microsoft Windows for Workgroups version 3.1 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	You may receive one of the following error messages if you are running Windows
	and MS-DOS:
	
	  Windows 3.1:
	
	  Corrupt Swap File Warning - The permanent swap file is corrupt
	
	  Windows 3.0:
	
	  Corrupt Swap File Warning - Your swap file is corrupt
	
	  Windows 3.0:
	
	  Unsupported DOS version; upgrade to DOS version 3.1 or higher
	
	These messages can occur after you install DoubleSpace or after you attempt to
	create a permanent swap file (PSF) on a compressed drive. This article covers
	the following subjects:
	
	- Attempting to Create a Permanent Swap File (PSF) on a Compressed Drive
	
	- Receiving the Error "Corrupt Swap File Warning" After Installing DoubleSpace
	
	- Receiving the "Unsupported DOS Version" Error Message
	
	- Why You Cannot Have a PSF on a Compressed Drive
	
	- Why Windows Doesn't Detect DoubleSpace
	
	- Troubleshooting Problems Encountered When Working Around This Problem
	
	MORE INFORMATION
	================
	
	Attempting to Create a Permanent Swap File (PSF) on a Compressed Drive
	----------------------------------------------------------------------
	
	To work around this situation, delete the PSF and create a PSF on your host
	drive.
	
	The host drive is the drive that actually contains the DoubleSpace compressed
	volume file (CVF). To determine which drive is your host drive, type "dblspace
	/list" (without the quotation marks) at the MS-DOS command prompt and then press
	ENTER. Any drive listed as a "Local hard drive" is valid for a PSF.
	
	When you create a new PSF on the host drive, you may receive the following
	warning:
	
	  Windows will not use more than the virtual memory specified by the
	  Recommended Size. Are you sure you want to create a larger swap file?
	
	As long as the PSF is not larger than four times your physical memory, Windows
	can use a swap file that is larger than the Recommended Size.
	
	Receiving the Error "Corrupt Swap File Warning" After Installing DoubleSpace
	----------------------------------------------------------------------------
	
	If you receive the "Corrupt Swapfile Warning" error message after installing
	DoubleSpace, it is likely that your SYSTEM.INI file was not changed to reflect
	the PSF drive letter change.
	
	NOTE: In some cases, you do not receive this error; instead, the machine stops
	responding (hangs) when you start Windows.
	
	To work around this problem, refer to the section in this article titled
	"Attempting to Create a Permanent Swap File (PSF) on a Compressed Drive."
	
	If you cannot run Windows because it hangs, do the following:
	
	1. Use MS-DOS Editor to edit the [386Enh] section of the SYSTEM.INI file and set
	  Paging=NO.
	
	2. Save the SYSTEM.INI file and quit MS-DOS Editor.
	
	3. Run Windows, then and refer to the section in this article titled "Attempting
	  to Create a Permanent Swap File (PSF) on a Compressed Drive."
	
	Receiving the "Unsupported DOS Version" Error Message
	-----------------------------------------------------
	
	When you run Windows 3.0 in real mode (in order to run SWAPFILE.EXE), you receive
	the following message:
	
	  Unsupported DOS version; upgrade to DOS version 3.1 or higher
	
	This message is occurs when you have a corrupted permanent swap file (PSF) or you
	just installed MS-DOS.
	
	If you have SPATCH.BAT from MS-DOS 6.2 or the MS-DOS 6 Supplemental Disk, you can
	work around this problem by running SPATCH.BAT (regardless of which version of
	Windows you have). To do so, type the following at the command prompt:
	
	  " spatch <drive>:<path> " (without the quotation marks)
	
	For <drive> and <path>, specify the location of your Windows
	directory. For example, if your Windows directory is on drive C and is named
	WINDOWS, you would type the following:
	
	  " spatch c:\windows " (without the quotation marks)
	
	If you have SPATCH.BAT included with MS-DOS 6.0 and Windows 3.0, you must use the
	version of SPATCH.BAT available on the MS-DOS 6 Supplemental Disk or upgrade to
	MS-DOS 6.2. As an alternative, you can modify the SPATCH.BAT file provided with
	the MS-DOS 6 Upgrade by using an ASCII text editor, such as MS-DOS Editor, to
	change the SET ADDR= line in SPATCH.BAT from "SET ADDR=2df2" to "SET ADDR=2dc0"
	(without the quotation marks). To use the MS-DOS 6.0 version of SPATCH.BAT, use
	the following syntax:
	
	  " spatch <drive>:<path>swapfile.exe " (without the quotation
	  marks)
	
	For <drive> and <path>, specify the location of your SWAPFILE.EXE
	file. For example, if your SWAPFILE.EXE file is on drive C in the WINDOWS\SYSTEM
	directory, you would type the following:
	
	  " spatch c:\windows\system\swapfile.exe " (without the quotation marks)
	
	NOTE: The version of SPATCH.BAT on the MS-DOS 6 Supplemental Disk and the version
	included with MS-DOS 6.2 work on both the Windows 3.0 and Windows 3.0a
	SWAPFILE.EXE files.
	
	If you have Windows 3.0 (not 3.0a) and you run the version of SPATCH.BAT provided
	with MS-DOS 6 Upgrade, your SWAPFILE.EXE file will be corrupted. You can restore
	this file by copying the SWAPFILE.SAV file as SWAPFILE.EXE to your Windows
	directory. The SWAPFILE.SAV file is not always easy to find because it is placed
	in the directory from which you ran SPATCH.BAT. For example, if you ran
	SPATCH.BAT from the root directory of your C drive, use the following command to
	restore your PSF:
	
	  " copy c:\swapfile.sav c:\windows\swapfile.exe " (without the quotation
	  marks)
	
	To obtain the MS-DOS 6 Supplemental Disk, use the order form in the back of the
	"User's Guide."
	
	Why You Cannot Have a PSF on a Compressed Drive
	-----------------------------------------------
	
	Windows accesses a PSF directly through the disk controller if the 32-Bit Disk
	Access (FastDisk) option is selected. If this option is not selected, Windows
	uses the BIOS to access the PSF. Both these methods access your hard disk at a
	level that is below compressed drives. This causes Windows to read invalid data
	and issue the "Corrupt Swap File Warning" message.
	
	Why Windows Doesn't Detect DoubleSpace
	--------------------------------------
	
	Windows cannot create a PSF on a compressed volume file (CVF) created by a
	disk-compression program (such as DoubleSpace, Stacker, and SuperStor). Since
	Windows performs direct disk read/write operations to a PSF, the swap file must
	be located on a physical hard disk, not a CVF.
	
	
	NOTE: Because DoubleSpace had not been developed when Windows 3.1 was released,
	it was not possible to add detection code to Windows to prevent it from
	installing on a DoubleSpace drive.
	
	Troubleshooting Potential Problems with the Workaround
	------------------------------------------------------
	
	If there is not enough disk space on an uncompressed drive for a swap file, you
	must either delete files from the host drive or reduce the size of the
	compressed drive.
	
	For example, if your compressed drive is C and your host drive is H, you could
	use the following command to decrease the size of the compressed drive, creating
	12 megabytes (MB) of free space on the host drive (H):
	
	  dblspace /size /reserve=12 c:
	
	If you receive the error message "Drive C is too fragmented to resize," type
	"defrag /h /q c:" (without the quotation marks) at the MS-DOS command prompt and
	then press ENTER.
	
	For more information on DoubleSpace, do the following:
	
	- Type "help dblspace" (without the quotation marks) at the MS-DOS command
	  prompt and then press ENTER.
	
	-or-
	
	- Type "dblspace" (without the quotation marks) at the MS-DOS command prompt,
	  press ENTER, then choose Contents from the Help menu.
	
	Additional query words: fastdisk 6.00 swapfile dblspace double space dblspace.exe err msg errmsg
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbWin3xSearch kbWFWSearch kbZNotKeyword3 kbWin300 kbWin300a kbWin310 kbWFW310 kbMSDOSSearch kbMSDOS621 kbMSDOS622 kbMSDOS620 kbMSDOS600
	Version           : MS-DOS:6.0,6.2,6.21,6.22; WINDOWS:3.0,3.0a,3.1
	
	=============================================================================
	

{% endraw %}
