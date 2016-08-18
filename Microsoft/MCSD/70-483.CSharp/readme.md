##  Manage program flow (25–30%)##
###Implement multithreading and asynchronous processing###


- Use the [Task Parallel library](http://msdn.microsoft.com/en-us/library/dd460717.aspx "http://msdn.microsoft.com/en-us/library/dd460717.aspx") ([ParallelFor](http://msdn.microsoft.com/en-us/library/system.threading.tasks.parallel.for.aspx "http://msdn.microsoft.com/en-us/library/system.threading.tasks.parallel.for.aspx"), [Plinq](http://msdn.microsoft.com/en-us/library/dd997425.aspx "http://msdn.microsoft.com/en-us/library/dd997425.aspx"), [Tasks](http://msdn.microsoft.com/en-us/library/system.threading.tasks.task.aspx "http://msdn.microsoft.com/en-us/library/system.threading.tasks.task.aspx")); 
	- create [continuation tasks](http://msdn.microsoft.com/en-us/library/ee372288.aspx "http://msdn.microsoft.com/en-us/library/ee372288.aspx"); 
	- spawn threads by using [ThreadPool](http://msdn.microsoft.com/en-us/library/h4732ks0.aspx "http://msdn.microsoft.com/en-us/library/h4732ks0.aspx"); 
	- unblock the UI; 
	- use [async and await](http://msdn.microsoft.com/en-us/library/vstudio/hh191443.aspx "http://msdn.microsoft.com/en-us/library/vstudio/hh191443.aspx") keywords; 
	- manage data by using [concurrent collections](http://msdn.microsoft.com/en-us/library/dd997305.aspx "http://msdn.microsoft.com/en-us/library/dd997305.aspx")

###Manage multithreading###
- [Synchronize resources](http://msdn.microsoft.com/en-us/library/z8chs7ft.aspx "http://msdn.microsoft.com/en-us/library/z8chs7ft.aspx"); 
- implement [locking](https://msdn.microsoft.com/en-us/library/mt679037.aspx "https://msdn.microsoft.com/en-us/library/mt679037.aspx"); 
- [cancel a long-running task](http://msdn.microsoft.com/en-us/library/dd997396.aspx "http://msdn.microsoft.com/en-us/library/dd997396.aspx"); 
- implement [thread-safe methods](https://msdn.microsoft.com/en-us/library/a8544e2s(v=vs.120).aspx "https://msdn.microsoft.com/en-us/library/a8544e2s(v=vs.120).aspx") to handle [race conditions](https://msdn.microsoft.com/en-us/library/a8544e2s(v=vs.120).aspx "https://msdn.microsoft.com/en-us/library/a8544e2s(v=vs.120).aspx")

###Implement program flow###
- Iterate across collection and array items; 
- program decisions by using switch statements, if/then, and operators; 
- evaluate expressions

###Create and implement events and callbacks###
- Create event handlers; 
- subscribe to and unsubscribe from events; 
- use built-in delegate types to create events; 
- create delegates; 
- lambda expressions; 
- anonymous methods

###Implement exception handling###
- Handle exception types (SQL exceptions, network exceptions, communication exceptions, network timeout exceptions); 
- catch typed vs. base exceptions; 
- implement try-catch-finally blocks; 
- throw exceptions; 
- determine when to rethrow vs. throw; 
- create custom exceptions

###Preparation resources###
- [Parallel Computing](http://msdn.microsoft.com/en-gb/concurrency/default.aspx "http://msdn.microsoft.com/en-gb/concurrency/default.aspx")
- [Asynchronous programming with Async and Await (C# and Visual Basic)](http://msdn.microsoft.com/library/vstudio/hh191443.aspx "http://msdn.microsoft.com/library/vstudio/hh191443.aspx")
- [Simplifying Asynchronous Programming in C#](http://geekswithblogs.net/MarkPearl/archive/2011/10/11/simplifying-asynchronous-programming-in-c.aspx "http://geekswithblogs.net/MarkPearl/archive/2011/10/11/simplifying-asynchronous-programming-in-c.aspx")
- [Threading (C# and Visual Basic)](http://msdn.microsoft.com/library/ms173178.aspx "http://msdn.microsoft.com/library/ms173178.aspx")
- [Selection statements (C# reference)](http://msdn.microsoft.com/library/vstudio/676s4xab.aspx "http://msdn.microsoft.com/library/vstudio/676s4xab.aspx")

##Create and use types (25–30%)##

###Create types###

- Create value types (structs, enum), reference types, generic types, constructors, static variables, methods, classes, extension methods, optional and named parameters, and indexed properties; create overloaded and overriden methods
- Consume types
	- Box or unbox to convert between value types; cast types; convert types; handle dynamic types; ensure interoperability with unmanaged code, for example, dynamic keyword
- Enforce encapsulation
	- Enforce encapsulation by using properties, by using accessors (public, private, protected), and by using explicit interface implementation
- Create and implement a class hierarchy
- Design and implement an interface; inherit from a base class; create and implement classes based on the IComparable, IEnumerable, IDisposable, and IUnknown interfaces
- Find, execute, and create types at runtime by using reflection
- Create and apply attributes; read attributes; generate code at runtime by using CodeDom and lambda expressions; - - use types from the System.Reflection namespace (Assembly, PropertyInfo, MethodInfo, Type)

###Manage the object life cycle###
Manage unmanaged resources; implement IDisposable, including interaction with finalization; manage IDisposable by using the Using statement; manage finalization and garbage collection
Manipulate strings
Manipulate strings by using the StringBuilder, StringWriter, and StringReader classes; search strings; enumerate string methods; format strings
Preparation resources
Types (C# programming guide)
Classes and structs (C# programming guide)
Object-oriented programming (C# and Visual Basic)

##Debug applications and implement security (25–30%)
###Validate application input

Validate JSON data; data collection types; manage data integrity; evaluate a regular expression to validate the input format; use built-in functions to validate data type and content out of scope: writing regular expressions
Perform symmetric and asymmetric encryption
Choose an appropriate encryption algorithm; manage and create certificates; implement key management; implement the System.Security namespace; hashing data; encrypt streams

###Manage assemblies
- Version assemblies; 
- sign assemblies using strong names; 
- implement side-by-side hosting; 
- put an assembly in the global assembly cache; 
- create a WinMD assembly

####Be familiar with the following tools

- sn.exe
- al.exe
- signcode.exe
- gacutil.exe
- cordbg.exe

###Debug an application
Create and manage compiler directives; choose an appropriate build type; manage programming database files and symbols

###Implement diagnostics in an application
Implement logging and tracing; profiling applications; create and monitor performance counters; write to the event log
Preparation resources
Validating data
.NET Framework regular expressions

##Implement data access (25–30%)
###Perform I/O operations

Read and write files and streams; read and write from the network by using classes in the System.Net namespace; implement asynchronous I/O operations
Consume data
Retrieve data from a database; update data in a database; consume JSON and XML data; retrieve data by using web services

###Query and manipulate data and objects by using LINQ
Query data by using operators (projection, join, group, take, skip, aggregate); create method-based LINQ queries; query data by using query comprehension syntax; select data by using anonymous types; force execution of a query; read, filter, create, and modify data structures by using LINQ to XML

###Serialize and deserialize data
Serialize and deserialize data by using binary serialization, custom serialization, XML Serializer, JSON Serializer, and Data Contract Serializer

###Store data in and retrieve data from collections
Store and retrieve data by using dictionaries, arrays, lists, sets, and queues; choose a collection type; initialize a collection; add and remove items from a collection; use typed vs. non-typed collections; implement custom collections; implement collection interfaces
Preparation resources
File system and the registry (C# programming guide)
Connecting to data in Visual Studio
Editing data in your application