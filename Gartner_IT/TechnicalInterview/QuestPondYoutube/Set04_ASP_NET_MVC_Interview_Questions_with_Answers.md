### ASP.NET MVC Interview Questions & Answers - Part 1

**Question 1: What is ASP.NET MVC Core?**
ASP.NET MVC Core is a web development framework by Microsoft that provides a high-performance, cross-platform way to build modern, cloud-based, internet-connected applications. It combines the features of MVC (Model-View-Controller) and Web API into a single framework, allowing for more streamlined development and deployment of web applications.

**Question 2: Differentiate between ASP.NET Webforms vs MVC vs MVC Core?**
- **ASP.NET Webforms**:
  - Event-driven model.
  - Uses server controls and view state for managing state.
  - Suitable for RAD (Rapid Application Development).

- **ASP.NET MVC**:
  - Based on the Model-View-Controller pattern.
  - Provides better separation of concerns.
  - No view state or server controls.
  - More control over HTML, CSS, and JavaScript.

- **ASP.NET MVC Core**:
  - Cross-platform (Windows, Linux, macOS).
  - Unified framework for MVC and Web API.
  - High performance, more lightweight, and modular.
  - Uses a new project structure and simplified hosting model.

**Question 3: Explain MVC Architecture?**
MVC architecture divides an application into three main components:
- **Model**: Represents the application's data and business logic.
- **View**: Displays the data (user interface).
- **Controller**: Handles user input and updates the model and view accordingly.

**Question 4: Why do we have wwwroot folder?**
The `wwwroot` folder is the web root for the application. It's where static files like CSS, JavaScript, and images are stored. These files are publicly accessible via the web.

**Question 5: Explain the importance of appsettings.json?**
`appsettings.json` is a configuration file in ASP.NET Core used to store application settings such as database connection strings, API keys, and other configuration data. It's a JSON file and can be easily read and modified.

**Question 6: How to read configurations from appsettings.json?**
You can read configurations using the `Configuration` API in ASP.NET Core. For example:
```csharp
public class Startup
{
    public Startup(IConfiguration configuration)
    {
        Configuration = configuration;
    }

    public IConfiguration Configuration { get; }

    public void ConfigureServices(IServiceCollection services)
    {
        var mySetting = Configuration["MySetting"];
    }
}
```

**Question 7: What is dependency injection?**
Dependency Injection (DI) is a design pattern used to implement IoC (Inversion of Control). It allows the creation of dependent objects outside of a class and provides those objects to a class in various ways, increasing modularity and testing ease.

**Question 8: Why do we need dependency injection?**
DI is needed to:
- Decouple the creation of objects from their usage.
- Increase code maintainability and readability.
- Facilitate unit testing by making it easier to mock dependencies.

**Question 9: How do we implement dependency injection?**
In ASP.NET Core, DI is implemented using the built-in IoC container. Services are registered in the `ConfigureServices` method in `Startup.cs`.
```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddTransient<IMyService, MyService>();
}
```

**Question 10: What is the use of Middleware?**
Middleware components are used to handle requests and responses in the ASP.NET Core request pipeline. Each component can perform operations before and after the next component in the pipeline is invoked.

**Question 11: How to create a Middleware?**
To create custom middleware:
1. Create a class with an `Invoke` or `InvokeAsync` method.
2. Register the middleware in the `Configure` method of `Startup.cs`.
```csharp
public class CustomMiddleware
{
    private readonly RequestDelegate _next;

    public CustomMiddleware(RequestDelegate next)
    {
        _next = next;
    }

    public async Task InvokeAsync(HttpContext context)
    {
        // Middleware logic
        await _next(context);
    }
}
```
Register in `Startup.cs`:
```csharp
public void Configure(IApplicationBuilder app)
{
    app.UseMiddleware<CustomMiddleware>();
}
```

**Question 12: What does startup.cs file do?**
The `Startup.cs` file configures the request pipeline and services used by the application. It contains two primary methods:
- `ConfigureServices`: Registers services in the DI container.
- `Configure`: Defines the middleware pipeline.

