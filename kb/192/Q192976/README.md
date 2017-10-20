---
layout: page
title: "Q192976: PRB: VFP 6.0 Application Requires FoxFont In Fonts Directory"
permalink: /kb/192/Q192976/
---

## Q192976: PRB: VFP 6.0 Application Requires FoxFont In Fonts Directory

{% raw %}

	Article: Q192976
	Product(s): Microsoft FoxPro
	Version(s): 6.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 04-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you install a run-time application that uses the FoxFont font, the install
	places the FoxFont.fon file in the directory with your application's executable
	file. When you run the executable, it does not use FoxFont, instead it
	substitutes another font, such as Courier New.
	
	CAUSE
	=====
	
	Visual FoxPro 6.0 run-time applications no longer use the FoxFont when it is in
	the application directory. In order to use the FoxFont, it must be installed in
	the Fonts directory.
	
	RESOLUTION
	==========
	
	Place a copy of the FoxFont.fon font file in the Windows\Fonts directory. You
	can do this automatically by distributing the FoxFont.fon with your application
	and adding the following code to the initialization code of your application.
	This copies the font to the Windows/Fonts directory if it does not yet exist
	there. You would need to place this code before any other objects or code that
	use FoxFont, such as forms, reports, _SCREEN.FONTNAME="foxfont" commands, and so
	forth.
	
	Sample Code
	-----------
	
	     LOCAL lcAppDir, lcWinFontDir
	
	     * Get current App directory from SYS(16).
	     lcAppDir = SUBSTR(SYS(16), 1, RAT('\',SYS(16),1)-1)
	
	     * Get WinDir environment and find the Fonts directory.
	     lcWinFontDir = GETENV('windir')+'\Fonts'
	
	     * Check that FoxFon.fon is in App directory and not in Fonts directory.
	     IF FILE(lcAppDir+'\foxfont.fon') AND !FILE(lcWinFontDir+'\foxfont.fon')
	        * Copy the file
	        COPY file (lcAppDir+'\foxfont.fon') ;
	           TO (lcWinFontDir+'\foxfont.fon')
	        SET MESSAGE TO    && Clears "<nnnnn> bytes copied" from status bar
	        WAIT "" TIME 2    && Pause to allow font to be loaded
	     ENDIF
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a new project called Fonttest and add a program named Main with the
	  following contents:
	
	        * This uses CREATE OBJECT and a form class, but the same steps
	        * work with a form created with DO FORM.
	
	        oform1=CREATEOBJECT("form1")
	        oform1.Show
	        READ events
	
	        DEFINE CLASS form1 AS form
	           Height = 169
	           Width = 309
	           AutoCenter = .T.
	           Caption = "Font Test Form"
	           Name = "Form1"
	
	        ADD OBJECT command1 AS commandbutton WITH ;
	           Top = 108, ;
	           Left = 108, ;
	           Height = 27, ;
	           Width = 84, ;
	           Cancel = .T., ;
	           Caption = "E\<xit", ;
	           TabIndex = 2, ;
	           Name = "Command1"
	
	        ADD OBJECT text1 AS textbox WITH ;
	           FontName = "FoxFont", ;
	           FontSize = 9, ;
	           Value = (chr(227)), ;
	           Height = 25, ;
	           Left = 84, ;
	           Top = 36, ;
	           Width = 144, ;
	           Name = "Text1"
	
	        PROCEDURE Destroy
	           Clear events
	        ENDPROC
	
	        PROCEDURE command1.Click
	           Release thisform
	        ENDPROC
	
	        ENDDEFINE
	
	2. Build the project into an executable file.
	
	3. Place the executable from Step 2 and the Foxfont.fon from your Visual FoxPro
	  6.0 home directory in a separate directory. The Visual FoxPro home directory
	  can be determined by issuing the following command in the Command window:
	
	  " ?HOME() " (without the quotation marks)
	
	4. Run the .exe file. When the form appears, the text box contains a lower case
	  a with two dots over it, or some other character. The FoxFont character for
	  CHR(227) is the symbol for pi, and this is what would appear if FoxFont were
	  being used.
	
	Demonstration of Workaround
	---------------------------
	
	1. Paste the code listed in the RESOLUTION section into the Main program created
	  in Step 1 of the Steps to Reproduce Behavior section. Insert the code at the
	  beginning of the program, before the CREATEOBJECT command.
	
	2. Repeat steps 2-4 in the Steps to Reproduce Behavior section. This time, the
	  symbol for pi appears in the text box.
	
	Previous versions of FoxPro for Windows and Visual FoxPro for Windows allowed
	run-time applications to find and use the FoxFont if it was located in the
	application directory. However, Visual FoxPro 6.0 requires any font used by a
	run-time application to be in the Windows\Fonts directory.
	
	Windows 9x and Windows NT each store font files in a subdirectory of the Windows
	directory called Fonts. Any font files in this directory are available for use
	by applications. Windows 9x installs, by default, to the C:\Windows directory,
	and Windows NT installs, by default, to a directory called C:\WINNT.
	Additionally, you have the option to specify the directory where Windows will be
	installed during Windows Setup. The preceding code retrieves the Windows
	directory name using the WINDIR environment variable. This makes the code
	generic, so it works properly regardless of the Windows directory name, or
	whether the operating system is Windows 9x or Windows NT.
	
	REFERENCES
	==========
	
	For more information on True Type fonts, please refer to the following article
	in the Microsoft Knowledge Base:
	
	  Q186722 HOWTO: Programmatically Install a True Type Font
	
	(c) Microsoft Corporation 1998, All Rights Reserved. Contributions by Jim
	Saunders, Microsoft Corporation.
	
	
	Additional query words: kbAppSetup kbVFp600
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbVFP600
	Version           : :6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}