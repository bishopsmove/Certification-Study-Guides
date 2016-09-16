# Developing Microsoft Azure and Web Services (70-487)

This guide is based, in large part, on the skills summary lists located here:

- [Microsoft Learning Portal](https://www.microsoft.com/en-us/learning/exam-70-487.aspx "https://www.microsoft.com/en-us/learning/exam-70-487.aspx")
- [Microsoft Born To Learn](https://borntolearn.mslearn.net/certification/p/wiki?es=webApp&ec=487 "https://borntolearn.mslearn.net/certification/p/wiki?es=webApp&ec=487") Training and Certification Community Wiki site

Anything else listed additionally is based on my own observations. Links listed here may be subject to copyright protection and access to such is up to the discretion of the authors\owners to which they pertain.

####Additional Resources

- Pluralsight [recommended videos for 70-487](http://blog.pluralsight.com/developing-microsoft-azure-and-web-services-microsoft-exam-70-487 "http://blog.pluralsight.com/developing-microsoft-azure-and-web-services-microsoft-exam-70-487")
- MS Virtual Academy - [Applications on Azure: Putting All the Pieces Together](https://mva.microsoft.com/en-US/training-courses/applications-on-azure-putting-all-the-pieces-together-14429 "https://mva.microsoft.com/en-US/training-courses/applications-on-azure-putting-all-the-pieces-together-14429") (Updated tutorial from *Developing Windows Azure and Web Services Jump Start*)
- Barbarian Meets Coding - [Notes for 70-487](https://www.barbarianmeetscoding.com/wiki/70-487-azure-and-web-services-certification-study-guide/ "https://www.barbarianmeetscoding.com/wiki/70-487-azure-and-web-services-certification-study-guide/")

##Accessing data (20-25%)

- Choose data access technologies
	- Choose a technology based on application requirements
		- [ADO.NET](https://msdn.microsoft.com/en-us/library/h43ks021.aspx "https://msdn.microsoft.com/en-us/library/h43ks021.aspx")
			- DataReaders
				- Faster data access than DataAdapters
				- contains both synchronous and asynchronous methods
				- iterates only once and in forward-only fashion
				- cannot enfore constraints or recognize relationships between DB tables
			- DataAdapter
				- closely mimics the behavior of an RDBMS, like an in-memory portion of the DB
				- contains only synchronous methods
				- can iterate *n* number of times in a variety of means
				- can be loaded directly from XML documents and can persist to XML natively
				- Inherently serializable, allowing DataSets and DataTables to be easily passed between tiers
		- [Entity Framework](https://msdn.microsoft.com/en-us/library/bb399567.aspx "https://msdn.microsoft.com/en-us/library/bb399567.aspx")
			- [Impedance Mismatch](https://en.wikipedia.org/wiki/Object-relational_impedance_mismatch "https://en.wikipedia.org/wiki/Object-relational_impedance_mismatch") - O/RMs, like EF, were designed to address this issue.
			- O/RMs, like EF, allow for a separation of concerns between the conceptual model and the underlying data store
			- EF Model
				- EF DSLs: All used to define the EF model within the .edmx file:
					- CSDL: Conceptual Schema Definition Language
					- SSDL: Store Schema Definition Language
					- MSL: Mapping Specification Language
				- Entity Model Designer: 
					- Used to create the .edmx file
					- Manipulates the model
					- Manipulates associations
					- Manipulates and updates mappings
					- allows for adding/modifying inheritance relationships
				- Entity Data Model Wizard: enables you to build out the conceptual model and utilize an existing data store
				- Create Database Wizard: Opposite to the EDM Wizard, enables you to specify/modify the conceptual model and handles the implementation of the database instance, based on the conceptual model
				- Update Model Wizard: Allows for modification of the conceptual model, the underlying storage model and the mappings between them.
			- Mapping Strategies:
				- Table Per Hierarchy (TPH)
					- Better Performance
					- Resulting Data is slightly denormalized
					- Adds Descriminator column to determine type of each record
				- Table Per Type (TPT)
					- Less performant
					- Resulting data is properly normalized
					- Performs a Join across multiple tables to retrieve a single record's worth of data
				- Table Per Concrete Type (TPC) (Not likely to be covered in the test)
				- Mixed Inheritance (MI) (Not likely to be covered in the test)
			- DbContext vs ObjectContext
				- ObjectContext (Legacy)
				- DbContext (Current)
					- Wrapper to ObjectContext, with additional functionality
				- ObjectContext entities
					- EntityObject - Base class of inheritance
					- Attributes
						- EdmEntityTypeAttribute
						- SerializableAttribute
						- DataContractAttribute (required for WCF's default serialization)
			- LazyLoadingEnabled - The ContextOptions property is set to true by default.
				- Triggered when a Navigation Property is accessed, will conduct another round-trip to the database to pull relevant data. Considered a chatty pattern.
				- The reciprocal is eager-loading, triggered by the Include() method. Considered a chucky pattern.
		- [WCF Data Services](https://msdn.microsoft.com/en-us/library/cc668794.aspx "https://msdn.microsoft.com/en-us/library/cc668794.aspx")
			- Allows a web service interface (HTTP/S) to function as a data provider
			- OData
				- When WCF utilizes OData, data resources can be addressible by URI, providing for universal data access
				- Default data format is Atom but can output to JSON and/or XML and conforms to RESTful notation
			- Meant to be utilized with EF
		- [Azure storage](https://msdn.microsoft.com/en-us/magazine/gg309178.aspx "https://msdn.microsoft.com/en-us/magazine/gg309178.aspx")
			- [Code Project](http://www.codeproject.com/Articles/83481/Windows-Azure-Storage "http://www.codeproject.com/Articles/83481/Windows-Azure-Storage")
- Implement caching
	- Caching Options
		- [WCF Caching Support](https://msdn.microsoft.com/en-us/library/ee230443.aspx "https://msdn.microsoft.com/en-us/library/ee230443.aspx")
			- Basic Web HTTP Service Caching
			- SQL Cache Dependency
			- Conditional HTTP GET based Caching
		- [Azure Caching Service](https://msdn.microsoft.com/en-us/magazine/gg983488.aspx "https://msdn.microsoft.com/en-us/magazine/gg983488.aspx")
			- Shared of Co-Located Caching
			- Dedicated Caching
	- Cache static data, 
	- apply [cache policy](https://msdn.microsoft.com/en-us/library/system.runtime.caching.cacheitempolicy.aspx#Anchor_6 "https://msdn.microsoft.com/en-us/library/system.runtime.caching.cacheitempolicy.aspx#Anchor_6") (including expirations)
		- Absolute Expirations
		- Sliding Expirations
	- CachItemPriority
	- CacheChangeMonitor
		- CacheEntryChangeMonitor : base class
		- FileChangeMonitor: specific file
		- HostFileChangeMonitor: directory or file paths
		- SqlChangeMonitor
	- ObjectCache vs HttpContext.Cache
		- If implemented with ASP.Net: HttpContext.Cache
		- Everything else: ObjectCache
	-  use CacheDependency to refresh cache data
		-  [SqlCacheDependency](https://msdn.microsoft.com/en-us/library/system.web.caching.sqlcachedependency.aspx "https://msdn.microsoft.com/en-us/library/system.web.caching.sqlcachedependency.aspx")
			-  Wraps the SqlDependency object
		-  [AggregateCacheDependency](https://msdn.microsoft.com/en-us/library/system.web.caching.aggregatecachedependency.aspx "https://msdn.microsoft.com/en-us/library/system.web.caching.aggregatecachedependency.aspx")
			-  Specific to a collection of objects, where a change to one item in the collection removes the collection from cache and refreshes.
	-  [query notifications](https://msdn.microsoft.com/en-us/library/t9x04ed2.aspx "https://msdn.microsoft.com/en-us/library/t9x04ed2.aspx")
		-  [Enabling Query Notifications](https://msdn.microsoft.com/en-us/library/ms172133.aspx "https://msdn.microsoft.com/en-us/library/ms172133.aspx")
- Implement transactions
	- [Transactions](https://msdn.microsoft.com/en-us/library/system.transactions(v=vs.110).aspx "https://msdn.microsoft.com/en-us/library/system.transactions(v=vs.110).aspx")
		- Considered part of an explicit programming model
	- [TransactionScope](https://msdn.microsoft.com/en-us/library/system.transactions.transactionscope.aspx "https://msdn.microsoft.com/en-us/library/system.transactions.transactionscope.aspx")
		- Considered part of an implicit programming model
		- The more recommended choice (by MS)
	- Manage transactions by using the API from System.Transactions namespace
		- use TransactionScope in `Using` block, with final command `TransactionScope.Complete()` executed.
	-  implement distributed transactions
		-  When more than one connection is opened inside a transaction, that transaction is automatically escalated to a full distributed transaction.
	-  specify transaction isolation level
		- Unspecified
		- Chaos - not supported in SQL or Oracle
		- ReadUncommitted - No locks
		- ReadCommitted - Shared locks
		- RepeatableRead - All relevant data locked
		- Serializable - Range lock over DataSet
		- Snapshot - Copy of data, fully insulated. Allows concurrent changes.
- Implement data storage in Azure
	- Access data storage in Azure
	-  choose data storage mechanism in Azure:
		- blobs
		- tables
		- [queues](https://azure.microsoft.com/en-us/documentation/articles/storage-dotnet-how-to-use-queues/ "https://azure.microsoft.com/en-us/documentation/articles/storage-dotnet-how-to-use-queues/")
		- SQL Database
	-  distribute data by using the Content delivery network (CDN)
	-  handle exceptions by using retries (SQL Database)
	-  manage Azure Caching
- Create and implement a WCF Data Services service
	- Address resources
	-  implement filtering
		-  EXAMPLE
	-  create a query expression
	-  access payload formats (including JSON)
	-  use data service interceptors and service operators
		-  EXAMPLE
- Manipulate XML data structures
	- Read filter, create, modify XML data structures
	-  Manipulate XML data by using:
		- XMLReader
			- EXAMPLE
		- XMLWriter
			- EXAMPLE
		- XMLDocument
		- XPath
		- LINQ to XML
	-  transform XML by using XSLT transformations

####Preparation resources

- Transaction isolation levels
- WCF Data Services
- XML documents and data

##Querying and manipulating data by using Entity Framework (20-25%)

- Query and manipulate data by using the Entity Framework
- Query, update, and delete data by using DbContext
-  build a query that uses deferred execution
-  implement lazy loading and eager loading
-  create and run compiled queries
-  query data by using Entity SQL
-  perform asynchronous operations using Entity Framework
-  map a stored procedure
- Query and manipulate data by using Data Provider for Entity Framework
- Query and manipulate data by using Connection, DataReader, and Command from the System.Data.EntityClient namespace
-  perform synchronous and asynchronous operations
-  manage transactions (API)
-  programmatically configure a Data Provider
- Query data by using LINQ to Entities
- Query data by using LINQ operators (for example, project, skip, aggregate, filter, and join)
-  log queries and database commands
-  implement query boundaries (IQueryable vs. IEnumerable)
-  implement async query
- Query and manipulate data by using ADO.NET
- Query and manipulate data by using Connection, DataReader, Command, DataAdapter, DataSet
-  perform synchronous and asynchronous operations
-  manage transactions (API)
- Create an Entity Framework data model
- Structure the data model using table per type, table per class, table per hierarchy
-  choose and implement an approach to manage a data model (code first vs. model first vs. database first)
-  implement POCO objects
-  describe a data model by using conceptual schema definitions, storage schema definition, mapping language (CSDL, SSDL, MSL), and Custom Code First Conventions

####Preparation resources

- Entity Framework
- Loading related entities
- IQueryable<T> Interface

##Designing and implementing WCF Services (15-20%)

- Create a WCF service
- Create contracts (service, data, message, callback, and fault)
-  implement message inspectors
-  implement asynchronous operations in the service
- Configure WCF services by using configuration settings
- Configure service behaviors
	- EXAMPLE
-  configure service endpoints
-  configure bindings including WebSocket bindings
	-  EXAMPLE
-  specify a service contract
-  expose service metadata (XSDs, WSDL, and metadata exchange endpoint)
	-  EXAMPLE
-  configure message compression and encoding
- Configure WCF services by using the API
-  WCF routing and discovery features
- Secure a WCF service
- Implement 
	- message level security, 
		- EXAMPLE
	- implement transport level security
		- EXAMPLE
-  implement certificates
-  design and implement multiple authentication modes
- Consume WCF services
- Generate proxies by using SvcUtil
-  generate proxies by creating a service reference
-  create and implement channel factories
- Version a WCF service
- Version different types of contracts (message, service, data)
-  configure address, binding, and routing service versioning
- Create and configure a WCF service on Azure
- Create and configure bindings for WCF services (Azure extensions to WCF)
-  relay bindings to Azure using service bus endpoints
-  integrate with the Azure service bus relay
- Implement messaging patterns
- Implement one way, request/reply, streaming, and duplex communication
-  implement Azure Service Bus and Azure Queues
- Host and manage services
- Manage services concurrency 
	- single
		- EXAMPLE 
	- multiple
		- EXAMPLE 
	- reentrant
		- EXAMPLE
-  create service hosts
-  choose a hosting mechanism
-  choose an instancing mode 
	-  per call
		-  EXAMPLE
	-  per session
		-  EXAMPLE
	-  singleton
		-  EXAMPLE
-  activate and manage a service by using AppFabric
-  implement transactional services
-  host services in an Azure worker role

####Preparation resources

- Windows Communication Foundation Services and WCF Data Services in Visual Studio
- <bindings>
- Forward-Compatible data contracts

##Creating and consuming Web API-based services (15-20%)

- Design a Web API
- Define HTTP resources with HTTP actions
-  plan appropriate URI space, and map URI space using routing
-  choose appropriate HTTP method (get, put, post, delete) to meet requirements
-  choose appropriate format (Web API formats) for responses to meet requirements
-  plan when to make HTTP actions asynchronous
-  design and implement routes
- Implement a Web API
- Accept data in JSON format (in JavaScript, in an AJAX callback)
-  use content negotiation to deliver different data formats to clients
-  define actions and parameters to handle data binding
-  use HttpMessageHandler to process client requests and server responses
-  implement dependency injection, along with the dependency resolver, to create more flexible applications
-  implement action filters and exception filters to manage controller execution
-  implement asynchronous and synchronous actions
-  implement streaming actions
	-  EXAMPLE
-  implement SignalR
-  test Web API web services
- Secure a Web API
- Implement HTTPBasic authentication over SSL
-  implement Windows Auth
-  prevent cross-site request forgery (XSRF)
-  design, implement, and extend authorization and authentication filters to control access to the application
-  implement Cross Origin Request Sharing (CORS)
-  implement SSO by using OAuth 2.0
-  configure multiple authentication modes on a single endpoint
- Host and manage Web API
- Host Web API in an ASP.NET app
-  self-host a Web API in your own process (a Windows service) including Open Web Interface for .NET (OWIN)
-  host services in an Azure worker role
-  restrict message size
-  configure the host server for streaming
	-  EXAMPLE
- Consume Web API web services
- Consume Web API services by using HttpClient synchronously and asynchronously
-  send and receive requests in different formats (JSON/HTML/etc.)
-  request batching

####Preparation resources

- Getting started with ASP.NET Web API 2 (C#)
- Implementing Basic CRUD functionality with the Entity Framework in ASP.NET MVC application
- Json class

##Deploying web applications and services (15-20%)

- Design a deployment strategy
- Create an IIS install package
-  deploy to web farms
-  deploy a web application by using XCopy
-  automate a deployment from TFS or Build Server
- Choose a deployment strategy for an Azure web application
- Perform an in-place upgrade and VIP swap
-  configure an upgrade domain
-  create and configure input and internal endpoints
-  specify operating system configuration
-  deploy applications using Azure Web Site
- Configure a web application for deployment
- Switch from production/release mode to debug mode
-  use SetParameters to set up an IIS app pool
-  set permissions and passwords
-  enable and monitor ASP.NET App Suspend
-  configure WCF endpoints (including HTTPS protocol mapping), bindings, and behaviors
-  transform web.config by using XSLT (for example, across development, test, and production/release environments)
-  configure Azure configuration settings
- Manage packages by using NuGet
	- Visual Studio GUI Manager
	- Package Manager Console
- Create and configure a NuGet package
	- `nuget spec` : creates the .nuspec manifest file, which can then be updated with all relevant information
	- create lib, content & tools folders (as needed) and populate with needed files
	- `nuget pack {yourPackage}.nuspec` : creates the actual package that can then be uploaded to a NuGet source
	- `nuget push {yourPackage}.nupkg` : publishes the package to the configured source server
-  install and update an existing NuGet package
	- Visual Studio GUI Manager
	- Package Manager Console
		- Install-Package
		- Update-Package
-  connect to a local repository cache for NuGet, set up your own package repository
	-  Local directory
		-  In VS, under Tools/Options then NuGet Package Manager/Package Sources, you can add a new source with a name and the path to the local directory
	-  Internal server option
		-  Create empty ASP.NET web app project
		-  Install NuGet.Server package
		-  Set API key in web.config (optional)
		-  Deploy to IIS server
- Create, configure, and publish a web package
- Create an IIS InstallPackage
-  configure the build process to output a web package
	-  EXAMPLE
-  apply pre- and post- condition actions to ensure that transformations are correctly applied
-  include appropriate assets (web content, certificates)
- Share assemblies between multiple applications and servers
- Prepare the environment for use of assemblies across multiple servers (interning)
-  sign assemblies by using a strong name
-  deploy assemblies to the global assembly cache
-  implement assembly versioning
-  create an assembly manifest
-  configure assembly binding redirects (for example, from MVC4 to MVC5)

####Preparation resources

- ASP.NET Web Deployment using Visual Studio: Introduction
- How to: Create a Web Deployment Package in Visual Studio
- Installing [NuGet](https://www.nuget.org/ "https://www.nuget.org/")
