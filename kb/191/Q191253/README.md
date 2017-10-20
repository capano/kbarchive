---
layout: page
title: "Q191253: HOWTO: Implement Multi-user Custom Counters in DAO 3.5"
permalink: /kb/191/Q191253/
---

## Q191253: HOWTO: Implement Multi-user Custom Counters in DAO 3.5

{% raw %}

	Article: Q191253
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 5.0,6.0
	Operating System(s): 
	Keyword(s): kbVBp500 kbVBp600 kbGrpDSVBDB
	Last Modified: 01-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Because the Microsoft Jet database engine has a read-cache and lazy writes, you
	can get duplicate values in your custom counter field if two applications add
	records in less time than it takes the cache to refresh and the lazy-write
	mechanism to flush to disk. This article presents a method that takes these
	factors into account.
	
	MORE INFORMATION
	================
	
	The Microsoft Jet database engine provides a Counter (AutoIncrement) field.
	However, it starts at 1 and increments by 1. In order to do something different,
	such as increment by 10, you have to implement your own counter mechanism. In
	order to do so, you need to be aware of how some Microsoft Jet performance
	optimizations affects your implementation.
	
	Microsoft Jet has a read-cache that is updated every PageTimeout milli- seconds
	(default is 5000ms = 5 seconds). It also has a lazy-write mechanism that
	operates on a separate thread to main processing and thus writes changes to disk
	asynchronously. These two mechanisms help boost performance, but in certain
	situations that require high concurrency, they can create problems.
	
	Earlier versions of Microsoft Jet did not expose full programmatic control over
	concurrency. To refresh the cache, you had to close and re-open the database.
	Microsoft Jet 2.x and earlier did not have a lazy-write mechanism.
	
	The Microsoft Jet 3.5 database engine provides two methods to ensure that your
	application has current data:
	
	- DBEngine.Idle dbRefreshCache
	
	- CommitTrans dbForceOSFlush
	
	DBEngine.Idle dbRefreshCache
	----------------------------
	
	There is a separate read-cache for each Workspace object. This method immediately
	refreshes the read-cache for all Workspace objects in the DBEngine.Workspaces
	collection. The read-cache for Workspace objects not appended to this collection
	are unaffected.
	
	CommitTrans dbForceOSFlush
	--------------------------
	
	In Microsoft Jet 2.x and prior, all writes were immediately committed. With Win32
	and multi-threading, Microsoft Jet introduced a lazy-write mechanism. This
	method flushes all writes for objects created off the same Workspace the
	BeginTrans/CommitTrans is invoked from.
	
	These methods are preferable to modifying registry values to get the same effect,
	because you can precisely control where you need this value. Global registry
	programs will adversely affect engine performance in other areas and in other
	applications.
	
	EXAMPLE
	
	The following example provides a function for generating custom counter numbers
	and handling the concurrency and locking issues that result from the process. It
	involves the use of a second table to store the next available key value. This
	is used for performance reasons and also to avoid adversely affecting users who
	would just need to read data.
	
	The main function is NextKeyValue. It accepts four arguments: database object,
	table name, workspace object, and increment value. The last two are optional and
	default to DBEngine(0) and 1 respectively. It opens the table exclusively and
	reads the value from the first field of the first record. This is the key value
	returned. It then increments the value for the next user and releases the
	table.
	
	When you set the initial value in the table, this is the first value returned by
	the function.
	
	The error handling is designed to handle locking problems opening the table. If
	the locks time-out, the function returns -1 as the next key value. If any other
	error occurs, the function raises a run-time error that the main application
	will need to trap.
	
	Because most people leave their registry settings untouched, Microsoft Jet will
	usually have a 100ms delay between lock-retries. If all instances of Jet have
	the same delay, this could result in a race situation and cause your application
	to time-out more than is necessary. The NextKeyValue function sets the lock
	retry to a random interval between 60 and 120 milli- seconds to reduce the
	chance of a race condition occurring. The test application is responsible for
	using the RANDOM statement to seed the random number generator.
	
	The test application adds 100 records to the table. It does not implement any
	error handling.
	
	WARNING: Microsoft provides programming examples for illustration only, without
	warranty either expressed or implied, including, but not limited to, the implied
	warranties of merchantability and/or fitness for a particular purpose. This
	article assumes that you are familiar with the programming language being
	demonstrated and the tools used to create and debug procedures. Microsoft
	support engineers can help explain the functionality of a particular procedure,
	but they will not modify these examples to provide added functionality or
	construct procedures to meet your specific needs. If you have limited
	programming experience, you may want to contact the Microsoft fee-based
	consulting line at (800) 936-5200. For more information about the support
	options available from Microsoft, please see the following page on the World
	Wide Web:
	
	  http://msdn.microsoft.com/support/
	
	Database Setup
	--------------
	
	1. In Microsoft Access, open the NWind.MDB file, and create the following
	  tables:
	
	  Table: KeyStore
	     Field Name: NextValue
	     Type:       Number, Long Integer
	
	  Table: KeyTest
	     Field Name: ID
	     Type:       Number, Long Integer
	
	     Field Name: Description
	     Type:       Text, 50
	
	2. Open the KeyStore table and add a record. Set NextValue to the amount that
	  you want your counter to start from. Example: 3.
	
	3. Save the record and closeMicrosoft Access.
	
	Test Program
	------------
	
	1. Open a new Visual Basic or Visual Basic for Applications project with a Form
	  (Form1) and a Module (Module1).
	
	2. Add a reference (Project | References or Tools | References) for Microsoft
	  DAO 3.5 Object Library.
	
	3. Add the following code to the Module:
	
	     Option Explicit
	     Private Const MAX_RETRIES = 10
	
	     Function NextKeyValue(db As Database, _
	                           ByVal TableName As String, _
	                           Optional ws As Workspace = Nothing, _
	                           Optional Increment As Long = 1) As Long
	     Dim rs As Recordset, ErrorCount As Long, TempKeyValue As Long
	       NextKeyValue = -1   ' Returns this if the routine times out
	       On Error GoTo NKV_Err
	       ' Random delay between 90ms and 150ms prevents race condition
	       DBEngine.SetOption dbLockDelay, 90 + Rnd * 60
	       ' use default workspace if not supplied
	       If ws Is Nothing Then Set ws = DBEngine(0)
	       ' Error should occur on the next line if table is in use
	       ' Open it exclusively
	       Set rs = db.OpenRecordset(TableName, dbOpenTable, _
	                                 dbDenyRead Or dbDenyWrite)
	       DBEngine.Idle dbRefreshCache         ' refresh read cache
	       TempKeyValue = rs(0)                 ' get value to use
	       ws.BeginTrans
	         rs.Edit
	         rs(0) = TempKeyValue + Increment   ' value for next call
	         rs.Update
	       ws.CommitTrans dbForceOSFlush        ' flush the lazy-write cache
	       rs.Close
	
	       NextKeyValue = TempKeyValue
	       Exit Function
	
	     NKV_Abort:               ' clean up the mess
	       On Error Resume Next
	       ws.Rollback
	       rs.Close
	       Exit Function
	
	     NKV_Err:
	       Select Case Err.Number
	         Case 3008, 3009, 3189, 3211, 3260, 3261, 3262
	           ' various locking errors (above)
	           ErrorCount = ErrorCount + 1
	           If ErrorCount > MAX_RETRIES Then
	             Resume NKV_Abort
	           Else
	              Resume
	           End If
	         Case Else  ' unhandled errors
	           Err.Raise Err.Number, Err.Source, Err.Description
	       End Select
	
	     End Function
	
	4. Add a CommandButton (Command1) and a Text Box (Text1) to the form.
	
	5. Add the following code to the form:
	
	        Option Explicit
	        Dim ws As Workspace, db As Database
	
	        Private Sub Command1_Click()
	        Dim SQL As String, I As Long
	          For I = 1 To 100
	            SQL = "INSERT INTO KeyTest VALUES (" & _
	                  NextKeyValue(db, "KeyStore", ws, 10) & _
	                  ",'Test Record " & Time & "')"
	            db.Execute SQL
	            Text1 = CStr(I)
	            Me.Refresh
	          Next I
	        End Sub
	
	        Private Sub Form_Load()
	          Randomize
	          Set ws = DBEngine(0)
	          Set db = ws.OpenDatabase("NWIND.MDB")
	        End Sub
	
	        Private Sub Form_Unload(Cancel As Integer)
	          db.Close
	          ws.Close
	        End Sub
	
	6. In Visual Basic, compile the application to an EXE. Run the application from
	  multiple computers and click Command1 at the same time. It will run to
	  completion (barring any unhandled errors) and add records without duplicate
	  ID numbers.
	
	NOTES:
	
	1. The KeyStore table does not require an index. You will get better performance
	  and have fewer problems if you do not add (or allow Access to add) and index
	  or Primary Key to the table.
	
	2. The fewer indexes on the KeyText table, the better. Indices have a negative
	  effect on the ability to lock and update data quickly. If you have problems
	  in your application, try reducing the number of indices.
	
	REFERENCES
	==========
	
	For more information about Jet and DAO, please refer to your Visual Basic
	documentation.
	
	
	Additional query words: count autonumber custom multiuser kbDAO350 kbVBp500 kbVBp600 kbdse kbDSupport kbVBp
	
	======================================================================
	Keywords          : kbVBp500 kbVBp600 kbGrpDSVBDB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVB500 kbVB600
	Version           : :5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}