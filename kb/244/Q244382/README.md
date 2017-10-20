---
layout: page
title: "Q244382: Windows NT 4.0 Security Account Manager Replication"
permalink: /kb/244/Q244382/
---

## Q244382: Windows NT 4.0 Security Account Manager Replication

{% raw %}

	Article: Q244382
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article provides in-depth information about Netlogon functionality as it
	pertains to Security Account Manager (SAM) replication.
	
	MORE INFORMATION
	================
	
	For each backup domain controller (BDC), the primary domain controller (PDC)
	records the serial number of the most recent change sent to that BDC, and then
	compares it with the serial number of the most recent change made to the SAM
	database. If this comparison shows that this BDC is up to date, the notification
	engine does not notify this BDC during this cycle. Also, the PDC may send a
	notification change to a BDC, but the BDC may not apply it because of a computer
	failure. However, the BDC makes a replication request to the PDC upon
	restarting, and this request includes the serial number of the most recent
	change successfully applied to the BDC. This information permits the PDC to keep
	the BDC up to date.
	
	A comparison of the serial numbers between the PDC and its BDCs is made at two
	different times:
	
	- By the notification engine, whenever it considers sending a "pulse" to a BDC.
	
	- By the replication engine, whenever it receives a request for changes from a
	  BDC.
	
	How the PDC Requests BDC Notifications
	--------------------------------------
	
	The notification engine enumerates the BDCs using the capabilities of the SAM,
	and considers BDCs for notification in whatever order the SAM presents them. The
	order is consistent each time the notification engine runs, and there is no way
	for an administrator to control this order.
	
	When a PDC starts, it reads the list of BDCs from the SAM, and then builds a
	circular list in memory. The SAM supplies the BDCs in reverse alphabetical
	order, and if a new BDC is added while the PDC is already running, this BDC
	appears in an unpredictable location in the circular list.
	
	How a BDC Synchronizes After Notification
	-----------------------------------------
	
	After a BDC receives a notification from the PDC, it requests changes from the
	PDC, including the serial number of the most recent change successfully applied
	to the BDC. Then, the PDC attempts to respond with more recent changes, and if
	the response does not fit into a single response, the PDC returns as much as it
	can, including a status indicating that the BDC should make another request.
	This process continues until the PDC is able to respond with the remaining
	changes.
	
	If a PDC is updated during a replication cycle, BDCs that finish their
	replication before the update do not see the new value until the following
	replication cycle, while BDCs that finish their replication after the update see
	the new value in the current cycle.
	
	How the PDC Controls Replication Concurrency
	--------------------------------------------
	
	The PDC Netlogon service contains a notification engine that notifies BDCs that
	they should perform replication. Each time the notification engine starts, it
	runs a complete cycle. In one cycle, the engine considers each BDC and either
	notifies them by sending a "pulse" message, or not. At the end of a cycle, the
	engine either stops and waits for the configured number of "pulse" seconds to
	have elapsed since the last time the engine started its cycle, or immediately
	starts a new cycle if the configured number of "pulse" seconds have already
	elapsed.
	
	The notification engine employs feedback to avoid overloading the PDC with
	replication requests from BDCs. The notification engine notifies BDCs in slots
	of size PulseConcurrency. For example, if the PulseConcurrency value is set 30,
	then 30 BDCs replicate with the PDC at a given time until all BDCs for this
	replication cycle are synchronized, in a sliding window format always containing
	30 BDCs. When one BDC has finished replication, a new one is taken from the
	list. After notifying such a slot, the PDC waits for all the BDCs in the slot to
	complete their replication before starting the next slot of notifications.
	
	Determining when a BDC is notified of a "pulse" event depends entirely on where
	the notification engine stopped at the end of the previous cycle. The
	notification engine considers stopping each time it examines a list entry and
	decides not to send a pulse. For example, if N is the number of "live" BDCs in
	the list, and the notification engine has just examined N "live" entries and not
	sent pulses to any of them, and it is not time to start a new cycle, the
	notification engine stops. Also, because BDCs may go up and down or become
	unresponsive, the stopping place is not predictable, and the first BDCs to get
	pulsed when the engine starts are not predictable.
	
	NOTE: The PDC responds to all BDC replication requests, not just replication
	requests from BDCs in its current slot. There are several scenarios in which a
	BDC outside the current slot may request replication from the PDC:
	
	- The PDC notifies a BDC, but that BDC does not respond with a replication
	  request within PulseTimeout1 seconds. The PDC then skips that BDC, and does
	  not include it in the current slot. However, that BDC really did receive the
	  notification, and eventually performs a replication request.
	
	- The PDC sends a replication response to a BDC, but the response does not
	  bring that BDC fully up to date, and that BDC does not come back with a
	  replication request within PulseTimeout2 seconds. The PDC then removes that
	  BDC from the current slot. However, that BDC really did receive the
	  replication response, and eventually performs a replication request.
	
	- A BDC failed, and then restarted. After restarting, the BDC makes a
	  replication request to the PDC.
	
	- An administrator has manually issued a replication request at a BDC.
	
	Additional information about this behavior is provided in the white paper "Domain
	Sizing and Capacity Planning for Windows NT Server 4.0", and the Microsoft
	Windows NT Resource Kit. Also, additional details can be gathered by installing
	a checked version of the Netlogon.dll file and examining the logs that are
	generated.
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Hardware          : ALPHA x86
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}