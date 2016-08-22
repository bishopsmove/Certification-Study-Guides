# Developing ASP.NET MVC Web Applications (70-486)

This guide is based, in large part, on the skills summary lists located here:

- [Microsoft Learning Portal](https://www.microsoft.com/en-us/learning/exam-70-486.aspx "https://www.microsoft.com/en-us/learning/exam-70-486.aspx")
- [Microsoft Born To Learn](https://borntolearn.mslearn.net/certification/p/wiki?es=webApp&ec=486 "https://borntolearn.mslearn.net/certification/p/wiki?es=webApp&ec=486") Training and Certification Community Wiki site

Anything else listed additionally is based on my own observations. Links listed here may be subject to copyright protection and access to such is up to the discretion of the authors\owners to which they pertain.

####Caveats

This exam targets MVC 5.1 and VS2013. A number of aspects of MVC 4 still apply, as well as the general functionality of MVC on ASP.Net, but be aware of the MVC 5.x distinctions and how VS2013 is expected to be utilized.

####Additional Resources

- [PluralSight "Learning Path"](https://www.pluralsight.com/blog/software-development/asp-net-mvc-microsoft-exam-70-486 "https://www.pluralsight.com/blog/software-development/asp-net-mvc-microsoft-exam-70-486") for 70-486

##Design the application architecture (15-20%)

###Plan the application layers

- Plan data access
	- [Data Access Practices Using Microsoft .Net: A Nerdly Comparison](https://msdn.microsoft.com/en-us/data/ff707264.aspx "https://msdn.microsoft.com/en-us/data/ff707264.aspx")
	- Based on the exam ref prep book, you have a choice between using:
		- an ORM (Object/Relational Mapper):
			1. [Entity Framework](http://msdn.microsoft.com/en-us/data/ef.aspx "http://msdn.microsoft.com/en-us/data/ef.aspx")
			2. [NHibernate](http://nhibernate.info/ "http://nhibernate.info/")
			3. [Linq-to-SQL](https://msdn.microsoft.com/en-us/library/bb425822.aspx "https://msdn.microsoft.com/en-us/library/bb425822.aspx")
		- Roll your own DAL (using [ADO.Net](https://msdn.microsoft.com/en-us/library/e80y5yhx(v=vs.110).aspx "https://msdn.microsoft.com/en-us/library/e80y5yhx(v=vs.110).aspx"), etc.)
	- [EFMVC – ASP.NET MVC 4, Entity Framework 5 Code First and Windows Azure (Demo App)](http://efmvc.codeplex.com/ "http://efmvc.codeplex.com/")
	- Understand the difference between Database-First and Code-First design strategies
		- Data annotations for code first ([validation](http://labs.bjfocus.co.uk/2014/03/validation-attributes-in-code-first/ "http://labs.bjfocus.co.uk/2014/03/validation-attributes-in-code-first/") and [database related](http://labs.bjfocus.co.uk/2014/03/database-related-attributes-in-code-first/ "http://labs.bjfocus.co.uk/2014/03/database-related-attributes-in-code-first/"))
- plan for separation of concerns
	- [Wikipedia definition](https://en.wikipedia.org/wiki/Separation_of_concerns "https://en.wikipedia.org/wiki/Separation_of_concerns")
	- [Intro the MVC architecture and SoC](http://www.c-sharpcorner.com/UploadFile/1492b1/introduction-to-mvc-architecture-and-separation-of-concerns/ "http://www.c-sharpcorner.com/UploadFile/1492b1/introduction-to-mvc-architecture-and-separation-of-concerns/")
- appropriate use of:
	- models, 
	- views, 
	- controllers 
- choose between client-side and server side processing; 
- design for scalability

###Design a distributed application

- Design a hybrid application (on-premises versus off-premises, including Azure), 
- plan for session management in a distributed environment, 
- plan web farms

###Design and implement the Azure role life cycle

- Identify and implement Start, Run, and Stop events; 
- identify startup tasks (IIS configuration [app pool], registry configuration, third-party tools)

###Configure state management

- Choose a state management mechanism (in-process and out of process state management), 
- plan for scalability, 
- use cookies or local storage to maintain state, 
- apply configuration settings in web.config file, 
- implement sessionless state (for example, QueryString)

###Design a caching strategy

- Implement page output caching (performance oriented), 
- implement data caching, 
- implement HTTP caching, 
- implement Azure caching

###Design and implement a WebSocket strategy

- Read and write string and binary data asynchronously (long-running data transfers), 
- choose a connection loss strategy, 
- decide a strategy for when to use WebSockets, 
- implement SignalR

###Design HTTP modules and handlers

- Implement synchronous and asynchronous modules and handlers, 
- choose between modules and handlers in IIS

####Preparation resources

- [Entity Framework Development workflows](http://msdn.microsoft.com/en-US/data/jj590134 "http://msdn.microsoft.com/en-US/data/jj590134")
- [DataAdapters and DataReaders](http://msdn.microsoft.com/en-us/library/ms254931(v=vs.110).aspx "http://msdn.microsoft.com/en-us/library/ms254931(v=vs.110).aspx")
- [ASP.NET State Management overview](http://msdn.microsoft.com/en-us/library/75x4ha6s(v=vs.100).aspx "http://msdn.microsoft.com/en-us/library/75x4ha6s(v=vs.100).aspx")
- [Why use the Entity Framework? Yeah, why exactly?](http://weblogs.asp.net/fbouma/why-use-the-entity-framework-yeah-why-exactly "http://weblogs.asp.net/fbouma/why-use-the-entity-framework-yeah-why-exactly")

##Design the user experience (20-25%)

###Apply the user interface design for a web application

- Create and apply styles by using CSS, 
- structure and lay out the user interface by using HTML, 
- implement dynamic page content based on a design

###Design and implement UI behavior

- Implement client validation, 
- use JavaScript and the DOM to control application behavior, 
- extend objects by using prototypal inheritance, 
- use AJAX to make partial page updates, 
- implement the UI by using JQuery

###Compose the UI layout of an application

- Implement partials for reuse in different areas of the application, 
- design and implement pages by using Razor templates (Razor view engine), 
- design layouts to provide visual structure, 
- implement master/application pages

###Enhance application behavior and style based on browser feature detection

- Detect browser features and capabilities; 
- create a web application that runs across multiple browsers and mobile devices; 
- enhance application behavior and style by using vendor-specific extensions, for example, CSS

###Plan an adaptive UI layout

- Plan for running applications in browsers on multiple devices (screen resolution, CSS, HTML), 
- plan for mobile web applications

####Preparation resources

- [Build a better mobile browsing experience](http://msdn.microsoft.com/en-us/magazine/hh288079.aspx "http://msdn.microsoft.com/en-us/magazine/hh288079.aspx")
- [Display modes](http://www.asp.net/whitepapers/mvc4-release-notes#_Toc303253810 "http://www.asp.net/whitepapers/mvc4-release-notes#_Toc303253810")
- [Building Modern Web Apps Jump Start](https://mva.microsoft.com/training-courses/building-modern-web-apps-jump-start "https://mva.microsoft.com/training-courses/building-modern-web-apps-jump-start")

##Develop the user experience (15-20%)

###Plan for search engine optimization and accessibility

- Use analytical tools to parse HTML, 
- view and evaluate conceptual structure by using plugs-in for browsers, 
- write semantic markup (HTML5 and ARIA) for accessibility (for example, screen readers)

###Plan and implement globalization and localization

- Plan a localization strategy; 
- create and apply resources to UI, 
- including JavaScript resources; 
- set cultures; 
- create satellite resource assemblies

###Design and implement MVC controllers and actions

- Apply authorization attributes, global filters, and authentication filters; 
- specify an override filter; 
- implement action behaviors; 
- implement action results; 
- implement model binding

###Design and implement routes

- Define a route to handle a URL pattern, 
- apply route constraints, 
- ignore URL patterns, 
- add custom route parameters, 
- define areas

###Control application behavior by using MVC extensibility points

- Implement MVC filters and controller factories; 
- control application behavior by using action results, viewengines, model binders, and route handlers

###Reduce network bandwidth

- Bundle and minify scripts (CSS and JavaScript), 
- compress and decompress data (using gzip/deflate; storage), 
- plan a content delivery network (CDN) strategy (for example, Azure CDN)

####Preparation resources

- [Search Engine Optimization Toolkit](http://www.iis.net/downloads/microsoft/search-engine-optimization-toolkit "http://www.iis.net/downloads/microsoft/search-engine-optimization-toolkit")
- [GlobalizationSection Class](http://msdn.microsoft.com/en-us/library/system.web.configuration.globalizationsection.aspx "http://msdn.microsoft.com/en-us/library/system.web.configuration.globalizationsection.aspx")
- [FormCollection Class](http://msdn.microsoft.com/en-us/library/system.web.mvc.formcollection(v=vs.118).aspx "http://msdn.microsoft.com/en-us/library/system.web.mvc.formcollection(v=vs.118).aspx")

##Troubleshoot and debug web applications (20-25%)

###Prevent and troubleshoot runtime issues

- Troubleshoot performance, security, and errors; 
- implement tracing, logging (including using attributes for logging), and debugging (including IntelliTrace); 
- enforce conditions by using code contracts; 
- enable and configure health monitoring (including Performance Monitor)

###Design an exception handling strategy

- Handle exceptions across multiple layers, 
- display custom error pages using global.asax or creating your own HTTPHandler or set web.config attributes, 
- handle first chance exceptions

###Test a web application

- Create and run unit tests (for example, use the Assert class), 
- create mocks; 
- create and run web tests, including using Browser Link; 
- debug a web application in multiple browsers and mobile emulators

###Debug an Azure application

- Collect diagnostic information by using Azure Diagnostics API and appropriately implement on demand versus scheduled; 
- choose log types (for example, event logs, performance counters, and crash dumps); 
- debug an Azure application by using IntelliTrace, Remote Desktop Protocol (RDP), and remote debugging; 
- interact directly with remote Azure websites using Server Explorer.

####Preparation resources

- [Using shims to isolate your application from other assemblies for unit testing](http://msdn.microsoft.com/en-us/library/hh549176(v=vs.120).aspx "http://msdn.microsoft.com/en-us/library/hh549176(v=vs.120).aspx")

##Design and implement security (20-25%)

###Configure authentication

- Authenticate users; 
- enforce authentication settings; 
- choose between Windows, Forms, and custom authentication; 
- manage user session by using cookies; 
- configure membership providers; 
- create custom membership providers; 
- configure ASP.NET Identity

###Configure and apply authorization

- Create roles, authorize roles by using configuration, 
- authorize roles programmatically, 
- create custom role providers, 
- implement WCF service authorization

###Design and implement claims-based authentication across federated identity stores

- Implement federated authentication by using Azure Access Control Service; 
- create a custom security token by using Windows Identity Foundation; 
- handle token formats (for example, oAuth, OpenID, Microsoft Account, Google, Twitter, and Facebook) for SAML and SWT tokens

###Manage data integrity

- Apply encryption to application data, 
- apply encryption to the configuration sections of an application, 
- sign application data to prevent tampering

###Implement a secure site with ASP.NET

- Secure communication by applying SSL certificates; 
- salt and hash passwords for storage; 
- use HTML encoding to prevent cross-site scripting attacks (ANTI-XSS Library); 
- implement deferred validation and handle unvalidated requests, for example, form, querystring, and URL; 
- prevent SQL injection attacks by parameterizing queries; 
- prevent cross-site request forgeries (XSRF)

####Preparation resources

- [Introduction to ASP.NET Identity](http://www.asp.net/identity/overview/getting-started/introduction-to-aspnet-identity "http://www.asp.net/identity/overview/getting-started/introduction-to-aspnet-identity")
- [Chapter 5: Authentication, authorization, and identities in WCF](http://msdn.microsoft.com/en-us/library/ff647503.aspx "http://msdn.microsoft.com/en-us/library/ff647503.aspx")
- [Easy Web App Integration with Windows Azure Active Directory, ASP.NET & Visual Studio](http://blogs.technet.com/b/ad/archive/2013/06/26/improved-windows-azure-active-directory-integration-with-asp-net-amp-visual-studio.aspx "http://blogs.technet.com/b/ad/archive/2013/06/26/improved-windows-azure-active-directory-integration-with-asp-net-amp-visual-studio.aspx")