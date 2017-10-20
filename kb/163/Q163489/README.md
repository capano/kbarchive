---
layout: page
title: "Q163489: WD97: &quot;For Each...Next&quot; Loop Gives Wrong Result with Endnotes"
permalink: /kb/163/Q163489/
---

## Q163489: WD97: &quot;For Each...Next&quot; Loop Gives Wrong Result with Endnotes

{% raw %}

	Article: Q163489
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbmacroexample word8 kbwordvba word97
	Last Modified: 13-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	Using the "For Each...Next" loop in a Visual Basic for Applications macro to
	return footnotes, endnotes, or comments for a designated paragraph returns all
	footnotes, endnotes, or comments in the document.
	
	WORKAROUND
	==========
	
	Microsoft provides programming examples for illustration only, without warranty
	either expressed or implied, including, but not limited to, the implied
	warranties of merchantability and/or fitness for a particular purpose. This
	article assumes that you are familiar with the programming language being
	demonstrated and the tools used to create and debug procedures. Microsoft
	support professionals can help explain the functionality of a particular
	procedure, but they will not modify these examples to provide added
	functionality or construct procedures to meet your specific needs. If you have
	limited programming experience, you may want to contact a Microsoft Certified
	Partner or the Microsoft fee-based consulting line at (800) 936-5200. For more
	information about Microsoft Certified Partners, please visit the following
	Microsoft Web site:
	
	  http://www.microsoft.com/partner/referral/
	
	For more information about the support options that are available and about how
	to contact Microsoft, visit the following Microsoft Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	Use a "For...Next" loop with the Footnotes, Endnotes, or Comments collection
	instead of the "For Each...Next" loop.
	
	The following Visual Basic for Applications macro example uses a "For...Next"
	loop to extract the endnotes for a specified paragraph.
	
	     Sub ReturnNotesInParagraph()
	        Dim iCount As Integer
	        Dim oNote As Object
	        Dim iParaNum As Integer
	        ' Set the paragraph to return notes
	        iParaNum = 1
	        ' Note: If the specified paragraph does not exist
	        ' in the active document, an error will occur.
	        If ActiveDocument.Paragraphs.Count >= iParaNum Then
	           Set oNote = ActiveDocument.Paragraphs(iParaNum).Range.Endnotes
	           For iCount = 1 To oNote.Count
	              MsgBox oNote(iCount).Range.Text
	           Next
	        Else
	           MsgBox "The specified paragraph does not exist."
	        End If
	     End Sub
	
	STATUS
	======
	
	Microsoft is researching this problem and will post new information here in the
	Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q173707 OFF97: How to Run Sample Code from Knowledge Base Articles
	
	
	REFERENCES
	==========
	
	For more information about getting help with Visual Basic for Applications,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q163435 VBA: Programming Resources for Visual Basic for Applications
	
	Additional query words: wordcon vb vbe vba
	
	======================================================================
	Keywords          : kbmacroexample word8 kbwordvba word97 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}