**Question 13: ConfigureServices vs Configure method?**
- **ConfigureServices**: Used to register services with the DI container.
- **Configure**: Used to define the middleware components that handle HTTP requests.

**Question 14: Explain the different Ways of doing DI?**
In ASP.NET Core, DI can be implemented in three main ways:
- **Constructor Injection**: Dependencies are passed through a class constructor.
- **Method Injection**: Dependencies are passed as parameters to a method.
- **Property Injection**: Dependencies are set via public properties.

**Question 15: Explain Scoped vs Transient vs Singleton?**
- **Transient**: Created each time they are requested. Use for lightweight, stateless services.
- **Scoped**: Created once per request. Use for services that need to maintain state within a request.
- **Singleton**: Created the first time they are requested and reused for every subsequent request. Use for stateless, long-lived services.

**Question 16: What is Razor?**
Razor is a markup syntax for embedding server-based code into web pages. It allows you to mix HTML with C# or VB.NET code.

**Question 17: How to pass Model data to a View?**
Model data is passed to a view by including the model in the controller action method and returning it with the view.
```csharp
public IActionResult Index()
{
    var model = new MyModel();
    return View(model);
}
```

**Question 18: What is the use of Strongly typed views?**
Strongly typed views provide compile-time type checking and IntelliSense support for the model. They are defined by specifying the model type at the top of the view.
```csharp
@model MyModel
```

**Question 19: Explain the concept of ViewModel in MVC?**
A ViewModel is a model specifically created for a view. It can combine multiple models and add additional properties needed only for the view, improving separation of concerns.

**Question 20: What is Kestrel Web Server?**
Kestrel is a cross-platform web server for ASP.NET Core. It is included by default in ASP.NET Core project templates and is designed to be fast and lightweight.

**Question 21: Why Kestrel when we have IIS server?**
Kestrel is used for its performance and cross-platform capabilities. It can be used as an edge server or with a reverse proxy server like IIS, Nginx, or Apache for additional features like security and load balancing.

**Question 22: What is the concept of Reverse proxy?**
A reverse proxy server sits between client devices and a backend server, forwarding client requests to the backend server. It provides benefits like load balancing, security, and caching.

**Question 23: What are cookies?**
Cookies are small pieces of data stored by the web browser on the client's machine. They are used to store user preferences, session identifiers, and other data for tracking and personalization.

**Question 24: What is the need session management?**
Session management is used to store and retrieve user-specific data across multiple requests in a web application. It is essential for maintaining state in a stateless HTTP protocol.

**Question 25: What are the various ways of doing Session management in ASP.NET?**
- **In-Process**: Stores session data in memory on the web server.
- **Out-of-Process**: Stores session data in a distributed cache or database, suitable for web farms or applications needing durability across server restarts.

### ASP.NET MVC Interview Questions & Answers - Part 2

**Question 26: What exactly is a session?**
A session is a server-side storage of user-specific data that persists across multiple requests. It helps maintain state in web applications.

**Question 27: Explain "HTTP is a stateless protocol"?**
HTTP is a stateless protocol meaning each request from a client to server is treated as an independent transaction that is unrelated to any previous request. The server does not retain any state information between requests.

**Question 28: What are various way of doing session management?**
- **Cookies**: Store session data on the client-side.
- **Session State**: Stores data on the server side for the duration of a user's session.
- **Database**: Store session data in a database for persistence and scalability.
- **Cache**: Use distributed cache systems like Redis or Memcached for session storage.

**Question 29: Are sessions enabled by default?**
No, sessions are not enabled by default in ASP.NET Core. They need to be explicitly configured in the `Startup.cs` file.

**Question 30: How to enable sessions in MVC core?**
To enable sessions, configure services in `Startup.cs`:
```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddSession();
    services.AddMvc();
}

public void Configure(IApplicationBuilder app)
{
    app.UseSession();
    app.UseMvc();
}
```

