
# Best Practices

A page to store links, blogs, comments, and packages that I consider beneficial for learning, developing and writing clean .NET code.

## My own design guidelines

- Keep it simple, stupid.
- Minimise all external dependencies. For example, don't place just 3 or 4 email templates in blob storage that rarely change, which would mean a dependency on the blob storage service. Instead place them in C# classes.
- Following on from point above, keep as much work as possible in the local code.
- Keep all configuration local and change depending on environment. Don't automatically use web app config when it's only storing values that never need to be changed in the web app config settings of Azure portal.

## Microsoft Code with Engineering Playbook

[Mirosoft Commercial Software Engineering team, CSE Code with engineering playbook](https://microsoft.github.io/code-with-engineering-playbook)

[Engineering Fundamentals Checklist](https://microsoft.github.io/code-with-engineering-playbook/ENG-FUNDAMENTALS-CHECKLIST/)

[C# code reviews and checklist](https://microsoft.github.io/code-with-engineering-playbook/code-reviews/recipes/csharp/)

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
- LinkKit  
- EFCore.BulkExtensions  
- AngleSharp  
- Playwright  
- [Andrew Lock - Small package to allow adding security headers to ASP.NET Core websites](https://github.com/andrewlock/NetEscapades.AspNetCore.SecurityHeaders)  

Project Orleans  
AZD  

## Blogs/ YouTube channels / developers to follow
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

- [C# 9.0: Pattern Matching in Switch Expressions - Thomas Claudis Huber](https://www.thomasclaudiushuber.com/2021/02/25/c-9-0-pattern-matching-in-switch-expressions/)
- [Domain-Driven Design Fundamentals By Julie Lerman and Steve Smith - Pluralsight](https://app.pluralsight.com/course-player?clipId=2a61567d-77cd-4b9c-9c8b-8a942cf4abb8)
- [The Best Way to Validate Your Option Settings in .NET - Nick Chapsas](https://www.youtube.com/watch?v=jblRYDMTtvg) - related [Andrew Lock, Adding validation to strongly typed configuration objects in .NET 6](https://andrewlock.net/adding-validation-to-strongly-typed-configuration-objects-in-dotnet-6/)

## Microsoft DevBlog articles

- [Creating Discoverable HTTP APIs with ASP.NET Core 5 Web API - Microsoft .NET Blog](https://devblogs.microsoft.com/dotnet/creating-discoverable-http-apis-with-asp-net-core-5-web-api/) - 4th Feb, 2021  





 
    
