#Before.NET Core

.NET((pronounced dotnet) is a general purpose development platform developed by Microsoft primarily targeted for Windows and first version released in 2002.It has major releases from 2002 to till date versions spanning from  .NET Framework 1.1  to 4.6 . Key features that are attractive to  developers are automatic memory management , modern programming languages (c#,vb.net ,f# etc) , language interopability  and intergated IDEs. 

# .NET Core

.NET Core is an open source port of .NET framework developed by Microsoft .it can run on Microsoft Windows ,Linux,OS X and FreeBSD .  .NET Core  consists of an execution environment,standard libraries ,a package manager and compiler components.It provides a light weight development model and the flexibility to work with your favorite development tools on your favorite development platform.

* NET Core is a set of runtime, library and compiler components
* .NET Core compiles your code with a JIT compiler or ahead of time with .NET Native.
* .NET Core manages memory with a garbage collector, 
* NET Core apps that run on multiple OSes and CPUs. Ports are in progress for Linux, OS X and FreeBSD
* It can be installed locally with your app with only the packages you need

It includes a  class library known as CoreFX and provides language interoperability (each language can use code written in other languages) across several programming languages. Programs written for .NET Core execute in an environment known as CoreCLR (CLR), an application virtual machine that provides services such as security, memory management, and exception handling. (the code written using .NET Core is called "managed code".) CoreFX and CoreCLR together constitute .NET Core.


##CoreCLR

 It includes main execution environment, the garbage collector, JIT compiler, base .NET data types and many low-level classes.The base library called mscorlib is runtime specific(seperate for Linux,Windows, Mac OSX or FreeBSD)and lives inside the CoreCLR.

Microsoft also produces an integrated development environment for .NET called Visual Studio (runs on Windows) and Visual Studio Code(runs on linux,Windows and OSX).

##CoreFX 

provides libraries such as System.Collections, System.IO, System.Xml and so on for collections, file systems, console, XML,Diagnostics,Network Communications async and many others.  CoreFX is agnostic of runtime-implementation and can be run on any compatible .NET runtime such as full .NET framework or Mono.The libraries usually starts with Microsoft.* or System.* .