**Question 31: Are sessions variables shared (global) between users?**
No, session variables are specific to a single user session and are not shared between users.

**Question 32: Do session variables use cookies?**
Yes, session variables often use a session cookie to store the session ID on the client-side, which is then used to retrieve the session data on the server-side.

**Question 33: What is a cookie?**
A

 cookie is a small piece of data sent from a server and stored on the client's device. It can be used to track and store information about the user's interaction with the site.

**Question 34: Explain idle time out in sessions?**
Idle timeout is the amount of time a session can remain inactive before it is terminated. If there are no requests from the user within this time frame, the session will expire and its data will be cleared.

**Question 35: What does a Context mean in HTTP?**
In HTTP, a context refers to the information about the current request and response. It includes data such as request headers, query strings, and body content, as well as methods to manipulate the response.

### ASP.NET MVC Interview Questions & Answers - Part 3

**Question 36: When should we use ViewData?**
Use `ViewData` when you need to pass data from the controller to the view, especially for small amounts of data. It is a dictionary object and does not require a strongly typed view.

**Question 37: How to pass data from controller to view?**
Data can be passed using `ViewData`, `ViewBag`, or a model. Example using `ViewData`:
```csharp
public IActionResult Index()
{
    ViewData["Message"] = "Hello, World!";
    return View();
}
```

**Question 38: In same request can ViewData persist across actions?**
No, `ViewData` is meant for a single request. For passing data between actions, use `TempData`.

**Question 39: ViewData vs ViewBag**
- **ViewData**: Dictionary-based, requires casting to retrieve data.
- **ViewBag**: Dynamic object, more flexible, no casting required.

**Question 40: How does ViewBag work internally?**
`ViewBag` uses the `ViewData` dictionary internally. It is a dynamic wrapper around `ViewData`.

**Question 41: Explain ViewModel?**
A `ViewModel` is a model specifically created for the view. It combines multiple models or additional data needed by the view.

**Question 42: ViewBag vs ViewModel - What's the best practice?**
Using a `ViewModel` is the best practice as it provides strong typing and better organization of the data passed to the view, leading to more maintainable and readable code.

### ASP.NET MVC Interview Questions & Answers - Part 4

**Question 43: Explain TempData?**
`TempData` is used to pass data between two consecutive requests. It is a dictionary object and can store data temporarily.

**Question 44: Can TempData persist across action redirects?**
Yes, `TempData` is specifically designed to persist data across redirects.

**Question 45: How is TempData different from ViewData?**
- **TempData**: Persists data for the next request only, mainly used for redirects.
- **ViewData**: Used to pass data from controller to view within a single request.

**Question 46: If TempData is read, is it available for the next request?**
No, once `TempData` is read, it is marked for deletion. To persist it, you can use the `Keep` method.

**Question 47: How to persist TempData?**
Use the `Keep` or `Peek` method to persist `TempData` for subsequent requests.
```csharp
var value = TempData["key"];
TempData.Keep("key");
```

**Question 48: What does Keep do in TempData?**
`Keep` marks the specified `TempData` key for retention for the next request.

**Question 49: Explain Peek in TempData?**
`Peek` reads the value without marking it for deletion, allowing it to be available for subsequent requests.
```csharp
var value = TempData.Peek("key");
```

**Question 50: How is TempData different from session variables?**
- **TempData**: Temporary data, persists for one request.
- **Session**: Stores data throughout the user session.

**Question 51: If I restart the server does TempData, session stay?**
- **TempData**: No, it is lost on server restart as it is stored in memory.
- **Session**: Depends on the session state mode. In-Process sessions are lost, while out-of-process sessions (e.g., SQL Server, Redis) can persist.

**Question 52: Is TempData private to a user?**
Yes, `TempData` is specific to a user session and is not shared between users.

