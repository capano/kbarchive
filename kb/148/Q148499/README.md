---
layout: page
title: "Q148499: Differences Between SLIP and PPP with Dial-Up Networking"
permalink: /kb/148/Q148499/
---

## Q148499: Differences Between SLIP and PPP with Dial-Up Networking

{% raw %}

	Article: Q148499
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 95
	Operating System(s): 
	Keyword(s): dun win95 kbDialUp
	Last Modified: 19-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	- Microsoft Plus! for Windows 95 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains information describing technical aspects and the usage of
	the SLIP and PPP line-control protocols with Dial-Up Networking.
	
	MORE INFORMATION
	================
	
	Microsoft's Windows 95 implementation of the SLIP and PPP protocols is based on
	the standards set forth by the Internet Engineering Task Force (IETF). These
	standards are contained in technical documents called Requests For Comments
	(RFC) and are widely available on the Internet. By adhering closely to these
	standards, connectivity to other SLIP or PPP servers similarly designed is
	virtually guaranteed.
	
	Brief outlines of the protocols themselves are provided below, with information
	pertinent to their operation with Windows 95 following.
	
	If more information on either protocol is required, the following RFCs are good
	sources of information:
	
	  RFC-1055: SLIP Implementation
	  RFC-1661: PPP Implementation
	  RFC-1700: Internet Assigned Numbers
	
	The following URL contains the RFC Index, which is constantly updated, and
	contains links to all the RFC documents:
	
	  http://ds.internic.net/ds/rfc-index.html
	
	Serial Line Internet Protocol - SLIP
	------------------------------------
	
	SLIP can be defined as an encapsulation method for transmitting IP packets over a
	serial connection. From its creation until the present time, the recommended
	method for implementing SLIP has remained a de facto standard.
	
	Specifications:
	
	Packet Framing:
	
	  Special Characters
	
	     END (C0h,192d) Signals the end of a packet's transmission.
	     ESC (DBh,219d) Special character used when characters
	                     duplicate the END character.
	
	  NOTE: If a data byte has the same value as the END character, a
	  two-byte sequence of ESC and DCh is sent instead. If a data
	  byte is the same as an ESC character, a two-byte sequence of ESC
	  and DDh is sent instead.
	
	Packet Size:
	
	  IP (headers and data) + transport protocol headers - framing
	  characters <= 1006 bytes
	
	Other Information:
	
	SLIP does not have the ability to transmit more than one network protocol at a
	time. Its architecture does not provide a method of differentiating between
	network protocols. TCP/IP is the protocol that is typically used with SLIP,
	which made it ideal for connecting a remote computer to the Internet using a
	dial-up SLIP server. However, because TCP/IP is the only network protocol SLIP
	can carry makes it of limited use in other applications.
	
	SLIP also provides no mechanisms for error correction. It relies on the hardware
	used to make the connection, and the error-correction capabilities of TCP/IP to
	determine if a packet's information is bad and needs to be resent.
	
	There are no compression algorithms built into SLIP. There are variants of SLIP
	(for example, CSLIP, or Compressed SLIP) that provide some degree of
	streamlining, but the majority of SLIP connections do not use compression.
	
	Point to Point Protocol - PPP
	-----------------------------
	
	PPP can be defined as an encapsulation method for transmitting multiple- protocol
	datagrams over point-to-point links. It is more robust and versatile than its
	predecessor, SLIP. PPP provides a data-link layer, the Link Control Protocol
	(LCP), for setting up, configuring, and monitoring the connection to ensure that
	the connection remains reliable. In addition, by using Network Control Protocols
	(NCPs), different network- layer protocols can be used dynamically.
	
	Specifications:
	
	Packet Framing:
	
	  Protocol Field (xxxxxxxx,yyyyyyyy)
	
	     The Protocol field is one or two octets, and its value
	     identifies the datagram encapsulated in the Information field
	     of the packet. The field is transmitted and received most-
	     significant-octet first.
	
	  Information Field (0 - n[xxxxxxxx])
	
	     The Information field is zero or more octets. The Information
	     field contains the datagram for the protocol specified in the
	     Protocol field. The maximum length for the Information field,
	     including padding, but not including the Protocol field, is
	     termed the Maximum Receive Unit (MRU), which defaults to 1500
	     octets. By negotiation, consenting PPP implementations may
	     use other values for the MRU.
	
	  Padding (0 - n[xxxxxxxx])
	
	     On transmission, the Information field may be padded with an
	     arbitrary number of octets up to the MRU.  It is the
	     responsibility of each protocol to distinguish padding octets
	     from real information.
	
	Link Negotiation:
	
	  Phase I
	
	     Each side exchanges LCP packets that test the integrity of
	     the link and configure the operational parameters the
	     connection will use at the data-link layer.
	
	  Phase II
	
	     Each side negotiates for and participates in user
	     authentication. This phase is only a suggestion to the
	     standard implementation of a point-to-point protocol, and as
	     such, may not be included in all implementations.
	
	  Phase III
	
	     Each side negotiates for the set of NCPs that will be used. For
	     each different type of datagram to be exchanged (IPX, IP, and so
	     on), an NCP must be configured and operational. This provides the
	     method for transmission of network-layer information.
	
	Other Information:
	
	The most important thing to remember about PPP is that it can support multiple
	network protocols simultaneously, or any individual protocol by itself. In
	addition, it provides error correction and compression of a very sophisticated
	nature. While it has more overhead and additional information, the compression
	and error control make PPP much faster than SLIP and far more reliable.
	
	Using SLIP and PPP with Windows 95
	----------------------------------
	
	Windows 95 automatically supports dialing into servers that allow PPP, RAS, or
	NRN (NetWare Connect) connections. SLIP support must be installed separately. If
	you are using the CD-ROM version of Windows 95, you can install SLIP support
	(along with scripting support) by following these steps:
	
	1. In Control Panel, double-click Add/Remove Programs.
	
	2. On the Windows Setup tab, click Have Disk.
	
	3. In the Copy Manufacturer's Files From box, enter the following line and then
	  click OK
	
	  <drive>:\admin\apptools\dscript
	
	  where <drive> is the CD-ROM drive containing the Windows 95 CD-ROM.
	
	4. Click OK.
	
	5. Click "SLIP and Scripting for Dial-Up Networking."
	
	6. Click Install.
	
	After you install SLIP support, SLIP and CSLIP are available as additional server
	types when you specify the type of server being dialed into.
	
	NOTE: If you do not have the CD-ROM version of Windows 95, see the following
	articles in the Microsoft Knowledge Base for information about obtaining SLIP
	support:
	
	  Q135315 CD-ROM Extras for Microsoft Windows 95 Upgrade
	
	  Q146238 Microsoft Windows 95 Service Pack 1 Admin.doc File (3 of 3)
	
	When you are using SLIP, you are limited to the use of the TCP/IP protocol. In
	addition, in the Dial-Up Networking connectoid, the Enable Software Compression
	and Require Encrypted Password options will not be available. These restrictions
	are limitations of the SLIP protocol, as noted previously.
	
	When you are using PPP, you can use the full flexibility of Dial-Up Networking.
	You can select NetBEUI, IPX/SPX, TCP/IP, or any combination thereof. The
	compression and password-encryption options are also available. However, if the
	dial-up server does not support either of these options, they will not be used.
	The use of these options is negotiated during the second phase of the PPP
	connection.
	
	With the addition of Microsoft Plus! for Windows 95, a computer running Windows
	95 can be used as a dial-up server. However, incoming SLIP connections are not
	supported, as Windows 95 is not designed to route TCP/IP packets. Incoming PPP
	connections using NetBEUI or IPX/SPX are supported, and offer the remote
	computer access to the host's resources. If the host computer is connected to a
	LAN, the remote computer can gain access to network resources, and even be
	validated by a Microsoft Windows NT or Novell NetWare server.
	
	For information about how to obtain RFC documents, please see the following
	article in the Microsoft Knowledge Base:
	
	  Q185262 How to Obtain Request for Comments Documents from the Internet
	
	Additional query words:
	
	======================================================================
	Keywords          : dun win95 kbDialUp 
	Technology        : kbWin95search kbGamesSearch kbPlusSearch kbZNotKeyword3 kbPlus95
	Version           : :95
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
