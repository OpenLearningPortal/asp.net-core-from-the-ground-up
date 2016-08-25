# Startup class and Services

##The Startup class

In ASP.NET Core, the Startup class provides the entry point for an application, and is required for all applications.

asp.net core application is a console application under the hood with a web framework(asp.net core) listening and responding to http requests.So startup.cs class where we bootstrap the asp.net core framework components.This can be done as light weight as possible by registering and using the components you only need or you can go with a base template(like we created using VS or VS code in previous chapter).You also have the option to strip out built in components and use your own on third party frameworks.

###STARTUP.CS MAIN USE CASES
* The constructor Startup() allows us to setup or include the configuration values.
* ConfigureServices() allows us to add services to the Dependency Injection container.
* Configure() allows us to add middleware and services to the HTTP pipeline.

###Looking at a typical starup.cs  
``` 
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.AspNet.Builder;
using Microsoft.AspNet.Hosting;
using Microsoft.AspNet.Http;
using Microsoft.Extensions.DependencyInjection;

namespace WebApplication1
{
    public class Startup
    {
        // This method gets called by the runtime. Use this method to add services to the container.
        // For more information on how to configure your application, visit http://go.microsoft.com/fwlink/?LinkID=398940
        public void ConfigureServices(IServiceCollection services)
        {
        }

        // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
        public void Configure(IApplicationBuilder app)
        {
            

            app.Run(async (context) =>
            {
                await context.Response.WriteAsync("Hello World!");
            });
        }

        // Entry point for the application.
        public static void Main(string[] args) => WebApplication.Run<startup>(args);
    }
}

                    </startup>
STARTUP() METHOD

///IConfigurationRoot It represents the root of the configuration file that was formerly represented by the web.config file
public IConfigurationRoot Configuration { get; set; }

public Startup(IHostingEnvironment env)  
{
    // Set up configuration sources.
    var builder = new ConfigurationBuilder()
        .AddJsonFile("appsettings.json")
        .AddEnvironmentVariables();
    Configuration = builder.Build();
}

                    
AddJsonFile("appsettings.js") can parse JSON files and load the values from the app settings into the Configuration
AddEnvironmentVariables() adds any environmental values to the configuration
CONFIGURESERVICES()

// This method gets called by the runtime. Use this method to add services to the container.
public void ConfigureServices(IServiceCollection services)  
{
    // Add framework services.
    services.AddMvc();
}
                    
ConfigureServices exists for the explicit reason of adding services to ASP.NET Core. ASP.NET Core supports Dependency Injection natively, and as such this method is adding services to the DI container
CONFIGURE() -CONFIGURE ASP.NET PIPELINE.

public void Configure(IApplicationBuilder app, IHostingEnvironment env, ILoggerFactory loggerFactory)
{
    loggerFactory.AddConsole(Configuration.GetSection("Logging"));
    loggerFactory.AddDebug();

    if (env.IsDevelopment())
    {
        app.UseBrowserLink();
        app.UseDeveloperExceptionPage();
        app.UseDatabaseErrorPage();
    }
    else
    {
        app.UseExceptionHandler("/Home/Error");

        // For more details on creating database during deployment see http://go.microsoft.com/fwlink/?LinkID=615859
        try
        {
            using (var serviceScope = app.ApplicationServices.GetRequiredService<IServiceScopeFactory>()
                .CreateScope())
            {
                serviceScope.ServiceProvider.GetService<ApplicationDbContext>()
                     .Database.Migrate();
            }
        }
        catch { }
    }

    app.UseIISPlatformHandler(options => options.AuthenticationDescriptions.Clear());

    app.UseStaticFiles();

    app.UseIdentity();

    // To configure external authentication please see http://go.microsoft.com/fwlink/?LinkID=532715

    app.UseMvc(routes =>
    {
        routes.MapRoute(
            name: "default",
            template: "{controller=Home}/{action=Index}/{id?}");
    });
}
                    
IApplicationBuilder allows us to add services to the pipeline for this app.
IHostingEnvironment stores information about the current hosted environment.
ILoggerFactoryallows us to setup and add log providers.

```