**Question 53: ViewData vs ViewBag vs TempData vs Session variables**
- **ViewData**: Passes data from controller to view within a request, dictionary-based.
- **ViewBag**: Similar to `ViewData`, but dynamic object-based.
- **TempData**: Passes data between requests, persists for the next request.
- **Session**: Stores data throughout the user's session, persists across multiple requests.

### ASP.NET MVC Interview Questions & Answers - Part 5

**Question 54: What is WebAPI?**
WebAPI is a framework that makes it easy to build HTTP services that reach a broad range of clients, including browsers and mobile devices. It is ideal for building RESTful applications.

**Question 55: What is the advantage of WebAPI?**
- Lightweight and suitable for devices with limited bandwidth.
- Supports content negotiation.
- Easily testable.
- Can be hosted in IIS or self-hosted.

**Question 56: Explain REST and Architectural constraints of REST?**
REST (Representational State Transfer) is an architectural style for designing networked applications. The constraints of REST include:
- **Stateless**: Each request from a client to server must contain all the information needed to understand and process the request.
- **Client-Server**: Separation of client and server concerns.
- **Uniform Interface**: Simplifies and decouples the architecture.
- **Cacheable**: Responses must define themselves as cacheable or not to prevent clients from reusing stale or inappropriate data.
- **Layered System**: Client cannot ordinarily tell whether it is connected directly to the end server or an intermediary along the way.
- **Code on Demand (optional)**: Servers can temporarily extend or customize the functionality of a client by transferring executable code.

**Question 57: Can we use TCP/IP protocol with Web API?**
Web API is primarily designed for HTTP/HTTPS protocols, but it can be extended to use other protocols like TCP/IP by implementing custom message handlers.

**Question 58: How WebAPI different from MVC controller?**
- **WebAPI Controller**: Designed for handling HTTP requests and returning data (e.g., JSON, XML).
- **MVC Controller**: Designed for rendering views (HTML) in response to client requests.

**Question 59: What is content negotiations in Web API?**
Content negotiation is the process of selecting the best response format for a client request based on the client's capabilities and preferences, which are expressed in the `Accept` header of the HTTP request.

**Question 60: WebAPI vs WCF?**
- **WebAPI**: Ideal for building RESTful services, easy to use, and lightweight.
- **WCF**: Designed for building SOAP-based services, supports more protocols (TCP, Named Pipes, etc.), more complex and configurable.

**Question 61: WCF REST vs WebAPI REST?**
- **WCF REST**: More configuration and setup, supports both SOAP and REST, not as straightforward as WebAPI.
- **WebAPI REST**: Specifically designed for RESTful services, easier and more straightforward to implement.

**Question 62: How to return HTTP status codes?**
You can return HTTP status codes using the `HttpResponseMessage` or `IActionResult` in ASP.NET Core.
```csharp
public IActionResult Get()
{
    if (data == null)
    {
        return NotFound(); // Returns a 404 status code
    }
    return Ok(data); // Returns a 200 status code
}
```

**Question 63: For error which status code is returned?**
For errors, common status codes include:
- **400 Bad Request**: The request could not be understood by the server.
- **401 Unauthorized**: Authentication is required and has failed or has not been provided.
- **403 Forbidden**: The server understood the request, but refuses to authorize it.
- **404 Not Found**: The requested resource could not be found.
- **500 Internal Server Error**: A generic error message, given when no more specific message is suitable.

**Question 64: How did you secure your Web API?**
- Use HTTPS to encrypt data in transit.
- Implement authentication and authorization using tokens (e.g., JWT).
- Use CORS to control resource sharing across different origins.
- Validate and sanitize input to prevent attacks like SQL injection.
- Implement rate limiting to prevent denial of service attacks.

**Question 65: How do current JS frameworks work with Web API?**
Modern JavaScript frameworks like Angular, React, and Vue.js consume Web APIs to build single-page applications (SPAs). They use HTTP client libraries (e.g., Axios, Fetch API) to make asynchronous requests to the Web API and update the UI dynamically based on the API responses.