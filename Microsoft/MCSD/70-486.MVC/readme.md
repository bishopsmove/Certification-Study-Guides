# Developing ASP.NET MVC Web Applications (70-486)

This guide is based, in large part, on the skills summary lists located here:

- [Microsoft Learning Portal](https://www.microsoft.com/en-us/learning/exam-70-486.aspx "https://www.microsoft.com/en-us/learning/exam-70-486.aspx")
- [Microsoft Born To Learn](https://borntolearn.mslearn.net/certification/p/wiki?es=webApp&ec=486 "https://borntolearn.mslearn.net/certification/p/wiki?es=webApp&ec=486") Training and Certification Community Wiki site

Anything else listed additionally is based on my own observations. Links listed here may be subject to copyright protection and access to such is up to the discretion of the authors\owners to which they pertain.

##Design the application architecture (15-20%)

###Plan the application layers

- Plan data access; 
- plan for separation of concerns; 
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

- Entity Framework Development workflows
- DataAdapters and DataReaders
- ASP.NET State Management overview

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

- Build a better mobile browsing experience
- Display modes
- Building Modern Web Apps Jump Start

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

- Search Engine Optimization Toolkit
- GlobalizationSection Class
- FormCollection Class

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

- Using shims to isolate your application from other assemblies for unit testing

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

- Introduction to ASP.NET Identity
- Chapter 5: Authentication, authorization, and identities in WCF
- Easy Web App Integration with Windows Azure Active Directory, ASP.NET & Visual Studio