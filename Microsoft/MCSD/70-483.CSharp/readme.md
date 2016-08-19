# Programming in C# (70-483)

This guide is based, in large part, on the skills summary lists located here:

- [Microsoft Learning Portal](https://www.microsoft.com/en-us/learning/exam-70-483.aspx "https://www.microsoft.com/en-us/learning/exam-70-483.aspx")
- [Microsoft Born To Learn](https://borntolearn.mslearn.net/certification/p/wiki?es=webApp&ec=483 "https://borntolearn.mslearn.net/certification/p/wiki?es=webApp&ec=483") Training and Certification Community Wiki site

Anything else listed additionally is based on my own observations. Links listed here may be subject to copyright protection and access to such is up to the discretion of the authors\owners to which they pertain.

##  Manage program flow (25–30%)##
###Implement multithreading and asynchronous processing###


- Use the [Task Parallel library](http://msdn.microsoft.com/en-us/library/dd460717.aspx "http://msdn.microsoft.com/en-us/library/dd460717.aspx") ([ParallelFor](http://msdn.microsoft.com/en-us/library/system.threading.tasks.parallel.for.aspx "http://msdn.microsoft.com/en-us/library/system.threading.tasks.parallel.for.aspx"), [Plinq](http://msdn.microsoft.com/en-us/library/dd997425.aspx "http://msdn.microsoft.com/en-us/library/dd997425.aspx"), [Tasks](http://msdn.microsoft.com/en-us/library/system.threading.tasks.task.aspx "http://msdn.microsoft.com/en-us/library/system.threading.tasks.task.aspx")); 
	- create [continuation tasks](http://msdn.microsoft.com/en-us/library/ee372288.aspx "http://msdn.microsoft.com/en-us/library/ee372288.aspx");
	- Use TaskCreationOptions to manage nested\child task attachments
	- spawn threads by using [ThreadPool](http://msdn.microsoft.com/en-us/library/h4732ks0.aspx "http://msdn.microsoft.com/en-us/library/h4732ks0.aspx"); 
	- unblock the UI; 
	- use [async and await](http://msdn.microsoft.com/en-us/library/vstudio/hh191443.aspx "http://msdn.microsoft.com/en-us/library/vstudio/hh191443.aspx") keywords; 
	- manage data by using [concurrent collections](http://msdn.microsoft.com/en-us/library/dd997305.aspx "http://msdn.microsoft.com/en-us/library/dd997305.aspx")

###Manage multithreading###
- [Synchronize resources](http://msdn.microsoft.com/en-us/library/z8chs7ft.aspx "http://msdn.microsoft.com/en-us/library/z8chs7ft.aspx"); 
- implement [locking](https://msdn.microsoft.com/en-us/library/mt679037.aspx "https://msdn.microsoft.com/en-us/library/mt679037.aspx"); 
- [cancel a long-running task](http://msdn.microsoft.com/en-us/library/dd997396.aspx "http://msdn.microsoft.com/en-us/library/dd997396.aspx"); 
- implement [thread-safe methods](https://msdn.microsoft.com/en-us/library/a8544e2s(v=vs.120).aspx "https://msdn.microsoft.com/en-us/library/a8544e2s(v=vs.120).aspx") to handle [race conditions](https://msdn.microsoft.com/en-us/library/a8544e2s(v=vs.120).aspx "https://msdn.microsoft.com/en-us/library/a8544e2s(v=vs.120).aspx")

####Resources
- [How to synchronize access to a shared resource [...]](http://support.microsoft.com/kb/816161 "http://support.microsoft.com/kb/816161")
- [Thread Syncronization](http://msdn.microsoft.com/en-us/library/ms173179.aspx "http://msdn.microsoft.com/en-us/library/ms173179.aspx")
- [Parallel Programming: Task Cancellation (MSDN Blog post)](http://blogs.msdn.com/b/csharpfaq/archive/2010/07/19/parallel-programming-task-cancellation.aspx "http://blogs.msdn.com/b/csharpfaq/archive/2010/07/19/parallel-programming-task-cancellation.aspx")
- [Cancel an Async Task or a List of Tasks (C# and Visual Basic)](http://msdn.microsoft.com/en-us/library/vstudio/jj155759.aspx "http://msdn.microsoft.com/en-us/library/vstudio/jj155759.aspx")
- [Thread safe method in c# (MSDN Forum thread)](http://social.msdn.microsoft.com/Forums/vstudio/en-US/9639d953-b4d2-4b0b-a584-1c3c70c93323/thread-safe-method-in-c "http://social.msdn.microsoft.com/Forums/vstudio/en-US/9639d953-b4d2-4b0b-a584-1c3c70c93323/thread-safe-method-in-c")
- [Managed Threading Best Practices](http://msdn.microsoft.com/en-us/library/1c9txz50.aspx "http://msdn.microsoft.com/en-us/library/1c9txz50.aspx")
- [Walkthrough: Authoring a Simple Multithreaded Component with Visual C#](http://msdn.microsoft.com/en-us/library/48cfdff6(v=vs.71).aspx "http://msdn.microsoft.com/en-us/library/48cfdff6(v=vs.71).aspx")

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

####Preparation resources###
- [Parallel Computing](http://msdn.microsoft.com/en-gb/concurrency/default.aspx "http://msdn.microsoft.com/en-gb/concurrency/default.aspx")
- [Asynchronous programming with Async and Await (C# and Visual Basic)](http://msdn.microsoft.com/library/vstudio/hh191443.aspx "http://msdn.microsoft.com/library/vstudio/hh191443.aspx")
- [Simplifying Asynchronous Programming in C#](http://geekswithblogs.net/MarkPearl/archive/2011/10/11/simplifying-asynchronous-programming-in-c.aspx "http://geekswithblogs.net/MarkPearl/archive/2011/10/11/simplifying-asynchronous-programming-in-c.aspx")
- [Threading (C# and Visual Basic)](http://msdn.microsoft.com/library/ms173178(v=vs.110).aspx "http://msdn.microsoft.com/library/ms173178(v=vs.110).aspx")
- [Managed Threading Best Practices](https://msdn.microsoft.com/en-us/library/1c9txz50(v=vs.110).aspx "https://msdn.microsoft.com/en-us/library/1c9txz50(v=vs.140).aspx")
- [Selection statements (C# reference)](http://msdn.microsoft.com/library/vstudio/676s4xab.aspx "http://msdn.microsoft.com/library/vstudio/676s4xab.aspx")


##Create and use types (25–30%)##

###Create types###

- Create value types (structs, enum), reference types, generic types, constructors, static variables, methods, classes, extension methods, optional and named parameters, and indexed properties; 
- Create overloaded and overriden methods
- Consume types
	- [Box or unbox](http://msdn.microsoft.com/en-us/library/yz2be5wk(v=vs.110).aspx "http://msdn.microsoft.com/en-us/library/yz2be5wk(v=vs.110).aspx") to convert between value types; 
	- cast types; 
	- convert types; 
	- handle [dynamic types](http://msdn.microsoft.com/en-us/library/dd264736(v=vs.110).aspx "http://msdn.microsoft.com/en-us/library/dd264736(v=vs.110).aspx"); 
	- ensure [interoperability with unmanaged code](https://msdn.microsoft.com/en-us/library/sd10k43k(v=vs.110).aspx "https://msdn.microsoft.com/en-us/library/sd10k43k(v=vs.110).aspx"), for example, dynamic keyword
- Enforce encapsulation
	- Enforce encapsulation by using properties, by using accessors (public, private, protected), and by using explicit interface implementation
- Create and implement a class hierarchy
- Design and implement an interface; 
- inherit from a base class; 
- create and implement classes based on the IComparable, IEnumerable, IDisposable, and IUnknown interfaces
- Find, execute, and create types at runtime by using reflection
- Create and apply attributes; 
- read attributes; 
- generate code at runtime by using CodeDom and lambda expressions;
- use types from the System.Reflection namespace (Assembly, PropertyInfo, MethodInfo, Type)

###Manage the object life cycle###

- Manage unmanaged resources; 
- implement IDisposable, including interaction with finalization; 
- manage IDisposable by using the Using statement; 
- manage finalization and garbage collection
	- Utilize a [WeakReference](https://msdn.microsoft.com/en-us/library/ms404247(v=vs.110).aspx "https://msdn.microsoft.com/en-us/library/ms404247(v=vs.110).aspx") object
		- Understand the [difference](https://msdn.microsoft.com/en-us/library/ms404247(v=vs.110).aspx#Anchor_0 "https://msdn.microsoft.com/en-us/library/ms404247(v=vs.110).aspx#Anchor_0") between a short WeakReference and a long WeakReference

###Manipulate strings

- Manipulate strings by using the StringBuilder, StringWriter, and StringReader classes; 
- search strings; 
- enumerate string methods; 
- format strings

####Preparation resources

- [Types (C# programming guide)](http://msdn.microsoft.com/library/ms173104.aspx "http://msdn.microsoft.com/library/ms173104.aspx")
- [Classes and structs (C# programming guide)](http://msdn.microsoft.com/library/vstudio/ms173109.aspx "http://msdn.microsoft.com/library/vstudio/ms173109.aspx")
- [Object-oriented programming (C# and Visual Basic)](http://msdn.microsoft.com/library/dd460654.aspx "http://msdn.microsoft.com/library/dd460654.aspx")

##Debug applications and implement security (25–30%)
###Validate application input

- Validate JSON data; 
- data collection types; 
- manage data integrity; 
- evaluate a regular expression to validate the input format; 
- use built-in functions to validate data type and content out of scope: writing regular expressions

###Perform symmetric and asymmetric encryption

- Choose an appropriate encryption algorithm
	- Algorithms:
		- Symmetric cipher: [AES-256](http://msdn.microsoft.com/en-us/library/system.security.cryptography.aesmanaged.aspx "http://msdn.microsoft.com/en-us/library/system.security.cryptography.aesmanaged.aspx")
		- Asymetric cipher: [RSA (with 4096-bit key)](http://msdn.microsoft.com/en-us/library/system.security.cryptography.rsacryptoserviceprovider.aspx "http://msdn.microsoft.com/en-us/library/system.security.cryptography.rsacryptoserviceprovider.aspx")
		- Hash: [SHA-512](http://msdn.microsoft.com/en-us/library/system.security.cryptography.sha512.aspx "http://msdn.microsoft.com/en-us/library/system.security.cryptography.sha512.aspx")
		- Message Authentication Code: [HMAC with SHA-512](http://msdn.microsoft.com/en-us/library/system.security.cryptography.hmacsha512.aspx "http://msdn.microsoft.com/en-us/library/system.security.cryptography.hmacsha512.aspx")
- manage and create certificates; 
- implement key management; 
- implement the System.Security namespace; 
- hashing data; 
- encrypt streams

###Manage assemblies
- Version assemblies; 
- sign assemblies using strong names; 
- implement side-by-side hosting; 
- put an assembly in the global assembly cache; 
- create a WinMD assembly

####Be familiar with the following tools

- [sn.exe](https://msdn.microsoft.com/en-us/library/k5b5tt23(v=vs.110).aspx "https://msdn.microsoft.com/en-us/library/k5b5tt23(v=vs.110).aspx")
- [al.exe](https://msdn.microsoft.com/en-us/library/c405shex(v=vs.140).aspx "https://msdn.microsoft.com/en-us/library/c405shex(v=vs.140).aspx")
- [signtool.exe](https://msdn.microsoft.com/en-us/library/8s9b9yaz(v=vs.110).aspx "https://msdn.microsoft.com/en-us/library/8s9b9yaz(v=vs.110).aspx")
- [gacutil.exe](https://msdn.microsoft.com/en-us/library/ex0ss12c(v=vs.110).aspx "https://msdn.microsoft.com/en-us/library/ex0ss12c(v=vs.110).aspx")
- [MDbg.exe](https://msdn.microsoft.com/en-us/library/ms229861(v=vs.110).aspx "https://msdn.microsoft.com/en-us/library/ms229861(v=vs.110).aspx")
- [Makecert.exe (deprecated)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx "https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx") - x.509 certificate creation tool
- [New-SelfSignedCertificate (PowerShell commandlet)](https://technet.microsoft.com/library/hh848633 "https://technet.microsoft.com/library/hh848633")

###Debug an application

- Create and manage compiler directives; 
- choose an appropriate build type; 
- manage programming database files and symbols

###Implement diagnostics in an application

- Implement [logging](https://support.microsoft.com/en-us/kb/307024 "https://support.microsoft.com/en-us/kb/307024") and [tracing](https://msdn.microsoft.com/en-us/library/system.diagnostics.trace(v=vs.110).aspx "https://msdn.microsoft.com/en-us/library/system.diagnostics.trace(v=vs.110).aspx"); 
- profiling applications; 
- create and monitor performance counters; 
- write to the [event log](https://msdn.microsoft.com/en-us/library/system.diagnostics.eventlog(v=vs.110).aspx "https://msdn.microsoft.com/en-us/library/system.diagnostics.eventlog(v=vs.110).aspx")

####Preparation resources

- Validating data
- .NET Framework regular expressions

##Implement data access (25–30%)
###Perform I/O operations

- Read and write files and streams; 
- read and write from the network by using classes in the System.Net namespace; 
- implement asynchronous I/O operations

###Consume data

- Retrieve data from a database; 
- update data in a database; 
- consume JSON and XML data; 
- retrieve data by using web services

###Query and manipulate data and objects by using LINQ

- Query data by using [operators](https://msdn.microsoft.com/en-us/library/bb397676.aspx "https://msdn.microsoft.com/en-us/library/bb397676.aspx") (projection, join, group, take, skip, aggregate); 
- create [method-based LINQ queries](https://msdn.microsoft.com/en-us/library/mt693056.aspx "https://msdn.microsoft.com/en-us/library/mt693056.aspx"); 
- query data by using query comprehension syntax; 
- select data by using anonymous types; 
- force execution of a query; 
- read, filter, create, and modify data structures by using LINQ to XML

###Serialize and deserialize data

- Understand the XmlObjectSerializer class
- Serialize and deserialize data by using:
	- binary serialization 
	- custom serialization 
	- XML Serializer 
	- JSON Serializer 
	- Data Contract Serializer

###Store data in and retrieve data from collections

- Store and retrieve data by using dictionaries, arrays, lists, sets, and queues; 
- choose a collection type; initialize a collection; 
- add and remove items from a collection; 
- use typed vs. non-typed collections; 
- implement custom collections; 
- implement collection interfaces

####Preparation resources

- File system and the registry (C# programming guide)
- Connecting to data in Visual Studio
- Editing data in your application