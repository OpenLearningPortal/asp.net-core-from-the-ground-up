# ASP.NET CORE Main Features

ASP.NET Core framework provides many features which is required for modern web application development.Let's looks through main ones

###Open Source Cross platform Runtime

ASP.NET Core project targets .NET Core by default, in addition to the FUll .NET Framework or Mono. .NET Core is a small, optimized runtime that can be run on Linux,Windows ,Mac OSX or FreeBSD. 

###Light-Weight and Modular
SP.NET Core and .NET Core come with the great advantage of only including the libraries and functions you explicitly want to use in your application rather than bringing in the entire framework. Asp.net core is a simple and lightweight web framework without the need for cumbersome (XML) configuration, to enable very fast web application development with minimal effort. 

###Ridiculously fast.

As of RC2, ASP.NET Core exceeds 1.15 Million request/s which represents a 2300% gain from ASP.NET 4.6.In the RC stage only, it outperforms popular nodejs or scala benchmarks on many scenarios. Once we hit RTM we will see a lot more improvement.

###a unified programming model

MVC, Web API and Web Pages  MVC 6, merged those models into a single programming model.This will create a single web application that handles the Web UI and data services and You will also be able to seamlessly transition a simple site first developed with Web Pages into a more robust MVC application

###Cross platform development

You can develop asp.net core applications using favorite IDEs.Supported IDEs are visual Studio(windows),Visual Studio Code(linux,windows,Mac OSX etc) ,Sublime Text,VIM,EMAC,Brackets etc.

###Cloud ready

In ASP.NET Core,  eliminated the need to use XML based config file for configuration values.It is easier for you to deploy your app to the cloud and have the app automatically read the correct configuration values for that environment. The new Configuration system enables you to request named values from a variety of sources (such as JSON, XML, or environment variables). So your application can be deployed on multiple enviroments (linux,windows,azure Cloud or Docker)

###Multiple languages Support and language interoparable

The .NET Core is language independent. This means that, as a developer, you can develop in one of the many languages that target the .NET Core, such as C#, VB.NET , F# etc. You can access the types and members of class libraries developed for the .NET Core without having to know the language in which they were originally written and without having to follow any of the original language's conventions. If you are a component developer, your component can be accessed by any .NET Core app regardless of its language.


###Integrated Package Management

In .NET CORE almost all features are now implemented as NuGet modules - allowing you to optimize your app to have just what you need.it has Integrated support for creating and using NuGet packages,even references or dependencies are added as Nuget packages