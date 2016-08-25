# Run your First ASP.NET CORE application


###Initialize a simple console app

```mkdir hwapp
cd hwapp
dotnet new ///initialize basic .net project```


###RUN THE APP


```dotnet restore ///restore packages specified in project.json file
dotnet run    ///compile and run your application```


###Initialize asp.net core app

#####INSTALL LATEST .NET CORE AND CLI SDK

https://github.com/dotnet/cli
make sure git is installed 


#####CLONE CLI SAMPLES FROM GITHUB REPO

```git clone https://github.com/aspnet/cli-samples.git aspnetcli
cd aspnetcli
dotnet restore```



##### RUN THE APP
```navigate to either HelloMvc or HelloWeb
cd HelloMVC
dotnet run    ///compile and run your application```