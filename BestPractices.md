
# Best Practices

A page to store links, comments, and packages that I consider beneficial for devloping and writing clean code.

## Microsoft Code with Engineering Playbook

https://microsoft.github.io/code-with-engineering-playbook, especially  
https://microsoft.github.io/code-with-engineering-playbook/ENG-FUNDAMENTALS-CHECKLIST/  
https://microsoft.github.io/code-with-engineering-playbook/code-reviews/recipes/csharp/

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
## Web site security headers

https://github.com/andrewlock/NetEscapades.AspNetCore.SecurityHeaders

Related NuGet package is NetEscapades.AspNetCore.SecurityHeaders

## NuGet packages to consider for each project

Fluent Results  
BenchmarkDotNet.Org  
DbUp  
Serilog  
HangFire  
Scrutor  
FluentValidation  
AutoFixture  
FluentAssertions  
Quartz.Net  



 
    
