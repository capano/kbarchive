---
layout: page
title: "Q123791: SNA Server Remote Station Discovery Process"
permalink: /kb/123/Q123791/
---

## Q123791: SNA Server Remote Station Discovery Process

{% raw %}

	Article: Q123791
	Product(s): Microsoft SNA Server
	Version(s): 2.0,2.1,2.11,2.11 SP1,2.11 SP2,3.0,3.0 SP1,3.0 SP2,3.0 SP3,4.0,4.0 SP1
	Operating System(s): 
	Keyword(s): kbnetwork kbsna211sp1 kbsna211sp2 kbsna300sp1 kbsna300sp2 kbsna300sp3 sna4 kbsna400sp1
	Last Modified: 06-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.0, 2.1, 2.11, 2.11 SP1, 2.11 SP2, 3.0, 3.0 SP1, 3.0 SP2, 3.0 SP3, 4.0, 4.0 SP1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When SNA Server starts an 802.2 connection, it submits, by default, an unlimited
	number of Open(Link) requests to the 802.2 link service. If an SNA Server 802.2
	connection is configured to activate OnServer Startup or By Administrator, the
	server will try indefinitely to activate the connection.
	
	The DLC protocol then sends logical link control (LLC) test frames to test link
	station-to-link station connectivity. These test frames are the first frames
	that are sent by SNA Server (through DLC) and are used to discover the remote
	station. To ensure the best chance of remote station discovery, the DLC protocol
	then submits various types of MAC level frames to the NDIS (Network Device
	Interface Specification) interface. The types submitted depend on the media
	access method DLC is bound to.
	
	THE SNA SERVER LINK LEVEL OPEN(LINK) REQUEST
	--------------------------------------------
	
	SNA Server's link level requests can be adjusted in SNA Server Admin/Manager by
	choosing the Retry Timers button in the Connection Properties dialog box.
	
	The two values are:
	
	- Maximum number of attempts
	
	  This value represents the number of link level Open (link) requests made by
	  the SNA Server service to the SNA Server 802.2 link service. It does not
	  represent the number of test frames that will be submitted by the DLC
	  protocol to NDIS. The valid range is from 1 to No Limit; the default is No
	  Limit.
	
	- Delay after failed attempts
	
	  This value represents the number of seconds that the SNA Server service will
	  wait after a failed attempt before submitting another request 802.2 link
	  service. The valid range is from 5 seconds through 255 seconds (in multiples
	  of 5); the default is 10 seconds.
	
	DLC MAC level Framing
	---------------------
	
	Ethernet:
	
	On Ethernet there are two frame formats: IEEE 802.3 and the older DIX (Digital
	Intel Xerox). With DIX format, SNAP message headers are used to identify the
	protocol as DLC because various other MAC level protocols can flow on Ethernet
	such as TCP/IP, NetBEUI, IPX, and so forth.
	
	SNA Server tells the DLC stack which sort of framing to use:
	
	  HKEY_LOCAL_MACHINE\SYSTEM
	  CurrentControlSet\Services\DLCLinkServiceName\Parameters\ExtraParameters
	  Frametype:REG_DWORD:number
	
	This specifies the type of frames for DLC to send over an Ethernet local area
	network (LAN). The variable need be set only if the LAN is Ethernet and only if
	the SNA server communicates with remote host, peer, or downstream systems via
	routers (not MAC layer bridges). If the SNA server communicates over Ethernet
	via routers, check with the local network support staff to determine what types
	of frames the routers pass. The frames can be either standard 802.3 format or
	802.2 packets prefixed by DIX headers using EtherType value 0x80D5.
	
	Specify the number in FrameType as follows:
	
	Value   Effect
	-----------------------------------------------------------------------
	
	 0     Use the frame type specified for this adapter in the
	       registry entry for the DLC protocol stack:
	
	          HKEY_LOCAL_MACHINE\SYSTEM
	          \CurrentControlSet\Services\DLC\Parameters\AdapterName
	            \UseDixOverEthernet
	
	       The default for UseDixOverEthernet is 0, resulting in 802.3
	       format.
	
	 1     Use the frame type automatically determined by the DLC stack
	       during XID exchange.
	
	 2     Use standard 802.3 format.
	
	 3     Use 802.2 packets prefixed by DIX headers using EtherType value
	       0x80D5.
	
	If FrameType is not set it defaults to 0.
	
	When you run DLC applications on Ethernet LANs, where the DLC traffic may need to
	pass over an Ethernet-Token Ring bridge (such as IBM 8209), the destination
	adapter address may need to be sent in bit-flipped order to accommodate the
	address change that such a bridge performs.
	
	SNA Server handles this by sending TEST and XID frames to both the configured
	remote network address and the bit-flipped address (for Ethernet 802.2
	connections), in both DIX and 802.3 formats.
	
	Some stations may send bits in little-endian order (least significant bit first),
	while others send them big-endian (most significant bit first). As a result,
	some remote stations won't recognize their own addresses unless the local
	station reverses the order of bits in the MAC address on every frame. One common
	problem occurs when an older LAN bridge flips the bits as the frames pass
	through it. As a result, remote systems do not recognize their own address, even
	when the sending and receiving stations are using the same bit ordering. Because
	of this, DLC sends both bit flipped and non- bit flipped frames to ensure that
	the remote system recognizes its address even when passing through one of these
	bridges.
	
	In summary, on each connection, the originating station starts an 802.2 session
	by sending an LLC TEST frame. By default, DLC sends this frame using both 802.3
	and DIX framing with both bit orderings of the MAC header. This can create as
	many as four TEST frames on the wire per request from the SNA Server 802.2 link
	service. The answering station's LAN adapter is only listening to one bit
	ordering of its MAC address, but it may be enabled for both 802.3 and DIX
	framing; the receiving station responds with either one or, at most, two TEST
	frames - one for each framing. The bit ordering is now established. DLC at the
	originating station hears both responses, and chooses one for the 802.2
	session.
	
	Token Ring:
	
	On token ring LANs, there is only one framing format, as specified by IEEE
	standard 802.5. Bit-flipping is not necessary.
	
	In Windows NT 3.1, DLC's automatic frame type detection did not work correctly;
	it could not establish a session with DIX framing, though it could via 802.3.
	
	In Windows NT 3.5, a filtering algorithm was added to avoid unnecessary
	duplication of the initial messages. This filtering avoids handing the client
	software (SNA Server) a duplicate message received with both framing formats.
	This cuts down on the superfluous messages exchanged during XID negotiation.
	
	To Bit-flip:
	
	1. Separate the 12-digit hexadecimal address into a set of two digits; for
	  example:
	
	  40 00 0A 12 34 56
	
	2. Reverse the positions of the characters in each of the two-digit sets:
	
	  40 00 0A 12 34 56  ->   04 00 A0 21 43 65
	
	3. Use the table below to bit-reverse each digit. For example:
	
	     04 00 A0 21 43 65  ->   02 00 50 48 2C 6A
	
	  Conversion Table
	  ----------------
	  Original  Converted
	  Bit       Bit
	  --------  ---------
	  0          0
	  1          8
	  2          4
	  3          C
	  4          2
	  5          A
	  6          6
	  7          E
	  8          1
	  9          9
	  A          5
	  B          D
	  C          3
	  D          B
	  E          7
	  F          F
	
	4. After bit-reversing each digit, combine the six pairs into a 12-digit
	  hexadecimal address. For example:
	
	     020050482C6A
	
	Additional query words: ntprotocol prodsna
	
	======================================================================
	Keywords          : kbnetwork kbsna211sp1 kbsna211sp2 kbsna300sp1 kbsna300sp2 kbsna300sp3 sna4 kbsna400sp1 
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300 kbSNAServ200 kbSNAServ211 kbSNAServ400 kbSNAServ210 kbSNAServ211SP1 kbSNAServ211SP2 kbSNAServ300SP3 kbSNAServ300SP1 kbSNAServ400SP1 kbSNAServ300SP2
	Version           : :2.0,2.1,2.11,2.11 SP1,2.11 SP2,3.0,3.0 SP1,3.0 SP2,3.0 SP3,4.0,4.0 SP1
	
	=============================================================================
	

{% endraw %}
