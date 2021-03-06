---
layout: page
title: "Q192099: FIX: STATIC_DOWNCAST and DYNAMIC_DOWNCAST"
permalink: /kb/192/Q192099/
---

## Q192099: FIX: STATIC_DOWNCAST and DYNAMIC_DOWNCAST

{% raw %}

	Article: Q192099
	Product(s): Microsoft C Compiler
	Version(s): winnt:4.0,5.0
	Operating System(s): 
	Keyword(s): kberrmsg kbdocerr kbLangCPP kbMFC kbDocs kbVC400bug kbVC500bug kbVC600fix kbBug kbGrpDS
	Last Modified: 27-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, version 4.0 
	- Microsoft Visual C++, 32-bit Enterprise Edition, version 5.0 
	- Microsoft Visual C++, 32-bit Professional Edition, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The following provides supplemental information to the documentation on
	STATIC_DOWNCAST:
	
	     STATIC_DOWNCAST( class_name, pobject )
	
	Parameters:
	
	  
	
	     class_name
	   
	
	  The name of the class you want to cast to.
	
	   
	     pobject
	   
	
	  The pointer to be cast to a pointer to a class_name object.
	
	Remarks:
	
	  This macro casts pobject to a pointer to a class_name object. pobject must
	  either be NULL, or point to an object of a class which is derived directly,
	  or indirectly, from class_name. In builds of your application with the _DEBUG
	  preprocessor symbol defined, the macro will ASSERT if pobject is not NULL and
	  if it points to an object that is not a "kind of" the class_name (see
	  definition for the CObject::IsKindOf). In non- _DEBUG builds, the macro
	  performs the cast without any type checking.
	
	  class_name must be derived from CObject and use the DECLARE_DYNAMIC and
	  IMPLEMENT_DYNAMIC, the DECLARE_DYNCREATE and IMPLEMENT_DYNCREATE, or the
	  DECLARE_SERIAL and IMPLEMENT_SERIAL macros explained in the Help topic
	  "CObject Class: Deriving a Class from Cobject."
	
	  For example, you might cast a pointer to CYourDocument, called pYourDoc, to a
	  pointer to CDocument using the following expression:
	
	        CDocument* pDoc = STATIC_DOWNCAST(CDocument, pYourDoc);
	
	  If pYourDoc does not point to an object derived directly or indirectly from
	  CDocument, the macro will ASSERT.
	
	  Similarly, the documentation on DYNAMIC_DOWNCAST should be supplemented by
	  saying that class_name must be derived from CObject and use the
	  DECLARE_DYNAMIC and IMPLEMENT_DYNAMIC, the DECLARE_DYNCREATE and
	  IMPLEMENT_DYNCREATE, or the DECLARE_SERIAL and IMPLEMENT_SERIAL macros.
	
	  If you leave out the pair of DECLARE_... and IMPLEMENT_... macros from your
	  code, trying to cast the class pointer using STATIC_DOWNCAST or
	  DYNAMIC_DOWNCAST gives compiler errors like the following:
	
	  error C2039: 'classCMyClass' : is not a member of 'CMyClass'
	
	  error C2065: 'classCMyClass' : undeclared identifier
	
	STATUS
	======
	
	
	
	MORE INFORMATION
	================
	
	Following is additional information on related subjects:
	
	1. The documentation on CObject::IsKindOf should also include:
	
	  This function works only for classes declared with the
	  DECLARE_DYNAMIC, DECLARE_DYNCREATE, or DECLARE_SERIAL macros.
	
	2. The documentation on DECLARE_DYNCREATE should also include:
	
	  The DECLARE_DYNCREATE macro includes all the functionality of
	  DECLARE_DYNAMIC.
	
	3. You may also want to see the topics on the static_cast and dynamic_cast
	  operators in the Visual C++ documentation. Please note that the
	  STATIC_DOWNCAST and DYNAMIC_DOWNCAST macros suggest an action that is
	  contrary to the common usage of the term "downcast". The term "downcast" is
	  commonly used to signify the movement of an object down a class hierarchy,
	  from a given class to a class derived from it. This may be confusing when you
	  consider that the STATIC_DOWNCAST and DYNAMIC_DOWNCAST macros perform the
	  action of "upcasting". The term "upcast" is commonly used to signify the
	  movement of an object up the class hierarchy, from a derived class to a class
	  it is derived from.
	
	REFERENCES
	==========
	
	  Q151070 FIX: DYNAMIC_DOWNCAST & STATIC_DOWNCAST Causes Stack Overflow
	
	Additional query words: DECLARE_DYNAMIC IMPLEMENT_DYNAMIC DECLARE_DYNCREATE IMPLEMENT_DYNCREATE DECLARE_SERIAL IMPLEMENT_SERIAL IsKindOf
	
	======================================================================
	Keywords          : kberrmsg kbdocerr kbLangCPP kbMFC kbDocs kbVC400bug kbVC500bug kbVC600fix kbBug kbGrpDSMFCATL kbISS 
	Technology        : kbVCsearch kbVC400 kbAudDeveloper kbVC500 kbVC32bitSearch kbVC500Search
	Version           : winnt:4.0,5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