###STARTUP() METHOD

```
///IConfigurationRoot It represents the root of the configuration file that was formerly represented by the web.config file
public IConfigurationRoot Configuration { get; set; }

public Startup(IHostingEnvironment env)  
{
    // Set up configuration sources.
    var builder = new ConfigurationBuilder()
        .AddJsonFile("appsettings.json")
        .AddEnvironmentVariables();
    Configuration = builder.Build();
}

```

* AddJsonFile("appsettings.js") can parse JSON files and load the values from the app settings into the Configuration
* AddEnvironmentVariables() adds any environmental values to the configuration

###CONFIGURESERVICES()

```
// This method gets called by the runtime. Use this method to add services to the container.
public void ConfigureServices(IServiceCollection services)  
{
    // Add framework services.
    services.AddMvc();
}
```

* ConfigureServices exists for the explicit reason of adding services to ASP.NET Core. 
* ASP.NET Core supports Dependency Injection natively, and as such this method is adding services to the DI container

###CONFIGURE() -Typical CONFIGURE ASP.NET PIPELINE.

```
public void Configure(IApplicationBuilder app, IHostingEnvironment env, ILoggerFactory loggerFactory)
{
    loggerFactory.AddConsole(Configuration.GetSection("Logging"));
    loggerFactory.AddDebug();

    if (env.IsDevelopment())
    {
        app.UseBrowserLink();
        app.UseDeveloperExceptionPage();
        app.UseDatabaseErrorPage();
    }
    else
    {
        app.UseExceptionHandler("/Home/Error");

        // For more details on creating database during deployment see http://go.microsoft.com/fwlink/?LinkID=615859
        try
        {
            using (var serviceScope = app.ApplicationServices.GetRequiredService<IServiceScopeFactory>()
                .CreateScope())
            {
                serviceScope.ServiceProvider.GetService<ApplicationDbContext>()
                     .Database.Migrate();
            }
        }
        catch { }
    }

    app.UseIISPlatformHandler(options => options.AuthenticationDescriptions.Clear());

    app.UseStaticFiles();

    app.UseIdentity();

    // To configure external authentication please see http://go.microsoft.com/fwlink/?LinkID=532715

    app.UseMvc(routes =>
    {
        routes.MapRoute(
            name: "default",
            template: "{controller=Home}/{action=Index}/{id?}");
    });
}
```

##Services

A SERVICE IS A COMPONENT THAT IS INTENDED FOR COMMON CONSUMPTION IN AN APPLICATION

CONFIGURESERVICES METHOD IN ASP.NET CORE EXISTS FOR THE EXPLICIT REASON OF ADDING SERVICES TO ASP.NET

```
// This method gets called by the runtime. Use this method to add services to the container.
public void ConfigureServices(IServiceCollection services)  
{
  services.Configure<AppSettings>(Configuration.GetSubKey("AppSettings"));

    services.AddEntityFramework()
            .AddSqlServer()
            .AddDbContext<MovieContext>();

    // Add MVC services to the services container.
    services.AddMvc();
}
      
```

DEPENDENCY INJECTION IS THE DEFAULT WAY OF ADDING SERVICES TO OUR RUNTIME AND ENVIRONMENT IN ASP.NET CORE

E.G. ADDING SIMPLE LOGGING SERVICES

```
    public interface ILog { }
public class Log : ILog { }
```

```
public void ConfigureServices(IServiceCollection services)
       {
           services.AddMvc();
           services.AddTransient<ILog, Log>();
       }
                
```
E.G.INJECTING EF INTO THE SERVICES LAYER

```
//Add Entiy framework services to the services container.
 services.AddEntityFramework()
            .AddSqlServer()
            .AddDbContext<MovieContext>();
```