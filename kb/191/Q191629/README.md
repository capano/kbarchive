---
layout: page
title: "Q191629: HOWTO: Create an MTS Component that Works with FoxIsapi"
permalink: /kb/191/Q191629/
---

## Q191629: HOWTO: Create an MTS Component that Works with FoxIsapi

{% raw %}

	Article: Q191629
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 13-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Visual FoxPro 6.0 contains many server improvements including those that allow
	better integration with Microsoft Transaction Server (MTS). There may be
	situations where you want to use an MTS component with FoxIsapi.
	
	MORE INFORMATION
	================
	
	FoxIsapi is an Internet Server Application Programming Interface (ISAPI)
	extension that allows for Visual FoxPro (VFP) servers to be used with Internet
	Information Server to generate server-side HTML Web pages. The URL includes the
	VFP server, which is instantiated, and the associated method to be invoked. The
	method returns HTML to be rendered by the Web browser.
	
	There are no specific requirements for VFP servers used with FoxIsapi, however,
	best results are often obtained with use of Local EXE servers since it is easier
	to protect global data. The FoxIsapi sample uses a form so that it can obtain a
	private data session.
	
	One of the benefits of FoxIsapi is its built-in Pool Manager, which lets you
	manage multiple running servers pooled together for maximum scalability. One can
	efficiently use FoxIsapi to handle Web sites that need to respond to hundreds of
	thousands of Web hits a day.
	
	With all the nice features offered by MTS, one could easily use MTS along with
	FoxIsapi. While the improved scalability offered by MTS would not necessarily be
	taken advantage because of the FoxIsapi architecture, the Pool Manager support
	may provide an even better alternative. One of the nice advantages of using MTS
	is its automatic security and transaction support. These are reasons to consider
	using MTS with FoxIsapi. Remember, MTS components must be In-Process DLLs
	(marked as Multi-Use). One should not need to perform any other special tasks in
	order to get these servers to work under FoxIsapi. In addition, one can call
	other MTS servers directly within your FoxIsapi servers since these all exist
	within same MTS activity.
	
	The Pool Manager controls how servers scale, and how many instances can run
	simultaneously. Make sure you test various Pool Manager scenarios to get optimal
	results. You can also setup load balancing across multiple computers to make
	further scalability improvements. Strategies such as DNS Round Robin schemas are
	options to consider for load balancing.
	
	REFERENCES
	==========
	
	Microsoft Transaction Server Help; search on: "COM Components"
	
	Additional query words: PGFest600 kbVFp600 kbISAPI kbMTS
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbVFP600
	Version           : WINDOWS:6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}