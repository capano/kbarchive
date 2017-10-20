---
layout: page
title: "Q170777: INFO: Interpreting 802.2 DLC Outage Code from SNA Server Level 2"
permalink: /kb/170/Q170777/
---

## Q170777: INFO: Interpreting 802.2 DLC Outage Code from SNA Server Level 2

{% raw %}

	Article: Q170777
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.0,2.1,2.11,2.11 SP1,2.11 SP2,3.0,3.0 SP1,3.0 SP2,3.0 SP3,4.0,4.0 SP1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 12-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.0, 2.1, 2.11, 2.11 SP1, 2.11 SP2, 3.0, 3.0 SP1, 3.0 SP2, 3.0 SP3, 4.0, 4.0 SP1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The SNA Server 802.2 DLC link service communicates over the Windows NT DLC
	transport protocol to support DLC connections over Token Ring, Ethernet, or
	FDDI. If a 802.2 DLC connection is lost for any reason, the Windows NT DLC
	interface returns a DLC status code in a DLC READ response to the SNA Server
	802.2 link service. This status code is interpreted by the link service and
	mapped to the actual "qualifier" that is reported in the Windows NT application
	event log as follows:
	
	  Source: SNA Server
	  Event ID: 23
	  Description:
	  Connection <name> using Link Service <link> failed.
	  Qualifier = 00xx
	
	The qualifier codes are documented in the SNA Server Reference Guide. For 802.2
	links, the following qualifiers can occur:
	
	  29 = Remote node not active
	  AE = DISC/DM received
	  AF = Link lost
	  AB = SABME received while connection active
	  AC = FRMR (frame reject) sent
	  AD = FRMR (frame reject) received
	
	If a FRMR is causing the connection failure, SNA Server will indicate additional
	information about the FRMR in one of the following events:
	
	  Event 227  FRMR received
	  (Windows NT DLC received a FRMR from the remote system)
	
	  Event 228  FRMR sent
	 (Windows NT DLC sent a FRMR to the remote system)
	
	These events include a "FRMR code" returned by DLC to indicate the cause of the
	FRMR.
	
	This article describes how to interpret the DLC status code returned by the DLC
	READ response, which can be captured within an SNA Server 802.2 link service
	"Level 2" trace.
	
	NOTE: It is not necessary to decode the READ response from a Level 2 trace to
	determine the cause of a failure, since the Event 23, 227, and 228 events
	already indicate the relevant information.
	
	MORE INFORMATION
	================
	
	The Windows NT DLC programming interface (DLCAPI.DLL), supports the CCB2 DLC
	interface, as documented by the IBM Local Area Network Technical Reference (IBM
	document #SC30-3383). This interface is used by the SNA Server 802.2 link
	service to support SNA communication over Token Ring, Ethernet, and FDDI.
	
	After an 802.2 DLC connection is established, the DLC interface indicates a
	connection failure to SNA Server by responding to a DLC READ command and
	indicating a DLC Status code. Here is the format of the READ structure returned
	by DLC:
	
	  CCB2 Structure
	  ==============
	
	  Parameter       Byte Len  Type  Description
	
	  CCB_ADAPTER        1      DB    Adapter number (0 or 1)
	  CCB_COMMAND        1      DB    Command field (31 = READ)
	  CCB_RETCODE        1      DB    Completion code
	  CCB_WORK           1      DB    Adapter support software work area
	  CCB_POINTER        4      DW    Queue pointer
	  CCB_CMPL_FLAG      4      DD    Command completion flag
	  CCB_PARM_OFFSET    2      DW    Offset to CCB2 parameter table
	                                (Pointer to READ Parameter Table below)
	
	  [ other parameters ]
	
	  CCB2 Parameter Table for READ
	  =============================
	
	  Parameter       Byte Len  Type  Description
	
	  STATION_ID         2      DW   SAP station ID
	  OPTION_INDICATOR   1      DB   READ option indicator
	  EVENT_SET          1      DB   Set of events for notification
	  EVENT              1      DB   Posting event (*)
	  CRITICAL_SUBSET    1      DB   Critical event subset identifier (*)
	  <reserved>         2      DB   <unused > (**)
	  NOTIFICATION_FLAG  4      DD   Event user notification flag (*)
	  STATION_ID         2      DW   Station ID
	  DLC_STATUS_CODE    2      DW   DLC status code
	  FRMR_DATA          5      DB   Five byte FRMR "reason code"
	  ACCESS_PRIORITY    1      DB   New access priority if status bit 5 is "on".
	  REMOTE_NODE        6      DB   6-byte remote node address
	  REMOTE_SAP         1      DB   Remote SAP address
	  <reserved>         1      DB   <unused>
	  USER_STAT_VALUE    2      DW   User value as defined in DLC.OPEN.SAP command
	
	(*)  Indicates a returned value  
	(**) In Windows NT DLC, there are 2 unused bytes resulting from the
	    use of a non-packed CCB2 structure
	
	Using the SNA Server Trace program (SNATRACE), it is possible to capture all DLC
	calls made by the 802.2 link service to the Windows NT DLC interface by enabling
	"Level 2" message tracing. If a DLC connection failure occurs, a DLC READ
	command will complete, and may appear as follows:
	
	  DLC   --------------------------------------------------
	  DLC   READ               OK
	  DLC   ---- DLC API control block at address 7c5e0----
	  DLC    00310000 00000000 00000000 FCC50700
	  DLC    D4000000 00000000 00002000
	  DLC
	  DLC    0004010C 08000000 01000000 01040040
	  DLC    00000000 00004201 02998122 04041FC0
	  DLC   --------------------------------------------------
	
	The first two lines correspond to the CCB2 structure passed in the DLC API
	control block, while the last two lines correspond to the CCB parameter table
	for the READ command. Using the structure definition above, the parameter table
	can be interpreted as follows:
	
	  0004 = station ID 
	  01   = option indicator
	  0C   = event set
	  08   = event
	  00   = critical subset
	  0000 = padding (unused)
	  01000000 = notification flag 
	  0104 = station ID (non-Intel format = 0401)
	  0040 = DLC status code (non-Intel format = 4000)
	  00000000 00 = FRMR data 
	  00   = access priority
	  42 01 02 99 81 22 04 = remote node address
	  04   = remote SAP
	  1F   = reserved
	  C0   = user status value
	
	Note that the DLC status code (DW = two byte "word" value) is stored in memory in
	Intel format, and needs to be "flipped" to show the real value as interpreted by
	the 802.2 link service.
	
	Using the DLC status code definitions below (as documented in Appendix B of the
	IBM LAN Technical Reference), a status code of 0x4000 is interpreted as
	follows:
	
	  0x4000 (hex) = 0100 0000 0000 0000 (binary)
	
	  Bit 14 on = DM or DISC received
	
	  DLC Status Codes
	  =================
	  BIT    Function                
	
	  15     Link lost
	  14     DM or DISC received
	  13     FRMR received  (See 5-byte FRMR data "reason code")
	  12     FRMR sent (See 5-byte FRMR data "reason code")
	  11     SABME received for an open link station
	  10     SABME received, link station opened
	  9      Remote station has entered "local busy" condition
	  8      Remote station has left a "local busy" condition
	  7      Ti has expired
	  6      DLC counter overflow (DLC.STATISTICS should be called)
	  5      Access priority lowered
	  4-1    reserved
	  0      Local station has entered a "local busy" condition
	
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300 kbSNAServ200 kbSNAServ211 kbSNAServ400 kbSNAServ210 kbSNAServ211SP1 kbSNAServ211SP2 kbSNAServ300SP3 kbSNAServ300SP1 kbSNAServ400SP1 kbSNAServ300SP2
	Version           : WINDOWS:2.0,2.1,2.11,2.11 SP1,2.11 SP2,3.0,3.0 SP1,3.0 SP2,3.0 SP3,4.0,4.0 SP1
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}