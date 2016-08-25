# Middleware

Middleware are components that are assembled into an application pipeline to handle requests and responses.The concept is similar as famous open source framewosk django(python) or expressjs(nodejs) frameworks

Middleware, at least in ASP.NET, comes from the Open Web Interface for .NET (Open Web Interface for .NET (OWIN) project.

MIDDLEWARE PIPELINE

![middleware pipeline](request-delegate-pipeline.png)

> ANY TIME YOU SEE APP.USEX()( inside Configure method ), YOU ARE USING SOME OF ASP.NET'S DEFAULT MIDDLEWARE COMPONENTS.

```
  app.UseStaticFiles();

    app.UseIdentity();

    // To configure external authentication please see http://go.microsoft.com/fwlink/?LinkID=532715

    app.UseMvc(routes =>
    {
        routes.MapRoute(
            name: "default",
            template: "{controller=Home}/{action=Index}/{id?}");
    });

```

WRITING A simple MIDDLEWARE is as easy as writing a Function

```
public class CustomMiddleware  
{
    private readonly RequestDelegate _next;

    public AuthorizationMiddleware(RequestDelegate next)
    {
        _next = next;
    }

}
```

###RUN,MAP AND USE

3 ways to configure middlewares

####RUN EXTENSION

```
public void Configure(IApplicationBuilder app)
    {        
        app.Run(async context =>
        {
            await context.Response.WriteAsync("Return From Run.");
        });
        app.Run(async context => {
            await context.Response.WriteAsync("This is second Run.");
        });
    }
```

The nature of Run extension is to short circuit the HTTP pipeline immediately. It is a shorthand way of adding middleware to the pipeline that does not call any other middleware which is next to it and immediately return HTTP response.


####USE EXTENSION

In case of Use extension, there is a chance to pass next invoker, so that HTTP request will be transferred to the next middleware after execution of current Use if there next invoker is present

```
public void Configure(IApplicationBuilder app)
    {        
        app.Use(next=> async context =>
        {
            await context.Response.WriteAsync("Return From Use.");
            await next.Invoke(context);
        });
        app.Run(async context => {
            await context.Response.WriteAsync("This is from Run.");
        });
    }
          
```
####MAP EXTENSION

Map extensions are used as convention for branching the pipeline. We can hook delegate to Map extension to push it to HTTP pipeline. Map simply accepts a path and a function that configures a separate middleware pipeline

```
private static void MyDelegate(IApplicationBuilder app)
    {
        app.Run(async context =>
        {
            await context.Response.WriteAsync("Returning from Map");
        });
    }
    public void Configure(IApplicationBuilder app)
    {
        app.UseMvc();
        app.Map("/MyDelegate", MyDelegate);
    }
                    
```

####MAPWHEN EXTENSION

```

private static void MapQuery(IApplicationBuilder app)
    {
        app.Run(async context =>
        {
            await context.Response.WriteAsync("Return from MapQuery");
        });
    }
    public void Configure(IApplicationBuilder app)
    {
        app.UseMvc();
        //Execute when "map" is there in query string
        app.MapWhen(context => {
            return context.Request.Query.ContainsKey("map");
        }, MapQuery);
        //Return response for other request
        app.Run(async context =>
        {
            await context.Response.WriteAsync("From Run extension");
        });
    }
```
