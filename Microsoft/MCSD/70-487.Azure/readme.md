# Developing Microsoft Azure and Web Services (70-487)

This guide is based, in large part, on the skills summary lists located here:

- [Microsoft Learning Portal](https://www.microsoft.com/en-us/learning/exam-70-487.aspx "https://www.microsoft.com/en-us/learning/exam-70-487.aspx")
- [Microsoft Born To Learn](https://borntolearn.mslearn.net/certification/p/wiki?es=webApp&ec=487 "https://borntolearn.mslearn.net/certification/p/wiki?es=webApp&ec=487") Training and Certification Community Wiki site

Anything else listed additionally is based on my own observations. Links listed here may be subject to copyright protection and access to such is up to the discretion of the authors\owners to which they pertain.

####Additional Resources

- Pluralsight [recommended videos for 70-487](http://blog.pluralsight.com/developing-microsoft-azure-and-web-services-microsoft-exam-70-487 "http://blog.pluralsight.com/developing-microsoft-azure-and-web-services-microsoft-exam-70-487")
- MS Virtual Academy - [Applications on Azure: Putting All the Pieces Together](https://mva.microsoft.com/en-US/training-courses/applications-on-azure-putting-all-the-pieces-together-14429 "https://mva.microsoft.com/en-US/training-courses/applications-on-azure-putting-all-the-pieces-together-14429") (Updated tutorial from *Developing Windows Azure and Web Services Jump Start*)
- Barbarian Meets Coding - [Notes for 70-487](https://www.barbarianmeetscoding.com/wiki/70-487-azure-and-web-services-certification-study-guide/ "https://www.barbarianmeetscoding.com/wiki/70-487-azure-and-web-services-certification-study-guide/")
- [Shane Bart's 70-487 Mind Map](https://i0.wp.com/www.shanebart.com/wp-content/uploads/2016/03/70-487.png?ssl=1 "https://i0.wp.com/www.shanebart.com/wp-content/uploads/2016/03/70-487.png?ssl=1")

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
	- CachItem
	- Priority
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
		1. Enable access to the data service by using `config.SetEntitySetAccessRule()` in the `InitializeService()` method of the Data Service class.
		2. Enable the ServiceOperation access by using `config.SetServiceOperationAccessRule()`, also in the `InitializeService()` method of the Data Service class.
		3. This now allows a client to query via Resource URIs:
			`http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=ShippedDate gt datetime'1997-09-22T00:00:00'`
	-  create a query expression

			[QueryInterceptor("Products")]
			public Expression<Func<Product, bool>> OnReadProducts()
			{
			    return o => o.Discontinued == false;
			}
	-  access payload formats (including JSON)
		-  Default is ATOM (XML wrapped with metadata)
			-  With AJAX WCF, the default format is XML and default verb is HTTP POST
		-  On the Endpoint behavior config (or the Endpoint itself, either by config file or in code), set the AutomaticFormatSelectionEnabled property to true. This allows the WCF infrastructure to determine the best format, based on the Accept headers of the request.
		-  Formats can also be specified explicitly on a per-endpoint-method basis
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
	- EXAMPLE

			<?xml version="1.0" encoding="utf-8"?>
			<configuration>
		    <system.serviceModel>
		        <bindings>
		            <basicHttpBinding>
		                <binding name="BasicHttpBinding_IService1" closeTimeout="00:01:00"
		                    openTimeout="00:01:00" receiveTimeout="00:10:00" sendTimeout="00:01:00"
		                    allowCookies="false" bypassProxyOnLocal="false" 
		                    hostNameComparisonMode="StrongWildcard" maxBufferSize="65536" 
		                    maxBufferPoolSize="524288" maxReceivedMessageSize="65536"
		                    messageEncoding="Text" textEncoding="utf-8" transferMode="Buffered"
		                    useDefaultWebProxy="true">
		                    <readerQuotas maxDepth="32" maxStringContentLength="8192" 
		                        maxArrayLength="16384" maxBytesPerRead="4096"
		                        maxNameTableCharCount="16384" />
		                    <security mode="None">
		                        <transport clientCredentialType="None" proxyCredentialType="None"
		                            realm="" />
		                        <message clientCredentialType="UserName" algorithmSuite="Default" />
		                    </security>
		                </binding>
		            </basicHttpBinding>
		        </bindings>
		        <client>
		            <endpoint address="http://localhost:36906/Service1.svc" binding="basicHttpBinding"
		                bindingConfiguration="BasicHttpBinding_IService1" contract="IService1"
		                name="BasicHttpBinding_IService1" />
		        </client>
		    </system.serviceModel>
</configuration>

- Configure service behaviors
	- EXAMPLE
-  configure service endpoints
-  configure bindings including WebSocket bindings
	-  EXAMPLE
-  specify a service contract
-  expose service metadata (XSDs, WSDL, and metadata exchange endpoint)
	- EXAMPLE

			<services>
				<service name="Metadata.Example.SimpleService"
      					behaviorConfiguration="SimpleServiceBehavior">

	    		<endpoint address=""
		              binding="wsHttpBinding"
		              contract="Metadata.Example.ISimpleService" />

			    <endpoint address="mex"
			              binding="mexHttpBinding"
			              contract="IMetadataExchange" />
  				</service>
			</services>
			<behaviors>
				<serviceBehaviors>
					<behavior name="SimpleServiceBehavior">
					  <serviceMetadata httpGetEnabled="True" policyVersion="Policy15" />
					</behavior>
				</serviceBehaviors>
			</behaviors>

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
- Manage [services concurrency](http://stackoverflow.com/questions/3657858/how-does-concurrency-work-in-wcf#3658417 "http://stackoverflow.com/questions/3657858/how-does-concurrency-work-in-wcf#3658417") 
	- Single : only one thread can access service instance. This is default behavior.
		- EXAMPLE

				[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerCall, 
				                 ConcurrencyMode = ConcurrencyMode.Single)]
				public class HelloWorldService : IHelloWorldService
				{
				}
 
	- Multiple : multiple threads can access service instance.
		- EXAMPLE

				[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerCall, 
				                 ConcurrencyMode = ConcurrencyMode.Multiple)]
				public class HelloWorldService : IHelloWorldService
				{
				}
  
	- Reentrant : one thread can access service but but it can release the lock and allow other thread to use the instance while first thread will be blocked. This is used in callback scenario.
		- EXAMPLE

				[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]
				public class HelloWorldService : IHelloWorldService
				{
				}
 
-  create service hosts
-  choose a hosting mechanism
-  choose an [instancing mode](http://stackoverflow.com/questions/3657858/how-does-concurrency-work-in-wcf#3658417 "http://stackoverflow.com/questions/3657858/how-does-concurrency-work-in-wcf#3658417") 
	-  per call
		-  EXAMPLE: typical stateless scenario. Multiple concurrent calls are allowed.

				[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerCall, 
				                 ConcurrencyMode = ConcurrencyMode.Single)]
				public class HelloWorldService : IHelloWorldService
				{
				}
 
	-  per session
		-  EXAMPLE : multiple concurrent calls are allowed. Multiple calls from each proxy can access same instance at the same time. You have to do manual synchronization of access to shared fields in the service instance.

				[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession, 
				                 ConcurrencyMode = ConcurrencyMode.Multiple)]
				public class HelloWorldService : IHelloWorldService
				{
				}
 
	-  singleton
		-  EXAMPLE : multiple concurrent calls are allowed. All calls access same instance at the same time. You have to do manual synchronization of access to shared fields in the service instance.

				[ServiceBehavior(InstanceContextMode=InstanceContextMode.Single, 
				                 ConcurrencyMode = ConcurrencyMode.Multiple)]
				public class HelloWorldService : IHelloWorldService
				{
				}
 
-  activate and manage a service by using AppFabric
-  implement transactional services
-  host services in an Azure worker role

####Preparation resources

- Windows Communication Foundation Services and WCF Data Services in Visual Studio
- <bindings>
- Forward-Compatible data contracts
- [Sessions, Instancing, and Concurrency](https://msdn.microsoft.com/en-us/library/ms731193(v=vs.110).aspx "https://msdn.microsoft.com/en-us/library/ms731193(v=vs.110).aspx")

##Creating and consuming Web API-based services (15-20%)

- Design a Web API
- Define HTTP resources with HTTP actions
	- [Http<Action> vs AcceptVerbs](http://stackoverflow.com/a/16034262/885317 "http://stackoverflow.com/a/16034262/885317")
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
-  implement [streaming actions](http://weblogs.asp.net/andresv/asynchronous-streaming-in-asp-net-webapi "http://weblogs.asp.net/andresv/asynchronous-streaming-in-asp-net-webapi")
	-  EXAMPLE
	  
			public HttpResponseMessage Get([FromUri] int accountId)
		    {
		        HttpResponseMessage response = Request.CreateResponse();
		
		        // Create push content with a delegate that will get called when it is time to write out 
		        // the response.
		        response.Content = new PushStreamContent(
		            async (outputStream, httpContent, transportContext) =>
		            {
		                try
		                {
		                    // Execute the command and get a reader
		                    using (var reader = GetMetadataListReader(accountId))
		                    {
		
		                        // Read rows asynchronously, put data into buffer and write asynchronously
		                        while (await reader.ReadAsync())
		                        {
		                            var rec = MapRecord(reader);
		
		                            var str = await JsonConvert.SerializeObjectAsync(rec);
		
		                            var buffer = UTF8Encoding.UTF8.GetBytes(str);
		
		                            // Write out data to output stream
		                            await outputStream.WriteAsync(buffer, 0, buffer.Length);
		                        }
		                    }
		                }
		                catch(HttpException ex)
		                {
		                    if (ex.ErrorCode == -2147023667) // The remote host closed the connection. 
		                    {
		                        return;
		                    }
		                }
		                finally
		                {
		                    // Close output stream as we are done
		                    outputStream.Close();
		                }
		            });
		
		        return response;
		    }

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
-  [configure the host server for streaming](https://msdn.microsoft.com/en-us/library/ee960144(v=vs.110).aspx "https://msdn.microsoft.com/en-us/library/ee960144(v=vs.110).aspx")
	-  When using WCF with ASP.Net, WCF limits the HTTP message size to 64k by default. To stream large amounts of data, reset the maxReceivedMessageSize setting in the config to an appropriate size. Also, set the transferMode to "Streamed" to prevent WCF from buffering either\both the request\response.
	-  Utilize the `PushStreamContent` class
- Consume Web API web services
- Consume Web API services by using HttpClient synchronously and asynchronously
-  send and receive requests in different formats (JSON/HTML/etc.)
	-  Set the ServiceBehavior or ServiceEndpoint AutomaticFormatSelectionEnabled to true.
	-  Or inspect the request's Accept header to to determine the preferred format type
	-  Or establish a separate endpoint method to output the preferred format. A IRequestHandler can be used to determine a format request and forward to the correct endpoint method.
-  request batching

####Preparation resources

- Getting started with ASP.NET Web API 2 (C#)
- Implementing Basic CRUD functionality with the Entity Framework in ASP.NET MVC application
- Json class

##Deploying web applications and services (15-20%)

- Design a deployment strategy
	- Simple: Xcopy - for files only
	- Complex: Web Deploy - Files, config, registry, database, PowerShell
	- Scale-out options: web farm, session management, load balancing
	- Continuous Integration\Deployment: Build Server
	- Azure:
		- Delete and redeploy
			- Incurs downtime
			- Required for changes to endpoints, firewall rules or certificates
		- In-place update
			- No downtime
			- Requires upgrade domains to be configured
			- During upgrade process, different versions of site are running concurrently.  This condition must be accounted for, e.g. db schema change
		- Virtual IP (VIP) Swap
			- No downtime
			- Makes use on Prod and Staging environments (specifically their IPs)
			- Upload to Staging (via D&R or In-place update), test, then "promote" Staging and "demote" Prod, effectively swapping their Virtual IPs
			- During swap process, remnant connections will likely be affected
			- Once swap is complete, Staging will now incur cost until deleted
- Create an IIS install package
	1. Create a *Publish profile* using the **Publish Web** wizard in Visual Studio
		1. Publish method: **Web Deploy Package** 
		2. Define the package location (including name of .zip file)
		3. Specify the IIS site name, though this can be overridden during install
		4. Settings: Specify the configuration and the default connection string for that confirguration
	2. Click *Publish* to create the package. The resulting .zip file will contain the following files:
	   - ***projectname*.deploy.cmd** - Helper command-line batch file that invokes Web Deploy in order to install the application on the destination server locally or remotely.
	   - ***projectname*.SetParameters.xml** - contains parameters that are passed to Web Deploy on the destination server. 
	   - ***projectname*.SourceManifest.xml** - contains settings that Visual Studio used to create the deployment package.
    3. Advanced options (Project Properties \ Package/Publish Web tab)
       - Specify physical IIS path
       - Specify password for IIS settings 
-  deploy to web farms
	-  Requirements (for all servers in the farm):
		-  Web Deployment Tool's Remote Agent Service must be installed and running
		-  HTTP port must be allowed by their firewall
		-  Must all be members of same domain and the account used for synchronization must have administrative rights on all servers in the farm.
	-  Deploy IIS package to one of the servers in the farm
	-  Establish this server as the "model computer" by making app or site configuration changes
	-  Using *msdeploy.exe*, sync each server in the farm to the model, either via the package name or "webserver" - which will sync with the entire IIS web server (Examples):
		-  `msdeploy.exe -verb:sync -source:package={packageName} -dest:auto,computername={remoteServer} {MSDeployOperationSettingOptions}`
		-  `msdeploy.exe -verb:sync -source:package=webServer -dest:auto,computername={remoteServer} {MSDeployOperationSettingOptions}`
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
-  enable and monitor [ASP.NET App Suspend](https://blogs.msdn.microsoft.com/webdev/2013/10/09/enable-and-monitor-asp-net-app-suspend-on-windows-server-2012-r2/ "https://blogs.msdn.microsoft.com/webdev/2013/10/09/enable-and-monitor-asp-net-app-suspend-on-windows-server-2012-r2/")
	- To enable: In Advanced Settings for ApplicationPool, set Idle Time-out Action to "Suspend"
	- To monitor: In the Application event log, search for event 2310 to confirm that a worker process timed-out and was suspended.
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
- Create an [IIS InstallPackage](http://www.iis.net/learn/publish/using-web-deploy/export-a-package-through-iis-manager "http://www.iis.net/learn/publish/using-web-deploy/export-a-package-through-iis-manager")
	1. Install project as web application to local IIS
	2. In IIS Management Console, select web application and export
	3. Under Manage Components, choose the providers needed for deployment (i.e. dbFullSql, appPoolConfig, etc) and configure accordingly for deployment environment.
	4. Select and add/modify parameters as needed
	5. specify path and filename to save the package
	6. Click finish to complete the process.
-  configure [the build process to output a web package](http://www.asp.net/web-forms/overview/deployment/web-deployment-in-the-enterprise/building-and-packaging-web-application-projects "http://www.asp.net/web-forms/overview/deployment/web-deployment-in-the-enterprise/building-and-packaging-web-application-projects")
	-  EXAMPLE
-  apply pre- and post- condition actions to ensure that transformations are correctly applied
-  include appropriate assets (web content, certificates)
- Share assemblies between multiple applications and servers
- Prepare the environment for use of assemblies across multiple servers (interning)
	- [aspnet_intern.exe](https://www.shanebart.com/aspnet-assembly-interning/ "https://www.shanebart.com/aspnet-assembly-interning/")
		- `aspnet_intern [-mode analyze|exec|clean|query] [-sourcedir <input source path>] [-interndir <output target interned path>] [-minrefcount 3]`
-  sign assemblies by using a strong name
	-  create the strong name key: `sn -k sgKey.snk`
	-  Assign the key to the assembly via Assembly Linker:
		-  `al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk`
-  deploy assemblies to the global assembly cache
-  implement assembly versioning (only applies to assemblies with strong names)
-  create an assembly manifest
-  configure assembly binding redirects (for example, from MVC4 to MVC5)
	-  Example

			<configuration>
			   <runtime>
			      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
			         <dependentAssembly>
			            <assemblyIdentity name="myAssembly"
			                              publicKeyToken="32ab4ba45e0a69a1"
			                              culture="neutral" />
			            <bindingRedirect oldVersion="1.0.0.0"
			                             newVersion="2.0.0.0"/>
			            <codeBase version="2.0.0.0"
			                      href="http://www.litwareinc.com/myAssembly.dll"/>
			         </dependentAssembly>
			      </assemblyBinding>
			   </runtime>
			</configuration>
	
	- Alternative
		- Using NuGet, you can run Add-BindingRedirect after the project has been built. This will update the .config file automatically.
	- Probing PrivatePath
		- Helps specify subdirectories where assemblies may reside

				<configuration>
				   <runtime>
				      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
				         <probing privatePath="bin;bin2\subbin;bin3"/>
				      </assemblyBinding>
				   </runtime>
				</configuration>
####Preparation resources

- ASP.NET Web Deployment using Visual Studio: Introduction
- How to: Create a Web Deployment Package in Visual Studio
- Installing [NuGet](https://www.nuget.org/ "https://www.nuget.org/")
