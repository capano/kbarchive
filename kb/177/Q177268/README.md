---
layout: page
title: "Q177268: XADM: Information Store Stops When Decoding Inbound TNEF Propert"
permalink: /kb/177/Q177268/
---

## Q177268: XADM: Information Store Stops When Decoding Inbound TNEF Propert

{% raw %}

	Article: Q177268
	Product(s): Microsoft Exchange
	Version(s): winnt:5.0,5.5
	Operating System(s): 
	Keyword(s): exc5 exc55
	Last Modified: 22-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.5, 5.0 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	The Microsoft Exchange Server information store may unexpectedly terminate with
	an access violation. If Windows NT Server and Microsoft Exchange Server symbols
	are installed and correct, the drwtsn32.log produced may look similar to the
	following:
	
	  State Dump for Thread Id 0xfd
	
	  eax=00000000 ebx=00000001 ecx=00000001 edx=011d1458 esi=8004010d
	edi=011d145c
	  eip=0050304a esp=06a0f550 ebp=06a0f658 iopl=0         nv up ei pl nz na
	pe nc
	  cs=001b  ss=0023  ds=0023  es=0023  fs=003b  gs=0000
	efl=00000202
	
	  function: CMDBMessage::HrSetRTFBodyTag
	          00503030 83f801           cmp     eax,0x1
	          00503033 8bf8             mov     edi,eax
	          00503035 1bc0             sbb     eax,eax
	          00503037 250e000780       and     eax,0x8007000e
	          0050303c 750e             jnz
	CMDBMessage::HrSetRTFBodyTag+0x4c (0050304c)
	          0050303e 8bcb             mov     ecx,ebx
	          00503040 c1e902           shr     ecx,0x2
	          00503043 f3a5            rep  movsd ds:8004010d=????????
	es:011d145c=011d1b98
	          00503045 8bcb             mov     ecx,ebx
	          00503047 83e103           and     ecx,0x3
	  FAULT ->0050304a f3a4             rep     movsb         ds:8004010d=??
	es:011d145c=98
	          0050304c 5f               pop     edi
	          0050304d 5e               pop     esi
	          0050304e 5b               pop     ebx
	          0050304f c20400           ret     0x4
	          00503052 cc               int     3
	          00503053 cc               int     3
	          00503054 cc               int     3
	          00503055 cc               int     3
	          00503056 cc               int     3
	          00503057 cc               int     3
	          00503058 cc               int     3
	
	  *----> Stack Back Trace <----*
	
	  FramePtr ReturnAd Param#1  Param#2  Param#3  Param#4  Function Name
	  06a0f558 00502d7b 8004010d 06a0f658 011d4e7c 011d49cc
	store!CMDBMessage::HrSetRTFBodyTag  (FPO: [1,0,3])
	  06a0f57c 00502ad1 06a0f59c 011d4e7c 000000c0 011d49cc
	store!CMAPIMessage::HrProcessPropSet  (FPO: [EBP 0x06a0f658] [2,3,4])
	  06a0f654 00502a0c 0000000c 011d4e7c 011d49fc 011dc05c
	store!CMAPIMessage::HrProcessInboundProps  (FPO: [EBP 0x000000c0] [2,47,4])
	  06a0f674 00502e06 011d49cc 0000000c 011dc05c 06a0f69c
	store!CMAPIMessage::SetProps  (FPO: [EBP 0x011d49fc] [4,1,4])
	  06a0f6c0 004f5725 00000000 0000000c 011dc05c 06a0f720 store!HrCommitLast
	(FPO: [EBP 0x011d49fc] [6,10,4])
	  06a0f738 004f50e3 ffffffff 00000000 00405058 00000000
	store!HrExtractProperties  (FPO: [EBP 0x00000000] [4,19,4])
	  06a0f75c 004fef0d 011d49fc 00000002 00405058 00000000
	store!TNEF_ExtractProps  (FPO: [EBP 0x011d1534] [4,0,4])
	  06a0f798 004e6601 011dd2b4 011d9eec 00000000 00405e08
	store!CmnBptMessage::hrExtractTNEF  (FPO: [EBP 0x077ddcc4] [2,6,4])
	  06a0f7bc 004d6cd3 011dd2b4 011d9eec 011ddb4c 00000000
	store!CmcvtrBptEnd::hrExtract  (FPO: [EBP 0x00000000] [5,2,4])
	  06a0f7ec 004e64b4 06a0f800 00000000 06a0f800 00000000
	store!CINETextr::hrExtract  (FPO: [EBP 0x06a0f830] [3,2,4])
	  06a0f800 004e6456 00000000 077d08ec 00405ec8 00000000
	store!CConvertStream::HrFlush  (FPO: [0,1,0])
	  06a0f830 004e62da 011c5e1c 00000000 00000000 077d08ec
	store!CConvertStream::Commit
	  06a0f84c 0047164b 011d7cdf 00000dfe 00000f29 011d7bb4
	store!CSTREAM::HrCommit  (FPO: [2,1,3])
	  06a0f874 00471515 00000dfe 011d7cdf 06a0f89c 00000001
	store!EcWriteStreamOp  (FPO: [EBP 0x00000f29] [4,3,4])
	  06a0f89c 0040f3eb 00000001 0000002e 00000001 06a0f948
	store!EcWriteStream  (FPO: [EBP 0x011e9a74] [3,1,4])
	  06a0f90c 0040ec1e 06a0f928 00001200 06a0f92c 06a0fb38 store!EcRpc  (FPO:
	[EBP 0x06a0f948] [2,20,4])
	  06a0f928 77e11841 001720b0 011d7bb4 00173f30 00001200 store!EcDoRpc
	(FPO: [4,1,3])
	  06a0f948 77e52265 0040ebe0 06a0fb3c 00000004 06a0fb50
	rpcrt4!WMSG_BINDING_HANDLE::AllocateCCall [omap] (FPO: Non-FPO [4,6,3])
	  06a0f964 77e52236 0040ebe0 06a0fb3c 00000004 ffffffff
	rpcrt4!DG_CASSOCIATION::`vftable' [omap]
	  06a0fc28 77e51f9e 00000000 00000000 06a0fe08 06a0fc40
	rpcrt4!DG_BINDING_HANDLE::`vftable' [omap]
	  06a0fc7c 77e11122 00410230 06a0fe08 06a0fdc4 00000000
	rpcrt4!TRANS_CCONNECTION::`vftable' [omap]
	  06a0fcd0 77e112fb 06a0fe08 00000000 06a0fdc4 00166d18
	rpcrt4!RPC_INTERFACE::DispatchToStubWorker [omap] (FPO: Non-FPO [3,14,3])
	  06a0fcf0 77e119cf 06a0fe08 00000000 06a0fdc4 06a0fe68
	rpcrt4!NdrClientInitializeNew [omap]
	
	  06a0fdc8 77e12b98 00143b60 06a0fe68 06a0fe08 06a0fe3c
	rpcrt4!WMSG_CASSOCIATION::FreeCCall [omap]  (FPO: [EBP 0x00000000] [1,0,4])
	  06a0fe40 77e15fff 00143b60 06a0fe68 00000000 00166c70
	rpcrt4!WMSG_ADDRESS::DealWithLRPCRequest [omap] (FPO: Non-FPO [4,19,3])
	  06a0ff90 77e162f0 77e163e5 0014b4e8 06a0ffec 00000000
	rpcrt4!RpcBindingFromStringBindingW [omap] (FPO: Non-FPO [2,2,3])
	
	CAUSE
	=====
	
	During decoding of an inbound SMTP message that includes TNEF content, a disk
	full condition is hit (MAPI_E_DISK_FULL. 0x8004010d), and the error code is
	passed to the information store through TNEF. The IMAIL wrapper in the
	information store does pre-processing of the TNEF properties and does not check
	for errors in them, so it encounters the error code and crashes.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.0. This problem has been corrected in the latest U.S. Service Pack for
	Microsoft Exchange Server version 5.0. For information on obtaining the Service
	Pack, query on the following word in the Microsoft Knowledge Base (without the
	spaces):
	
	  S E R V P A C K
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server version
	5.5. This problem has been corrected in the latest U.S. Service Pack for
	Microsoft Exchange Server version 5.5. For information on obtaining the Service
	Pack, query on the following word in the Microsoft Knowledge Base (without the
	spaces):
	
	  S E R V P A C K
	
	
	Additional query words: crash hang GPF general protection fault
	
	======================================================================
	Keywords          : exc5 exc55 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbZNotKeyword2
	Version           : winnt:5.0,5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
