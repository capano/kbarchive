---
layout: page
title: "Q176643: HOWTO: Find Multiple Occurrences of a String in a RichTextBox"
permalink: /kb/176/Q176643/
---

## Q176643: HOWTO: Find Multiple Occurrences of a String in a RichTextBox

{% raw %}

	Article: Q176643
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): KbVBA kbVBp kbVBp500 kbVBp600 kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Finding a single occurrence of a text string in a RichTextBox is fairly
	straightforward. The Instr() function was designed for this. In order to find
	multiple occurrences of a block of text, however, you need to write a routine
	that will call the Instr() function as many times as necessary to search the
	entire block of text for the desired string, while progressively moving the
	starting point of the search forward to avoid finding the same occurrence
	multiple times.
	
	You can accomplish this by using a recursive routine, which calls itself from
	within its own code. If you are not careful, however, recursion can cause
	problems, such as infinite loops and stack faults. But recursion does allow for
	elegant solutions to otherwise difficult situations.
	
	This article illustrates recursion by example. The FindIt() routine calls itself
	recursively as long as the return value of the Instr() function does not equal
	zero. If this value is non-zero, it means Instr() found another occurrence of
	the string it was looking for. If the value is zero, either the string is not
	contained in the block of text being searched or all occurrences of the string
	have already been found. Checking this value each time the routine runs prevents
	an endless loop.
	
	MORE INFORMATION
	================
	
	The following steps create a working example of finding multiple occurrences of
	the same string within a larger block of text.
	
	Step-by-Step Example
	--------------------
	
	1. Start a new Visual Basic Standard EXE project. Form1 is created by default.
	
	2. Resize the form to be as large as possible, and add a RichTextBox and a
	  CommandButton to the form.
	
	3. Make the RichTextBox as large as possible and set its Scrollbars property to
	  3-rtfBoth.
	
	4. Add the following code to the form:
	
	       Private Sub Form_Load()
	
	           'Edit the following line to point to your license.txt or another
	           'text file
	
	           RichTextBox1.LoadFile "license.txt"
	
	        End Sub
	
	        Private Sub Command1_Click()
	
	        Dim strval As String    'Inputbox returns a string
	        Dim nStrings As Long
	
	           'Reload the file to undo the previous selections
	           'Edit the following line to point to your license.txt or another
	           'text file
	
	           RichTextBox1.LoadFile "license.txt"
	
	           'Ask the user what string to find. Defaults to finding all
	           'occurrences of the word "the." In this example, you are
	           'concatenating spaces onto each end of the search string to
	           'prevent the FindIt routine from finding occurrences of the
	           'search string within other words, ie; finding "the" in "there"
	           'or "these." If you want to find the string within other strings,
	           'simply eliminate the concatenation.
	
	           strval = " " & InputBox("Enter the string to find.", "Findit", _
	              "the") & " "
	
	           If strval <> "" Then
	
	           'the user didn't click cancel call the FindIt routine
	           'and pass it the
	
	              nStrings = FindIt(RichTextBox1, strval)
	              MsgBox (Str$(nStrings) & " instances found.")
	           End If
	
	        End Sub
	
	        '********************************************************************
	        'Findit takes three arguments; two required, and one optional. The
	        'required arguments, Box and Srch, are a RichTextBox object and a
	        'string to search for. The optional argument, Start, is a Long
	        'integer that is used in the recursive calls.
	        '********************************************************************
	
	        Private Function FindIt(Box As RichTextBox, Srch As String, _
	           Optional Start As Long)
	
	        Dim retval As Long      'Instr returns a long
	        Dim Source As String    'variable used in Instr
	
	           Source = Box.Text   'put the text to search into the variable
	
	           If Start = 0 Then Start = 1 'the initial call doesn't pass a value
	                                       'for Start, so it will equal 0
	
	              retval = InStr(Start, Source, Srch) 'do the first search,
	                                                  'starting at the beginning
	                                                  'of the text
	
	              If retval <> 0 Then  'there is at least one more occurrence of
	                                   'the string
	
	              'the RichTextBox doesn't support multiple active selections, so
	              'this section marks the occurrences of the search string by
	              'making them Bold and Red
	
	                 With Box
	                    .SelStart = retval - 1
	                    .SelLength = Len(Srch)
	                    .SelColor = vbRed
	                    .SelBold = True
	                    .SelLength = 0          'this line removes the selection
	                                            'highlight
	                 End With
	
	                 Start = retval + Len(Srch) 'move the starting point past the
	                                            'first occurrence
	
	                 'FindIt calls itself with new arguments
	                 'this is what makes it Recursive
	                 FindIt = 1 + FindIt(Box, Srch, Start)
	              End If
	        End Function
	
	5. Run the project and click the CommandButton. You can accept the default of
	  searching for occurrences of the word "the" or enter your own string to
	  search for. Remember to include a space before and after short words to
	  prevent FindIt() from finding your search string in the middle of a longer
	  word.
	
	Additional query words: Recursive Recursion Multiple Selection Richtextbox RTF KBCONTROL
	
	======================================================================
	Keywords          : KbVBA kbVBp kbVBp500 kbVBp600 kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600 kbVB400Search kbVB400 kbVB16bitSearch
	Version           : WINDOWS:4.0,5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
