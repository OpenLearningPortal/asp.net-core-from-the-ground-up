# ASP.NET CORE Basic Features

ASP.NET Core is a complete redesign of ASP.NET.For those who don't know, ASP.NET is web application framework runs on top of Full .Net Framework\(1.1 to 4.6\) from Microsoft mainly targeted for Windows.Though you could run asp.net applications on Mono open source framework on other platforms,it was not fully compatible and supported by Microsoft .ASP.NET Core is designed from ground up to run on .NET CORE runtime \(which is a cross platform port of .NET framework from Microsoft\) and fully supported by Microsoft.


![](/assets/aspnetcore.png)


ASP.NET CORE contains all the required components for creating modern web applications:

* MVC pattern 
* Simplest possible viewnengine for WEB UI (Razor ViewEngine)
* Built in Dependency Injection
* Best in class O/RM (EFCore) with Expressive Beautiful Syntax (LINQ)
* Easy integration of Modern Client side frameworks 
* Built in support for package management (Nuget packages)

### MVC pattern

ASP.NET CORE MVC gives you a powerful, patterns-based way to build dynamic websites that enables a clean separation of concerns and that gives you full control over markup for enjoyable, agile development..

### Razor Views

ASP.NET Core Razor syntax provide a fast, approachable, and lightweight way to combine server code with HTML to create dynamic web content. It includes many more features that help you create beautiful sites that conform to the latest web standards.


### Dependency Injection

ASP.NET Core is designed from the ground up to support and leverage dependency injection

### Entity Framework Core

Entity Framework (EF) Core is a lightweight and extensible version of the popular Entity Framework data access technology.EF Core is an object-relational mapper (O/RM) that enables .NET developers to work with a database using .NET objects. It eliminates the need for most of the data-access code that developers usually need to write. EF Core supports many database engines such as Microsfot SQL Server,Postgres,MySQL,SQlLite etc

### Beautiful Syntax

`
using (var db = new BloggingContext()) {
 var blogs = db.Blogs 
    .Where(b => b.Rating > 3) 
    .OrderBy(b => b.Url) .ToList(); 
}

`




