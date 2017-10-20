---
layout: page
title: "Q96004: PC DirSync: Error and Status Msgs #120 - 249"
permalink: /kb/096/Q96004/
---

## Q96004: PC DirSync: Error and Status Msgs #120 - 249

{% raw %}

	Article: Q96004
	Product(s): Microsoft Mail For PC Networks
	Version(s): WINDOWS:3.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 20-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for PC Networks, version 3.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	DIRECTORY SYNCHRONIZATION ERROR AND STATUS MESSAGES #120 - 249
	--------------------------------------------------------------
	
	On Microsoft Mail for PC Networks version 3.0 Server Disk 1, there is a file
	called DIRSYNC.TXT that contains the error codes used in directory
	synchronization (Dir-Sync) and in the IMPORT utility for Mail. The errors are
	logged in the DIRSYNC.LOG file.
	
	  [120] Requestor not registered
	
	  The specified requestor is not registered with the directory server
	  postoffice. Instruct the requestor administrator to register with the
	  Administrator program Config Dir-Sync Requestor Registration command. The
	  directory server administrator should also create the requestor with the
	  Administrator program Config Dir-Sync Requestors Create command.
	
	  [123] Could not compress file
	
	  The directory server could not back up the master update file MSTTRANS.GLB or
	  the server configuration file. Ensure that there is still a connection to the
	  server and try the operation again. Also check that there is sufficient disk
	  space to perform the compression.
	
	  [124] Invalid transaction format
	
	  Ensure that there is sufficient disk space to perform the operation.
	
	  If the requestor is a foreign requestor, ensure that:
	
	- The system message is in the correct format and starts with [dirsync]
	
	- The foreign requestor did not forget to include an attachment file if one was
	  specified
	
	- If there is an attachment file, it is in the correct format and starts with
	  [dirsync-transactions]
	
	  Wait at least one synchronization cycle and the problem should clear itself
	  up.
	
	  [125] Failure to copy attachment file
	
	  Ensure that there is sufficient disk space at the directory server postoffice
	  to perform the operation.
	
	  If the attachment is from a foreign requestor, check that the foreign
	  requestor did not forget to send an attachment with the system message. Wait
	  at least one synchronization cycle as the problem will most likely clear up
	  on its own.
	
	  [128] Could not process requestor status report
	
	  Ensure that there is still a connection to the server. Also ensure that there
	  is sufficient disk space to receive the report. Wait at least one directory
	  synchronization cycle and try the operation again. If the problem continues,
	  contact Microsoft Product Support Services.
	
	  [129] Could not find specified sync number
	
	  Wait at least one synchronization cycle and the problem should clear on its
	  own. If the problem continues, copy a backup of the MSTTRANS.GLB file, then
	  ask all requestors to export their address lists.
	
	  [133] Invalid Server Request
	
	  Ensure that the directory server's requestor schedule does not have any
	  errors. Check the requestor schedule. Ensure that there is enough time for
	  the server mail to reach the requestor postoffice.
	
	  [136] The local requestor is not registered
	
	  Ensure that this postoffice is registered as the directory server with the
	  Administrator program Config Dir-Sync Options command.
	
	  [150] Could not append transactions to the updates file
	
	  Ensure that:
	
	- There is sufficient disk space to perform the operation.
	
	- The computer running the Dispatch program has 640K of memory and that
	  FILES=20 (minimum) in the CONFIG.SYS file.
	
	  If the mail is from a foreign requestor, check that the foreign requestor did
	  not forget to send an attachment with the system message. If the problem
	  continues, wait at least one synchronization cycle as the problem will most
	  likely clear up on its own.
	
	  [151] Requestor configuration busy
	
	  Try the operation again. If the problem continues, the REQCONF.GLB may be
	  locked open. Contact your network vendor to determine how to find and close
	  files that are locked open.
	
	  [154] Non-delivery report from
	
	  This is an information message. The requestor received a directory
	  synchronization message that is not addressed to it and is not from a $SYSTEM
	  (directory synchronization) mailbox. This message is put in the DIRSYNC.LOG
	  file. The directory server may receive a directory synchronization message
	  that is not addressed to a $SYSTEM mailbox. This message is redirected to the
	  administrator.
	
	  [155] Invalid DirSync profile from
	
	  The directory server received a directory synchronization message with
	  unknown TASK= values. The mail likely has a TASK= value that is not supported
	  by the server. See [133]. This message is redirected to the directory server
	  administrator who should notify the foreign requestor administrator of the
	  problem.
	
	  [156] Invalid DirSync password from
	
	  The specified password in the directory synchronization system message does
	  not match the password in that is registered with the directory server
	  postoffice. The directory server administrator and the requestor
	  administrator should determine which is the correct password.
	
	  [157] DirSync software version out of sync
	
	  Ensure that the directory server and all requestors have upgraded to version
	  3.0.
	
	  [158] Requestor not registered
	
	  See [120].
	
	  The specified requestor is not registered with the directory server
	  postoffice. Instruct the requestor administrator to register with the
	  Administrator program Config Dir-Sync Requestor Registration command. The
	  directory server administrator should also create the requestor with the
	  Administrator program Config, Dir-Sync, Server, Requestors, Create command.
	
	  [159] Failure to send update mail to requestor
	
	  Ensure that:
	
	- There is still a connection to the server.
	
	- That there is sufficient disk space to receive the mail.
	
	- The computer running the Dispatch program has 640K of memory and that
	  FILES=20 (minimum) in the CONFIG.SYS file.
	
	  If the problem continues, wait at least one directory synchronization cycle
	  and the problem should clear on its own.
	
	  [161] Server configuration busy
	
	  Try the operation again. If the problem continues, the SRVCONF.GLB may be
	  locked open. Contact your network vendor to determine how to find and close
	  files that are locked open.
	
	  [162] Failure to transmit server updates
	
	  Ensure that:
	
	- There is still a connection to the server.
	
	- There is sufficient disk space to receive the updates.
	
	- The computer running the Dispatch program has 640K of memory and that
	  FILES=20 (minimum) in the CONFIG.SYS file.
	
	  If the problem continues, wait at least one directory synchronization cycle
	  and as the problem should clear on its own.
	
	  [163] Failure to copy server updates
	
	  Ensure that:
	
	- There is still a connection to the server.
	
	- There is sufficient disk space to copy the updates.
	
	- The computer running the Dispatch program has 640K of memory and that
	  FILES=20 (minimum) in the CONFIG.SYS file.
	
	  If the problem continues, wait at least one directory synchronization cycle
	  and the problem should clear on its own.
	
	  [166] Manual import required for
	
	  The size of the message generated to send the directory synchronization
	  updates to the specified requestor exceeds the limit set by the requestor. A
	  manual import procedure as described in The Administrator's Guide is
	  required.
	
	  [201] Warning .USR file missing
	
	  This is an information message. There is a postoffice without a list of
	  users.
	
	  [202] No Valid Postoffice found
	
	  Try the operation again. If the problem continues, check for that the
	  MASTER.GLB file is in the GLB directory. If it is not there, it may have been
	  accidentally deleted and you should restore a backup of your data files. If
	  it is there, it may be locked open. Contact your network vendor to determine
	  how to find and close files that are locked open.
	
	  [203] GAL Rebuild problem accessing files
	
	  Ensure that:
	
	- There is sufficient disk space to perform the operation.
	
	- The computer running the Rebuild utility has 640K of memory and that FILES=20
	  (minimum) in the CONFIG.SYS file.
	
	- Novell users have sufficient access rights.
	
	  [204] GAL Rebuild out of disk space
	
	  The Rebuild utility needs extra temporary disk space during sort and merge
	  operations. Ensure that there is sufficient disk space to perform the
	  operation.
	
	  [249] Not enough free file handles
	
	  Ensure that the computer running the Rebuild utility has 640K of memory and
	  that FILES=20 (minimum) in the CONFIG.SYS file.
	
	
	Additional query words: 3.00
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3 kbMailPCN300
	Version           : WINDOWS:3.0
	
	=============================================================================
	

{% endraw %}