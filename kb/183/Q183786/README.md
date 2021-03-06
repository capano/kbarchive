---
layout: page
title: "Q183786: TN3270 Server Keeps SNA Session Open When TN3270 Client Rebooted"
permalink: /kb/183/Q183786/
---

## Q183786: TN3270 Server Keeps SNA Session Open When TN3270 Client Rebooted

{% raw %}

	Article: Q183786
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:3.0,3.0 SP1,3.0 SP2,4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 02-APR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 3.0, 3.0 SP1, 3.0 SP2, 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, make sure you understand how to restore it if
	a problem occurs. For information about how to do this, view the "Restoring
	the Registry" Help topic in Regedit.exe or the "Restoring a Registry Key"
	Help topic in Regedt32.exe.
	
	SYMPTOMS
	========
	
	If a TN3270 client is not shut down gracefully (for example, powered off and on
	or restarted) while having an open session through the SNA Server TN3270
	Service, the TN3270 Server continues to keep the session open for 2 hours.
	
	If the TN3270 client is configured to open a specific TN3270 device (LUA LU),
	then the TN3270 client will receive the following error when attempting to open
	the session while the server operates as if it's still in use:
	
	  [TN3270-31] ERROR - Telnet device <devicename> in use.
	
	CAUSE
	=====
	
	The Windows NT TCP/IP driver does not report TCP/IP session errors until its
	default keep alive interval expires. This keep alive timeout defaults to 2
	hours. If a TN3270 client is powered off or restarted, the SNA Server TN3270
	Service is not notified until 2 hours elapse.
	
	RESOLUTION
	==========
	
	The TN3270 Service sets the SO_KEEPALIVE socket option, so it's possible to tune
	the following Windows NT TCP/IP values to control the time interval before the
	TN3270 Server is notified of a client outage. Tuning this parameter will affect
	Windows NT TCP/IP keepalive behavior for all TCP/IP socket applications that set
	the SO_KEEPALIVE socket option.
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall your operating system. Microsoft cannot guarantee that
	problems resulting from the incorrect use of Registry Editor can be solved. Use
	Registry Editor at your own risk.
	
	For information about how to edit the registry, view the "Changing Keys And
	Values" Help topic in Registry Editor (Regedit.exe) or the "Add and Delete
	Information in the Registry" and "Edit Registry Data" Help topics in
	Regedt32.exe. Note that you should back up the registry before you edit it. If
	you are running Windows NT, you should also update your Emergency Repair Disk
	(ERD).
	
	To change these parameters, perform the following procedure:
	
	1. Start Registry Editor (REGEDT32.EXE), and to the following subkey:
	
	HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services
	
	2. Add a value to the key described in the appropriate entry below, by Add Value
	  from the Edit menu, typing in the value, and using the "Data Type" check box
	  to set the value type.
	
	3. Click OK.
	
	4. Quit Registry Editor and restart the system for the changes to take effect.
	
	All of the TCP/IP parameters are registry values located under one of two
	different subkeys of HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services:
	
	- Tcpip\Parameters
	
	- <Adapter Name>\Parameters\Tcpip
	
	where <Adapter Name> refers to the subkey for a network adapter that TCP/IP
	is bound to, such as Lance01. Values under the latter key(s) are specific to
	each adapter. Parameters for which there may be both a DHCP and
	statically-configured value may or may not exist depending on whether the
	system/adapter is DHCP configured and/or static override values have been
	specified. A restart of the system is required for a change in any of these
	parameters to take effect.
	
	KeepAliveTime
	  Key: Tcpip\Parameters
	  Value Type: REG_DWORD - Time in milliseconds
	  Valid Range: 1 - 0xFFFFFFFF
	  Default: 7,200,000 (two hours)
	  Description: The parameter controls how often TCP attempts to verify
	  that an idle connection is still intact by sending a keep alive packet.
	  If the remote system is still reachable and functioning, it will
	  acknowledge the keep alive transmission. Keep alive packets are not sent
	  by default. This feature may be enabled on a connection by an
	  application.
	
	NOTE: The following KeepAliveInterval does not need to be changed, though it is
	provided below for reference purposes.
	
	KeepAliveInterval
	  Key: Tcpip\Parameters
	  Value Type: REG_DWORD - Time in milliseconds
	  Valid Range: 1 - 0xFFFFFFFF
	  Default: 1000 (one second)
	  Description: This parameter determines the interval separating keep
	  alive retransmissions until a response is received. After a response is
	  received, the delay until the next keep alive transmission is again
	  controlled by the value of KeepAliveTime. The connection will be aborted
	  after the number of retransmissions specified by
	  TcpMaxDataRetransmissions has gone unanswered.
	
	WORKAROUND
	==========
	
	The optimal solution is to modify the Windows NT TCP/IP driver's KeepAliveTime
	registry parameter where the SNA Server TN3270 Service is running, as described
	below, and then restart Windows NT.
	
	NOTE: The SNA Server TN3270 Service also has an "Idle Timeout" parameter that
	will automatically end a TN3270 client session that is idle for the timeout
	interval (which defaults to 120 minutes). However, this is a less optimal
	solution although this feature may be useful in some customer circumstances.
	
	MORE INFORMATION
	================
	
	The TN3270E specification (RFC 1647) section 13.3 suggests two possible methods
	for TN3270 client and server to implement the keepalive mechanism: the Telnet
	IAC NOP command, or the Telnet DO TIMING-MARK option. However, RFC 1647 does not
	require that any form of keep-alive mechanism be employed by either clients or
	servers. The SNA Server TN3270 Service chooses not to implement its own
	keep-alive mechanism, leaving it up to the administrator to tune the Windows NT
	TCP/IP KeepAliveTime as described above.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300 kbSNAServ400 kbSNAServ300SP1 kbSNAServ300SP2
	Version           : WINDOWS:3.0,3.0 SP1,3.0 SP2,4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
