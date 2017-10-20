---
layout: page
title: "Q277783: Clicore.log Incorrectly Displays That Client Files Are Installed"
permalink: /kb/277/Q277783/
---

## Q277783: Clicore.log Incorrectly Displays That Client Files Are Installed

{% raw %}

	Article: Q277783
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0 SP2
	Operating System(s): 
	Keyword(s): kbClient kbsms200 kbUpgrade
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 2.0 SP2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article discusses the behavior of the Clicore.log file; in particular, its
	indication that files are repeatedly being installed each time a user logs on to
	the computer, when, in fact, this addition of files does not occur.
	
	MORE INFORMATION
	================
	
	In Microsoft Systems Management Server (SMS) version 2.0 Service Pack 2 (SP2),
	the behavior of the periodic verification cycle on SMS clients has changed. Now,
	instead of having to reinstall all client component files during the
	verification cycle or during a logon installation phase, only those files that
	have changed are copied to the client.
	
	The Clicore.log file, however, often indicates that files are repeatedly being
	installed each time a user logs on to a computer (when the SMS site has
	Microsoft Windows NT Logon Client Installation enabled). A user may be concerned
	that a significant amount of network traffic is being generated by the
	installation of these files.
	
	In fact, the message displayed in the Clicore.log file is misleading. Because of
	the changes in the SMS Installer (for SP2), the actual location where you must
	check for files that are being installed or bypassed (skipped) is in the
	Coreinst.log file located in the <WinDir>\Ms\Sms\Core\Bin\Coreinst.log
	folder. The display of the Coreinst.log file reveals that most (if not all) of
	the Clicore files are being bypassed (that is, if the correct versions are
	already present on the client).
	
	The following entry is an excerpt from the Clicore.log file during a logon
	installation process on an existing client:
	
	Installing C:\Winnt\Ms\Sms\Core\Bin\Clilog.dll
	Installing C:\Winnt\Ms\Sms\Core\Bin\Abnwcli.dll
	registering common Nal Dlls
	After Nal32 install, Rebootrequired flag setting is 0
	Installing NT Nal Dlls
	Installing C:\Winnt\Ms\Sms\Core\Bin\Falclin.dll
	
	The corresponding section from the Coreinst.log file for the same time period
	displays the following entry:
	
	Skipped File: C:\Winnt\Ms\Sms\Core\Bin\Clilog.dll
	Skipped File: C:\Winnt\Ms\Sms\Core\Bin\Abnwcli.dll
	Self-Register: C:\Winnt\Ms\Sms\Core\Bin\Abnwcli.dll
	Skipped File: C:\Winnt\Ms\Sms\Core\Bin\Falclin.dll
	Skipped File: C:\Winnt\Ms\Sms\Core\Bin\Mslmclin.dll
	Skipped File: C:\Winnt\Ms\Sms\Core\Bin\Bindclin.dll
	Skipped File: C:\Winnt\Ms\Sms\Core\Bin\Ndsclin.dll
	Self-Register: C:\Winnt\Ms\Sms\Core\Bin\Falclin.dll
	Self-Register: C:\Winnt\Ms\Sms\Core\Bin\Mslmclin.dll
	Self-Register: C:\Winnt\Ms\Sms\Core\Bin\Bindclin.dll
	Self-Register: C:\Winnt\Ms\Sms\Core\Bin\Ndsclin.dll
	Skipped File: C:\Winnt\Ms\Sms\Core\Bin\Cliex32.dll
	Skipped File: C:\Winnt\Ms\Sms\Core\Bin\Delpath.exe
	Skipped File: C:\Winnt\Ms\Sms\Core\Bin\Smsdiscv.dll
	Skipped File: C:\Winnt\Ms\Sms\Core\Bin\Discv_nd.dll
	Skipped File: C:\Winnt\Ms\Sms\Core\Bin\Nalcli.dll
	Skipped File: C:\Winnt\Ms\Sms\Core\Bin\Smscstat.dll
	Skipped File: C:\Winnt\Ms\Sms\Core\Bin\Cliver.exe
	
	For additional information about the client component periodic verification
	cycle, click the article number below to view the article in the Microsoft
	Knowledge Base:
	
	  Q239564 Client Components Reinstalled During Periodic Verification
	
	Additional query words: prodsms 30-day 30 days re-install verify
	
	======================================================================
	Keywords          : kbClient kbsms200 kbUpgrade 
	Technology        : kbSMSSearch kbSMS200SP2
	Version           : :2.0 SP2
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}