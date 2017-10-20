---
layout: page
title: "Q43090: BC.EXE Command-Line Options for QuickBASIC and BASIC Compiler"
permalink: /kb/043/Q43090/
---

## Q43090: BC.EXE Command-Line Options for QuickBASIC and BASIC Compiler

{% raw %}

	Article: Q43090
	Product(s): See article
	Version(s): 4.00 4.00b 4.50
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | SR# S890329-57 B_BasicCom | mspl13_basic
	Last Modified: 20-DEC-1989
	
	This article documents the BC.EXE command-line options available in
	QuickBASIC Versions 4.00, 4.00b, and 4.50 and in Microsoft BASIC
	Compiler Versions 6.00 and 6.00b (with the exception of the /t option
	which is not available in QuickBASIC 4.00).
	
	These BC.EXE command-line options can also be found in the following
	manuals:
	
	1. Pages 210 and 211 of the "Microsoft QuickBASIC 4.0: Learning and
	   Using" manual for QuickBASIC 4.00 and 4.00b
	
	2. Pages 210 and 211 of the "Microsoft BASIC Compiler 6.0: Learning
	   and Using Microsoft QuickBASIC" manual, and additional options on
	   Pages 6, 7, 8 of the "Microsoft BASIC Compiler 6.0: User's Guide"
	   for 6.00 and 6.00b
	
	3. Pages 353 to 355 of the "Microsoft QuickBASIC 4.5: Programming in
	   BASIC" manual for QuickBASIC Version 4.50.
	
	Option  Definition
	------  ----------
	
	/a      Creates a listing of the disassembled object code for each
	        source line and shows the assembly-language code generated by
	        the compiler.
	
	/ah     Allows dynamic arrays of records, fixed-length strings, and
	        numeric data to occupy all of available memory. If this option
	        is not specified, the maximum size is 64K per array. Note that
	        this option has no effect on the way data items are passed to
	        procedures. (See also the REM $DYNAMIC metacommand.)
	
	/c:<n>  Sets the size (<n> = bytes) of the buffer receiving remote
	        data using an asynchronous communications adapter for each
	        communications port. (The transmission buffer is allocated 128
	        bytes for each communications port and cannot be changed on
	        the BC command line.)  This option has no effect if the
	        asynchronous communications card is not present. The default
	        buffer size is 256 bytes total for BOTH ports; the maximum
	        size is 32,767 bytes. The default, /c:512, is automatically
	        added when invoking the Make EXE File command from the Run
	        menu in QuickBASIC 4.00b and 4.50 (not in QuickBASIC 4.00).
	
	/d      Generates debugging code for run-time error checking and
	        enables CTRL+BREAK. This option is the same as the Produce
	        Debug Code option from the Run menu's Make EXE File command
	        within the environment.
	
	/e      Indicates the presence of ON ERROR with RESUME linenumber
	        statements. (See also the discussion of the /x option in this
	        list.)
	
	/mbf    Causes the QuickBASIC conversion functions to treat
	        IEEE-format numbers as Microsoft Binary format numbers. The
	        intrinsic functions MKS$, MKD$, CVS, and CVD are converted to
	        MKSMBF$, MKDMBF$, and CVSMBF, and CVDMBF, respectively. See
	        the "Microsoft QuickBASIC 4.0: BASIC Language Reference"
	        manual or corresponding help for more information about these
	        functions.
	
	/o      Substitutes the appropriate BCOMxx.LIB stand-alone program
	        library for the BRUNxx.LIB run-time module library.
	
	/r      Stores arrays in row-major order. BASIC normally stores arrays
	        in column-major order. This option is useful if you are using
	        other language routines that store arrays in row order.
	
	/s      Writes quoted strings to the object file instead of the symbol
	        table. Use this option when an "Out of memory" error message
	        occurs in a program that has many string constants.
	
	/t      This option stands for terse. It suppresses warning messages
	        during compilation. However, severe error messages still are
	        displayed. This option is not available in QuickBASIC 4.00.
	        Also, /t is automatically added to the BC command line in
	        QuickBASIC 4.00b and 4.50 whenever you choose Make EXE
	        File from within QB.EXE.
	
	/v      Enables event trapping for communications (COM), light pen
	        (PEN), joystick (STRIG), timer (TIMER), music buffer (PLAY),
	        and function keys (KEY). Use this option to check between
	        statements for an occurrence of an event.
	
	/w      Enables event trapping for the same statements as /v, but
	        checks between lines for occurrence of an event.
	
	/x      Indicates presence of ON ERROR with RESUME, RESUME NEXT, or
	        RESUME 0.
	
	/zd     Produces an object file containing line-number records
	        corresponding to the line numbers of the source file. This
	        option is useful when you want to perform source-level
	        debugging using the Microsoft Symbolic Debug Utility (SYMDEB)
	        available with Microsoft Macro Assembler Version 4.00.
	
	/zi     Produces an object file containing debugging information used
	        by the Microsoft CodeView debugger, available with Microsoft C
	        Version 5.00, Microsoft Macro Assembler Version 5.00, and
	        Microsoft BASIC Compiler Version 6.00.
	
	The following BC.EXE options are supported in Microsoft BASIC Compiler
	Versions 6.00 and 6.00b, but not in QuickBASIC 4.00, 4.00b, or 4.50:
	
	/LP     Creates a protected-mode object file for use in MS OS/2
	        protected mode, no matter which operating system you are in at
	        compile time.
	
	/LR     Creates a real-mode object file for use in MS-DOS or MS OS/2
	        real mode (DOS 3.x box), no matter which operating system you
	        are in at compile time.
	
	/FPi    Generates in-line (i) coprocessor instructions for floating
	        point (FP) math. If a coprocessor is not present at run time,
	        the BASIC run-time system will emulate a coprocessor.
	
	/FPa    Generates code using alternate (a) math library, which runs
	        faster than emulating a coprocessor when none is present.

{% endraw %}