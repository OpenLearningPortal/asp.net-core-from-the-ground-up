# What is .NET(dotnet) CLI

 .NET Core Command-line(CLI) Tools- command-line (CLI) tools, used for building .NET Core apps and libraries 
                    
                    
### INSTALLING DOTNET CLI



INSTALL .NET CORE AND CLI TOOLS

https://github.com/dotnet/cli
https://dotnet.github.io/getting-started/ 






### DOTNET CLI command Line usage

```.NET CORE COMMAND-LINE(CLI) TOOLS
COMMAND-LINE (CLI) TOOLS, USED FOR BUILDING .NET CORE APPS AND LIBRARIES
ROHITH RAJAN DEBUGGING.IO

INSTALLING DOTNET CLI
dotnet cli installers for all platforms
DOTNET CLI COMMAND-LINE USAGE

                      C:\>dotnet --help
.NET Command Line Tools (1.0.0-beta-002198)
Usage: dotnet [common-options] [command] [arguments]

Arguments:
  [command]     The command to execute
  [arguments]   Arguments to pass to the command

Common Options (passed before the command):
  -v|--verbose  Enable verbose output
  --version     Display .NET CLI Version Number
  --info        Display .NET CLI Info

Common Commands:
  new           Initialize a basic .NET project
  restore       Restore dependencies specified in the .NET project
  build         Builds a .NET project
  publish       Publishes a .NET project for deployment (including the runtime)
  run           Compiles and immediately executes a .NET project
  test          Executes tests in a test project
  repl          Launch an interactive session (read, eval, print, loop)
  pack          Creates a NuGet package
                    
RUN YOUR FIRST .NET CORE CONSOLE APP
INSTALL .NET CORE AND CLI TOOLS

https://github.com/dotnet/cli
https://dotnet.github.io/getting-started/ 

INITIALIZE APP DIRECTORY

                    

mkdir hwapp
cd hwapp
dotnet new ///initialize basic .net project
                    

                    
RUN THE APP

                    

dotnet restore ///restore packages specified in project.json file
dotnet run    ///compile and run your application
                    

                    
RUN YOUR FIRST ASP.NET CORE WEB APP FROM DOTNET CLI
INSTALL LATEST .NET CORE AND CLI SDK

https://github.com/dotnet/cli
make sure git is installed 

CLONE CLI SAMPLES FROM GITHUB REPO

                    

git clone https://github.com/aspnet/cli-samples.git aspnetcli
cd aspnetcli
dotnet restore
                    

                    
RUN THE APP

                    

;Navigate to either HelloMvc or HelloWeb
dotnet run    ///compile and run your application
                    

                    
PUBLISHING YOUR WEBAPP DOTNET PUBLISH

C:\myprojects\cli-samples\HelloMvc>dotnet publish
Publishing HelloMvc for .NETCoreApp,Version=v1.0
Project HelloMvc (.NETCoreApp,Version=v1.0) was previously compiled. Skipping co
mpilation.
No executable found matching command "dotnet-publish-iis"
Published to C:\myprojects\cli-samples\HelloMvc\bin\Debug\netcoreapp1.0\publish
Published 1/1 projects successfully
                    
published directory struture of asp.net core app using dotnet cli
REFERENCES
https://github.com/dotnet/cli
http://dotnet.github.io/
Asp.net core dotnet CLI samples
```

