---
layout: page
title: "Q151818: HOWTO: Build a Setup Program Creating Multiple Groups/Icon"
permalink: /kb/151/Q151818/
---

## Q151818: HOWTO: Build a Setup Program Creating Multiple Groups/Icon

{% raw %}

	Article: Q151818
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:4.0,5.0
	Operating System(s): 
	Keyword(s): kbVBp400 kbVBp500 kbGrpDSVB kbDSupport
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	- Microsoft Visual Basic Professional Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	By default, the Visual Basic 4.0 Setup Wizard creates one program group using
	the project name, and one icon within the program group for the executable file
	generated by the project. This article shows how to create additional program
	groups and more than one icon within a group for any additional executable files
	you want to ship by customizing the Visual Basic Setup Toolkit's SETUP1.VBP
	project.
	
	MORE INFORMATION
	================
	
	The SETUP1.VBP project in the Visual Basic 4.0 Setup Toolkit has two functions
	defined in the SETUP1.BAS file, CreateOSProgramGroup() and CreateOSLink(), that
	allow you to add program groups and icons. By default, the Form_Load event of
	SETUP1.FRM calls these two functions to create only one program group and one
	program icon. More program groups and icons can be added by calling these two
	functions multiple times and specifying new group names and additional
	executable file names. After you rebuild the SETUP1.EXE file, the modified
	version will be used in subsequent Setup programs created by the Visual Basic
	Setup Wizard. The SETUP1.VBP project is located in \SETUPKIT\SETUP1 subdirectory
	of the main Visual Basic directory.
	
	NOTE: Customizing SETUP1.EXE will make it unusable for other projects.
	
	Step-by-Step Example
	--------------------
	
	1. Backup all files in \SETUPKIT\SETUP1 subdirectory of the main Visual Basic
	  directory. This directory is also mirrored on the product CD-ROM in the
	  VB\SETUPKIT\SETUP1 directory.
	
	2. Load SETUP1.VBP, and locate the Form_Load event of the SETUP1.FRM.
	
	3. In Form_Load event, look for the section with the following comments:
	
	        '
	        'Create program groups and icons (or links, i.e. shortcuts)
	        '
	
	4. Find the lines where CreateOSProgramGroup() and CreateOSLink() are called:
	
	        CreateOSProgramGroup frmSetup1, strGroupName, strGrpPath
	        CreateOSLink frmSetup1, gsDest.strAppDir & gstrAppExe, "", _
	        gstrAppName
	
	5. Comment out those lines.
	
	6. Before the line:
	
	        If fCreateGroup Then
	
	        set fCreateGroup and fAdditionalIcons to TRUE:
	
	        fCreateGroup = TRUE
	        fAdditionalIcons = TRUE
	
	7. Suppose this setup program will create one program group called MyGroup1 that
	  contains MyExe1.Exe and MyExe2.Exe, and another group called MyGroup2 that
	  contains MyExe3.Exe and MyExe4.Exe. Suppose that the destination directory
	  for each of the EXE files is $(APPPATH) [ASCII 150] the default. In the
	  places where CreateOSProgramGroup and CreateOSLink are originally called
	  (step 4), type in the following code:
	
	        CreateOSProgramGroup frmSetup1, "MyGroup1", "MyGroup1.GRP"
	        CreateOSLink frmSetup1, gsDest.strAppDir & "MyExe1.EXE", "",_
	        "MyExe1", TRUE
	        CreateOSLink frmSetup1, gsDest.strAppDir & "MyExe2.EXE", "",_
	        "MyExe2", TRUE
	
	        CreateOSProgramGroup frmSetup1, "MyGroup2", "MyGroup2.GRP"
	        CreateOSLink frmSetup1, gsDest.strAppDir & "MyExe3.EXE", "",_
	        "MyExe3", TRUE
	        CreateOSLink frmSetup1, gsDest.strAppDir & "MyExe4.EXE", "",_
	        "MyExe4", TRUE
	
	NOTE: Under Windows NT, a program remover icon is created at the last program
	group. For this example, the icon will be at MyGroup2.
	
	1. Build SETUP1.EXE.
	
	2. Use Setup Wizard to build the setup program. This setup program will create
	  two program groups, and each program group will contain two EXE files.
	
	3. Restore the original SETUP1.VBP files to the \SETUPKIT\SETUP1 subdirectory of
	  your main Visual Basic directory.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbVBp400 kbVBp500 kbGrpDSVB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVBA500 kbVB500 kbVB400Search kbVB400 kbVB16bitSearch
	Version           : WINDOWS:4.0,5.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}