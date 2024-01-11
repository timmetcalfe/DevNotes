
# Best Practices

A page to store links, blogs, comments, and packages that I consider beneficial for learning, developing and writing clean .NET code.

## Design principals

- Keep it simple, stupid.
- Focus on the requirement, not the technology.
- Code should read like a story.
- Keep as much as possible in code and in .NET. For example, don't use Angular if all that is required are a few web pages, use Razor Pages instead.
- Prefer locality of behaviour and vertical slice architecture over multiple layers of components.
- Minimise all external dependencies. For example, don't place just 3 or 4 email templates that rarely change, in blob storage. This would mean a dependency on the blob storage service. Instead, place them in C# classes.
- Following on from point above, keep as much work as possible in the local code.
- Keep all configuration local and change depending on environment. Don't automatically use web app config when it's only storing values that never need to be changed in the web app config settings of Azure portal.
- Minimise dependency on specific cloud providers.
- Prefer build and deployment process in code and CLI rather than YAML based pipelines.
- A dependency is a liability. Reduce all external dependencies as much as posssible.

## Microsoft Code with Engineering Playbook

[Mirosoft Commercial Software Engineering team, CSE Code with engineering playbook](https://microsoft.github.io/code-with-engineering-playbook)

[Engineering Fundamentals Checklist](https://microsoft.github.io/code-with-engineering-playbook/ENG-FUNDAMENTALS-CHECKLIST/)

[C# code reviews and checklist](https://microsoft.github.io/code-with-engineering-playbook/code-reviews/recipes/csharp/)

## Coding conventions and engineering guidelines from Microsoft
[Common C# code conventions](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions)

[ASPNET Core engineering guidelines](https://github.com/dotnet/aspnetcore/wiki/Engineering-guidelines)

## Creating a new project/package

```
<PackageReference Include="AsyncFixer" Version="1.6.0">
  <IncludeAssets>runtime; build; native; contentfiles; analyzers; buildtransitive</IncludeAssets>
  <PrivateAssets>all</PrivateAssets>
</PackageReference>  
<PackageReference Include="NetEscapades.AspNetCore.SecurityHeaders" Version="0.18.0" />  
<PackageReference Include="SonarAnalyzer.CSharp" Version="8.52.0.60960">
  <IncludeAssets>runtime; build; native; contentfiles; analyzers; buildtransitive</IncludeAssets>
  <PrivateAssets>all</PrivateAssets>
</PackageReference>
  ```

## NuGet packages to consider for each project

- Fluent Results  
- BenchmarkDotNet.Org  
- DbUp  
- Serilog  
- HangFire  
- Scrutor  
- FluentValidation  
- AutoFixture  
- FluentAssertions  
- Quartz.Net  
- Wolverine  
- Elsa Core  
- FastEndpoints  
- Nuke.Build  
- LINQKit  
- EFCore.BulkExtensions  
- AngleSharp  
- Playwright
- CliWrap
- Bogus
- [Andrew Lock - Small package to allow adding security headers to ASP.NET Core websites](https://github.com/andrewlock/NetEscapades.AspNetCore.SecurityHeaders)  

Project Orleans  
AZD  
Microsoft Kiota  

## Blogs / YouTube channels / developers to follow
- [Azure Cloud Blogs](https://cloudblogs.microsoft.com)  
- [Microsoft Developer Blogs](https://devblogs.microsoft.com)  
- [Steve ‘Ardalis’ Smith](https://ardalis.com)  
- [Vladimir Khorikov](https://enterprisecraftsmanship.com)  
- [Jimmy Bogard](https://jimmybogard.com)  
- [Mark Heath](https://markheath.net)  
- [Khalid Abuhakmeh](https://khalidabuhakmeh.com)  
- [Derek Comartin](https://codeopinion.com)  
- [Bart Wullem](https://bartwullems.blogspot.com)  
- [Rick Strahl](https://weblog.west-wind.com)  
- [Jeremy Miller](https://jeremydmiller.com)  
- [Andrew Lock](https://andrewlock.net)  
- [Oscar Dudycz](https://event-driven.io/en)  
- [The Morning Brew](https://cwa.me.uk)  
- [The Morning Dew](https://alvinashcraft.com)  
- [Raw Coding](https://www.youtube.com/@RawCoding)  
- [Nick Chapsas](https://www.youtube.com/@nickchapsas)  

## Event Sourcing

[Examples and Tutorials of Event Sourcing in .NET - Oskar Dudycz](https://github.com/oskardudycz/EventSourcing.NetCore)

## UI

- [HTMX](https://htmx.org)
- [Hyperscript](https://hyperscript.org)
- [AlpineJs](https://alpinejs.dev)  

## Valuable articles / blog posts / courses

- [Microsoft REST API Guidelines](https://github.com/microsoft/api-guidelines/blob/vNext/Guidelines.md)
- [C# 9.0: Pattern Matching in Switch Expressions - Thomas Claudis Huber](https://www.thomasclaudiushuber.com/2021/02/25/c-9-0-pattern-matching-in-switch-expressions/)
- [Domain-Driven Design Fundamentals By Julie Lerman and Steve Smith - Pluralsight](https://app.pluralsight.com/course-player?clipId=2a61567d-77cd-4b9c-9c8b-8a942cf4abb8)
- [The Best Way to Validate Your Option Settings in .NET - Nick Chapsas](https://www.youtube.com/watch?v=jblRYDMTtvg) - related [Andrew Lock, Adding validation to strongly typed configuration objects in .NET 6](https://andrewlock.net/adding-validation-to-strongly-typed-configuration-objects-in-dotnet-6/)

## Microsoft DevBlog articles

- [Creating Discoverable HTTP APIs with ASP.NET Core 5 Web API - Microsoft .NET Blog](https://devblogs.microsoft.com/dotnet/creating-discoverable-http-apis-with-asp-net-core-5-web-api/) - 4th Feb, 2021  
- [Open-source HTTP API packages and tools - Microsoft .NET Blog](https://devblogs.microsoft.com/dotnet/open-source-http-api-packages-and-tools/) - 11th Feb, 2021

## Better code structure from a post on Scott Hanselman's blog

https://www.hanselman.com/blog/editorconfig-code-formatting-from-the-command-line-with-net-cores-dotnet-format-global-tool - Stuart’s comment.

We focus on having better code structure instead of micro coding rules which apply to one part of a statement or identifier declaration.

Variable naming, whether or not you use VAR and the like are minor minor worries.

Our solution:
- Getting the business logic right
- Having methods follow the business logic instead of misappropriated patterns
- Checking for errors
- Using guard clauses
- Avoid using the self-documenting code cliche instead of documenting the business purpose and logic for each unit of work
- Having code where the reading level is Junior developer
- Limiting the number of identifiers each line of code has access to
- Keeping code together for a single job, following locality of reference, not segregating code out into dozens of components for a single task just for whiteboard diagramming purposes. Indirection in reading the code for a business task from the first line to the last for the business task should be easy and not require the reader to look at dozens of source code files.
- Avoiding magic framework induced indirection. Code used should be referenced by a method and not through levels of framework interconnects. Breaking down business logic into X areas interconnected via framework indirection considerably lowers the maintainability of the code.
- Code should not require reader to be an expert in the framework, ASP.NET MVC structure, ... because that knowledge is an order of magnitude harder to find 3 years after the code goes into production. Think finding an Angular 1.0 expert now 5+ years after that framework was released
- Avoiding custom build steps
- Avoiding custom build tools
- *important* - Not buying or using tools, libraries, frameworks which hit 75% of our needs but need customization to work. It's a ticking maintenance bomb. The underlying tool, framework, library should have the functionality already in it and not require customization.

## Resiliency strategies

### Sending a message to service bus
Newer versions of the Azure SDK have default resiliency strategies for many Azure services. Details of them can be found at:
https://learn.microsoft.com/en-us/azure/architecture/best-practices/retry-service-specific

Using the Azure SDKs means resiliency is implemented by default for many services.

### Azure SQL database
Entity Framework Core has an option for connection resiliency, which is .EnableRetryOnFailure(). For example:

services.AddDbContext<QlikDbContext>(options =>
  options.UseSqlServer(hostContext.Configuration.GetSection("QlikDatabaseConnection").Value, sqlOptions =>
  {
      sqlOptions.EnableRetryOnFailure();
  }));
Details can be found at:
https://learn.microsoft.com/en-us/ef/core/miscellaneous/connection-resiliency

### Calling an HTTP endpoint using .NET HTTP client
.NET 8 has a new package available which provides updated default resiliency strategies based on Polly v8. Include the package Microsoft.Extensions.Http.Resilience, add .AddStandardResilienceHandler() to a HttpClient implementation and the new default strategies will be enabled. For example:

services.AddHttpClient<RmApiOutboundHttpClientService>().AddStandardResilienceHandler();
Details at:
https://devblogs.microsoft.com/dotnet/building-resilient-cloud-services-with-dotnet-8/



 
    
