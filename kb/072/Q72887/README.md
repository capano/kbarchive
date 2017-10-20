---
layout: page
title: "Q72887: FIX: Using a Higher Processor Directive in a Macro Causes A2006"
permalink: /kb/072/Q72887/
---

## Q72887: FIX: Using a Higher Processor Directive in a Macro Causes A2006

{% raw %}

	Article: Q72887
	Product(s): Microsoft Macro Assembler
	Version(s): MS-DOS:6.0,6.0a,6.0b
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Macro Assembler (MASM), versions 6.0, 6.0a, 6.0b 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to use a symbol in your assembly code without defining it
	first, the Microsoft Macro Assembler (MASM) generates the following error:
	
	  error A2006: undefined symbol : 'identifier'
	
	However, MASM may also incorrectly generate this error when you use a processor
	directive in a macro if the processor specified is higher than the one currently
	defined.
	
	RESOLUTION
	==========
	
	To work around the problem, declare a processor type of sufficient level to
	execute the instructions in the macro before calling the macro. The comment in
	the sample code below demonstrates this by declaring the .286 directive before
	the macro is called.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in MASM versions 6.0, 6.0a, and
	6.0b. This problem was corrected in MASM for MS-DOS version 6.1.
	
	MORE INFORMATION
	================
	
	The sample code below may be used to illustrate this problem. The default
	processor directive is .8086. When the macro is called, a LEAVE instruction is
	used that requires the .286 processor. However, with the .286 directive in the
	macro definition, the following error is generated by the assembler:
	
	  file.asm(14): error A2006: undefined symbol : s my_proc(2): Macro Called From
	  file.asm(14): Main Line Code
	
	Sample Code
	-----------
	
	  ;Assemble options needed: /c
	
	  .MODEL small
	  .8086
	  ;.286    ;Uncomment this directive for workaround.
	
	  my_proc MACRO  s
	     .286
	     enter s, 0
	     .8086
	  ENDM
	
	  .STACK 4096
	
	  .CODE
	  start:
	     my_proc 5
	     mov ax, 4C00h
	     int 21h
	  END start
	
	Additional query words: 6.00 6.00a 6.00b buglist6.00 buglist6.00a buglist6.00b fixlist6.10
	
	======================================================================
	Keywords          :  
	Technology        : kbMASMsearch kbAudDeveloper kbMASM600 kbMASM600a kbMASM600b
	Version           : MS-DOS:6.0,6.0a,6.0b
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}